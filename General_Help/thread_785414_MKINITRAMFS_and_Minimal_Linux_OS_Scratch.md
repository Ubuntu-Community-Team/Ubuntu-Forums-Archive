---
title: "MKINITRAMFS and Minimal Linux OS Scratch"
date: 2008-05-07
forum: General Help
---

### Post by LuisPT on 2008-05-07
[FONT="Arial"]Hello guys,

I didn't know where to put this, so I've created this topic under General Help forum.

I'm using Ubuntu Gutsy in my laptop as host system to develop a kind of linux from scratch, or else, a minimum linux OS: just the kernel and busybox (maybe one day I will  compile and install grub, xorg and xfce just for fun).

Anyway, Gutsy it's installed in /dev/sda7 and I'm building that minimal linux scratch OS in /dev/sda5 partition.

I've already created filesystem structure (the folders). the dev's with MAKEDEV, compiled and installed the latest (2.6.25.2) kernel & modules. I've already also compiled and installed busybox (last stable also).

But now I have a problem: I must create the initrd.img file so I can add it to grub for booting to /dev/sda5.

I've already know that the tool to use is MKINITRAMFS, with this command (more or less):
mkinitramfs -k -o /boot/initrd.img-$(uname -r)


My doubt is that when I use that initramfs command above, since I'm working in Gutsy enviroment, it will search /boot on sda7 (where is installed Gutsy) and will create the initrd image file of the kernel version and the filesystem that Gutsy is using, instead of the kernel and the filesystem on sda5 that is newer (2.6.25.2) than the Gutsy Kernel.

Does anybody know how to use mkinitramfs in a way that it will create the initrd.img of the 2.6.25.2 instaled on SDA5 instead of the kernel of Gutsy on SDA7 (please remember that on SDA7 it's installed GUtsy that's being used to deploy a linux OS on SDA5)? :confused:

I've already remember that maybe CHROOT would do the trick, but for that I would have to mount /proc and /sys on SDA5 but those two folders are totaly empty on SDA5. The mkinitramfs doesn's exist installed on SDA5 /sbin folder (remember just kernel and busybox), so I suspect that will not run on chroot enviroment (just a gess). :confused:

I would apreciate your help in this matter, because at the moment I'm stucked at this point.[/FONT]

---

