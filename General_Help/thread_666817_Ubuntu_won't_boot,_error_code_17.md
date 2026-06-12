---
title: "Ubuntu won't boot, error code 17"
date: 2008-01-13
forum: General Help
---

### Post by kingkilr on 2008-01-13
I installed ubuntu 7.10 several weeks ago using Wubi, it has been working well, however today it crashed, and when I tried to reboot I got the error, this all occurs before I even see the ubuntu loading bar: find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst Error 17: File not found, it then offers a prompt with a list of files, commandline, halt, and reboot, none of the listed files work, and I get this error no matter how many times I restart, what does this error mean, and how do I fix it

---

### Post by kingkilr on 2008-01-13
I have followed the instructions found here: [https://wiki.ubuntu.com/WubiGuide#head-7e1711f45843d41aff1ec27f06cdf8aca70cb88c](https://wiki.ubuntu.com/WubiGuide#head-7e1711f45843d41aff1ec27f06cdf8aca70cb88c) and I am still having the same problem, any help would be really appreciated.

---

### Post by kingkilr on 2008-01-14
Looking at C:\wubi\disks\ I don't see anything, I assume that is bad, especially since I didn't delete anything, suffice to say it it up and deleted all my stuff I am going to be very mad.

---

### Post by ago on 2008-01-14
Run chkdsk /r on the windows partition containing wubi

---

### Post by kingkilr on 2008-01-14
I have already run CHKDSK, both /r and /f.

---

### Post by ago on 2008-01-14
Look at the folder using a linux live CD, there might be some autorecovery .files in there.
Is the free size what you expect? Or is it like the space of wubi files was not released?

---

### Post by kingkilr on 2008-01-14
I'm fairly new to linux, could you explain or provide a link to exactly how to do those things(I have the 7.10 CD handy).

---

### Post by ago on 2008-01-15
Burn a live CD (e.g. ubuntu)
Then reboot with the CD in
Then mount the partition with the command

mkdir tmpmnt
sudo mount /dev/sda1 tmpmnt
ls -al tmpmnt/ubuntu/disks

sda1 might in fact be sda2 sda3, sdb1, sdb2 where a=disk, 1=partition

---

### Post by c0met on 2008-01-15
Hi,

Before getting into the code and stuff, it might be easiest if you downloaded a bootable ISO for the program called SuperGrub. Burn this to a CD and then boot your system from this CD. It will give you options for...

    * making your win(dows) drive bootable
    * making your linux drive bootable
    * setting your system up for a dual boot

If you have Windows on one drive and Linux on the other, then you simply need to choose the dual boot option and it will setup the Grub menu for you so that you can select which operating system to boot into.

This is a great little program to have on hand. It's got me out of a few tight spots. It's not perfect but it's worth a try. You can download the ISO from...

[[URL="http://users.bigpond.net.au/hermanzo...bDiskPage.html"]http://users.bigpond.net.au/hermanzo...bDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")[/URL]

---

