---
title: "overlayfs, unknown filesystem type"
date: 2014-08-08
forum: General Help
---

### Post by jjj3 on 2014-08-08
Hello,

I'm running on 14.04 and get "unknown filesystem type" when I try to use overlayfs. Any hints to get this working? Doing a search this seems like it should work out of the box.

Here is what I'm doing:
sudo apt-get install update
sudo apt-get install initramfs-tools
sudo apt-get install overlayroot
cd /tmp
mkdir upper
mkdir lower
mkdir overlay
sudo mount -t overlayfs -o lowerdir=/tmp/lower,upperdir=/tmp/upper none /tmp/overlay

mount: unknown filesystem type 'overlayfs'

---

