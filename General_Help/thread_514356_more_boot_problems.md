---
title: "more boot problems"
date: 2007-07-31
forum: General Help
---

### Post by guernicaaa on 2007-07-31
okay, i've always had problems getting xp and ubuntu to dual-boot.  on a few rare occasions, i was always able to boot into both interchangeably, but that was a thing of the past.  i finally gave up for a couple months and just used windows.  i miss ubuntu dearly so today, i thought i'd give it another shot.  on my 300gb hard drive, i installed windows to a 150gb partition and left the other 150gb blank.    so i installed ubuntu onto that other 150gb partition.  but when i restarted after the live cd, it went right into windows.  then after another restart, my pc won't boot, it just says "Invalid partition table"
how can i make the partition table valid and choose between windows and ubuntu?
edit:  now, when i put in my windows xp disk, i'm able to choose between my operatin systems!  wtf?!@

---

### Post by fjgaude on 2007-07-31
Gosh, this sounds like a big disk... you might start all over again and see what happens. Reformat the disk, install Windows, then install Ubuntu.

Or using the Live CD use the tools there if see what the disk is doing, like run in a terminal df -h, see if you can mount anything. Act like a detective with the tools at hand in the live cd.

frank

---

### Post by guernicaaa on 2007-08-04
I'm just wondering why it works when I have a WinXP CD in the drive.  It says
"Press any key to boot from CD..." and if I let it go, GRUB comes up, if I press a key, I can install Windows.

---

### Post by guernicaaa on 2007-08-06
bump

---

### Post by anaconda on 2007-08-06
Some older bioses didn't allow booting from above 80GB from the hd. And the way around that was to make a small boot partition to the beginning of the drive..

Just tought to mention..

---

### Post by guernicaaa on 2007-08-08
no, because my pc has booted up from the 300gb hard drive when I just had Windows on it

---

### Post by guernicaaa on 2007-08-10
bump

---

### Post by guernicaaa on 2007-08-12
bump
please somebody help me out

---

### Post by guernicaaa on 2007-08-16
please?

---

### Post by guernicaaa on 2007-08-20
Help Please?!

---

### Post by merlinus on 2007-08-20
I have not heard of this problem before, but let's look at some of your files and partitions after booting ubuntu:

```

sudo fdisk -l
cat /boot/grub/menu.lst
cat /etc/fstab

```-merlin

---

