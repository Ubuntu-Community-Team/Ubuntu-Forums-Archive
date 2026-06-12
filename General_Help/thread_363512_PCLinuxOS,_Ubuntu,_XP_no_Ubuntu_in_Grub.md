---
title: "PCLinuxOS, Ubuntu, XP no Ubuntu in Grub"
date: 2007-02-17
forum: General Help
---

### Post by Marious on 2007-02-17
OK here is what happen I was looking around checking out the Distro watch page and what do I do well I download PCLinuxOS and decide hey I'll just use the partitions that I set aside for another Distro, so I put in PCLOS and proceed to install it, at the end I screwed up Grub because I did not put in Ubuntu and now I can't even get into my Ubuntu /me sad. OK so what do I do? Here is what I tried so far, I went into my partition that has Ubuntu /sda2, I have /sda3 set for PCLOS and I throw in the info for Ubuntu, but here is the issue well not sure if it is an issue or not, would KDE being run in PCLOS and Gnome in Ubuntu make it an issue in the end? Anyways I was looking at both Grub Files the one created by Ubuntu and the one created by PCLOS since the one that is starting is the one that PCLOS created. But they are slightly different the layout of the two files is close so since the one that was starting was PCLOS one I followed there format. Here is what I remember doing, sorry on my other machine the one with XP only on it,

OK this is not working very well bring up my other machine I will post the file formats. BRB hehe.

---

### Post by Marious on 2007-02-17
Ok here I am on PCLOS the files are as follows:

The Grub File from Ubuntu

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

**The one From PCLOS**
title linux
kernel (hd0,2)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sda3  splash=silent vga=788
initrd (hd0,2)/boot/initrd.img

title linux-nonfb
kernel (hd0,2)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sda3 
initrd (hd0,2)/boot/initrd.img

title failsafe
kernel (hd0,2)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sda3  failsafe
initrd (hd0,2)/boot/initrd.img

*This is what I added following the format from the Grub file created by PCLOS*

[COLOR="Red"]title Ubuntu, kernel 2.6.17-11-generic
kernel (hd0,1)/boot/vmlinuz-2.6.17-11-generic root=/deve/sda2 ro quiet splash
initrd (hd0,1)/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-11-generic (recovery mode)
kerner (hd0,1)/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro single
initrd (hd0,1)/boot/initrd.img-2.6.17-11-generic
boot

title  Ubuntu, memtest86+
kernel (hd0,1)/boot/memtes86+.bin
quiet
boot[/COLOR]

title windows
root (hd0,0)
makeactive
chainloader +1

OK so here is the issue when I try Ubuntu I get to the splash screen and what it does is the bar does not move it hangs and it will not start Ubuntu at all so it kind of sucks not sure what to do, how do I change it so that I can get on my Ubuntu?

Each distro has its own /home and /usr but only one /swap partition would this be an issue or can PCLOS and Ubuntu share a /swap partition? 

Hope some one can help. Oh by the way I got Beryl working on Ubuntu from a previous Post, I screwed something up before so I decided to install a fresh copy and fist thing I did was to get my updates then follow the helpful HowTo one of you guys posted. You all are super helpful reason why I like Linux vs. XP. I like PCLOS and Ubuntu both each one has its own little quirks. In Ubuntu I would have to go with Gnome I think I like it much better than KDE, I like the control center PCLOS has and PCLOS is kind of an easier distro its more windows like so a nOOb like me can learn a bit easier, Ubuntu is a bit harder but I like the challenge both are great. I wanted to try Sabayon but my box wont boot to it ah well. Again thanks for all the help guys.

Mairous

---

### Post by Marious on 2007-02-17
Ok got it working, I saw my mistake, though it seems to be working really slow for some reason. Everything is loading super slow might be my machine or something I'll take a look at it later.

---

