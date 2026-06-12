---
title: "zfs root grub boot confusion"
date: 2015-08-16
forum: General Help
---

### Post by TheKeyMaker on 2015-08-16
So I am attempting a zfs root install with ubuntu and am stuck on trying to get it to boot with grub.

From what I have read on the zfsonlinux github pages:
[https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-to-a-Native-ZFS-Root-Filesystem]("https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-to-a-Native-ZFS-Root-Filesystem")
[https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-14.04-or-Later-to-a-Native-ZFS-Root-Filesyste]("https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-14.04-or-Later-to-a-Native-ZFS-Root-Filesyste")

It looks like the zfsonlinux/grub ppa doesn't support trusty or any newer versions
[https://launchpad.net/~zfs-native/+archive/ubuntu/grub]("https://launchpad.net/~zfs-native/+archive/ubuntu/grub")

So, I have created a gpt formatted drive in virtual box with the following partitions:
Device         Size    Type
/dev/sda1    2G      swap
/dev/sda2    256M   boot  - to be used for grub /boot/grub.  I thought this was the right way to do this???   Is the type boot correct?
/dev/sda3    29.8G  Linux filesystem - zfs root

I then created my zpool and zfs datasets.

Set mountpoints and bootfs to the datasets
zfs set mountpoint=/ ${POOL_NAME}/ROOT/ubuntu-1
zpool set bootfs=${POOL_NAME}/ROOT/ubuntu-1 $POOL_NAME

I kept following the first guide above and got to this:
debootstrap trusty /mnt 

I then copied over all the files needed and bind the right directorys and chrooted into the new root
chroot /mnt /bin/bash --login

In the chrooted environment I ran the following:
locale-gen en_US.UTF-8
apt-get update
apt-get install ubuntu-minimal software-properties-common
apt-add-repository --yes ppa:zfs-native/stable
apt-get update
apt-get install --no-install-recommends linux-image-generic linux-headers-generic
apt-get install ubuntu-zfs
apt-get install grub2-common grub-pc
apt-get install zfs-initramfs
apt-get dist-upgrade
passwd root 

That all went fine....

Now I am confused on where I go from here.  I have tried running grub-install on different things, but I am getting a lot of "error: failed to get canonical path of $HD"

grub-probe / also doesn’t give be "zfs" so I assume the grub I am using doesn't support zfs....

Has anyone here done this and could provide me with the steps to get my grub install working!   Thanks for your time!

---

### Post by dino99 on 2015-08-16
a recent zfs answer

[http://askubuntu.com/questions/651327/zfs-root-filesystem](http://askubuntu.com/questions/651327/zfs-root-filesystem)

---

### Post by TheKeyMaker on 2015-08-16
Hi dino99 thanks for the response.

I had seen that post but it still didn't provide the answer I was looking for.

> Advanced users can sometimes get the desired result using the basic ZFS support that is already in distro. In the HOWTO that you are using here, there should be links to alternative tutorials created by the ZoL community. 

I have tried a number of tutorials and haven't got things to work.  I was looking to see if I could find someone who has tried this recently to give me instruction.

I will post back if I get something working also...

Thanks!

---

### Post by lukeiamyourfather on 2015-08-18
If you're using a recent release of Ubuntu then GRUB already supports ZFS. That's probably why the GRUB in the ZFS repository doesn't support newer distributions, because it doesn't need to. I haven't tried to use ZFS for root but I'm curious to try it.

---

