---
title: "Need help resizing a partition..."
date: 2008-01-11
forum: General Help
---

### Post by XtremeGamer99 on 2008-01-11
I'm trying to upgrade Ubuntu from 7.04 to 7.10, but I don't have enough space on /boot (I'm short about 29M). The /boot is mounted from a 32MB ext2 partition; I structured it like this because this Linux is running off of a old Dell Poweredge 2300, and it can't read the entire ~260GB for booting (comes back as a GRUB error). I decided to install the boot partition as the beginning of the drive, and allocate only a small space for it.

But now I need to resize it some. To about 64M. I've tried using GParted, but it says that /boot can't be unmounted... Any help?

Edit: I also have free space on the drive and an 8GB flash drive, so if there's any way to make a temp /boot (thus not messing with the 32MB) on any of those drives and have the update run off that, that'll work for me. But again, I have no idea how to do that... =)

---

### Post by richardjennings on 2008-01-11
If you have enough ram - run a live cd - then gparted will be able to umount all partitions on your harddrive - letting you move stuff about.

How are your partitions laid out?

It sounds like your going to have to shift a load of data to leave the free space at the start of the drive, which will take ages. 

If you dont have enough ram to run the live cd - you can do it from a 'live terminal' cd like debian. You will need to manual use fdisk which isnt quite as easy as gparted.

---

### Post by djrobthaman on 2008-01-11
> If you have enough ram - run a live cd - then gparted will be able to umount all partitions on your harddrive - letting you move stuff about.

I was about to say the same thing.  But this might be a bit redundant.  If you're going to download the livecd, maybe you should just do a clean install.

---

### Post by ronmarley1 on 2008-01-11
Another option, that will run on less ram than the live CD, is the gParted LiveCD.  It worked quite well for me.
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

