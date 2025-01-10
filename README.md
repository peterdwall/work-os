# skywire-linux

This is a repo containing the files required to build a custom Fedora Atomic OS. You can visit the [BlueBuild documentation](https://blue-build.org/learn/getting-started/) for more info.

## Goals

Create a Fedora Silverblue-based immutable OS for technician and callcenter use. The base system will include all packages needed for daily operation in the image, including:

- Winbox 3
- Winbox 4 (flatpak)
- The Dude
- Ultimate Back Office
- LibreOffice
- 3CX
- Netinstall
- Pre-set `udev` and `serial`
- Post-installation scripts to set up Wireguard, extra optional packages, and anything else.

## Usage

Right now, download this repo and follow the [BlueBuild documentation](https://blue-build.org/how-to/setup/) on how to build the image from the `build.yml` file. The ISO is too big to keep in this repo, so you'll have to build it yourself. It should take less than 20 minutes to build on any modern system.

To create an ISO file for installation, run this command after `bluebuild` has been installed:

```
sudo bluebuild generate-iso recipe recipes/generate-iso.yml
```

After installation, for now, you can rebase to the publicly hosted GitHub images

```
# Standard image
rpm-ostree rebase ostree-image-signed:docker://ghcr.io/peterdwall/skywire-os:latest

# DX image
rpm-ostree rebase ostree-image-signed:docker://ghcr.io/peterdwall/skywire-os-dx:latest

```

---

To test builds directly, use these commands after downloading the repo:

```
# Standard image
bluebuild switch recipes/recipe.yml

# DX image
bluebuild switch recipes/recipe-dx.yml
```
