---
title: "fsck"
date: 2008-06-18
forum: General Help
---

### Post by Frogster on 2008-06-18
fsck at start up stops at

Starting common unix printing system: cupsd

It will just sit there.....:(

Help! what do I need to do to get it past this point so that i can use it?

---

### Post by Frogster on 2008-06-18
Anybody

---

### Post by Frogster on 2008-06-18
Do I just erase the disk and start again?

---

### Post by VMC on 2008-06-18
Did ubuntu ever work? What happened during the install phase?

Some background would be helpful. Type of hard drives, system used.

---

### Post by Frogster on 2008-06-19
> **VMC said:**
> Did ubuntu ever work? What happened during the install phase?

Some background would be helpful. Type of hard drives, system used.

Thank you. Ubuntu 7.10 installed with no difficulty and about two weeks ago and has been updated with no hassles.
Ubuntu boots from the one maxtor 40mb ide drive, no other OS is present.

If any other info is needed I am happy to provide it as at this point I am really clueless as to what is happening.

:)

---

### Post by VMC on 2008-06-19
> **Frogster said:**
> Thank you. Ubuntu 7.10 installed with no difficulty and about two weeks ago and has been updated with no hassles.
Ubuntu boots from the one maxtor 40mb ide drive, no other OS is present.

If any other info is needed I am happy to provide it as at this point I am really clueless as to what is happening.

:)

It appears that ugrading from 7.10 to 8.04 has many issues. There are many fixes for this. I installed straight from 8.04 without any issue. Since you only have a 49gig hard drive it doesn't seem feasible to install 8.04 alone to see if it boots correctly, so output these commands from a Terminal and lets have a look see:

```
fdisk -l
cat /boot/grub/menu.lst

```

Apparently they will have to be done from a livecd since you can't boot up directly. Make sure you get the correct menu.lst from the fdisk message. Also have you tried to boot using "recovery mode" image?

---

### Post by Frogster on 2008-06-19
Thank you for taking the time with this. I cannot seem to get any response from the terminal regarding fdisk -l or the cat /boot/grub/menu.lst

How do I boot using the "recovery mode" image? I have never heard of this option

---

### Post by russlar on 2008-06-19
> **Frogster said:**
> Thank you for taking the time with this. I cannot seem to get any response from the terminal regarding fdisk -l or the cat /boot/grub/menu.lst

How do I boot using the "recovery mode" image? I have never heard of this option

"recovery mode" gives you a root command line.

---

### Post by VMC on 2008-06-19
> **Frogster said:**
> Thank you for taking the time with this. I cannot seem to get any response from the terminal regarding fdisk -l or the cat /boot/grub/menu.lst

How do I boot using the "recovery mode" image? I have never heard of this option

When you boot up does grub boot? If you get some Grub message, instantly push the ESC key, and you should see the menu to choose from

---

### Post by Frogster on 2008-06-24
fdisk -l

returns disk details
Disk /dev/hda : 40.9 gb

Device boot is /cev/hda1 

cat /boot/grub/menu.lst

returns three kernels
ubuntu 7.10, kernel 2.6.22-14-generic 
root (hc0,0)

ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)

ubuntu 7.10, memtest86+

---

### Post by VMC on 2008-06-24
> **Frogster said:**
> fdisk -l

returns disk details
Disk /dev/hda : 40.9 gb

Device boot is /cev/hda1 

cat /boot/grub/menu.lst

returns three kernels
ubuntu 7.10, kernel 2.6.22-14-generic 
root (hc0,0)

ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)

ubuntu 7.10, memtest86+

Those outputs don't look right. Just copy and paste each one between the codes "#"
that way we can make a determination.

```
sudo fdisk -l
cat /boot/grub/menu.lst
```
So we need the outputs from the Terminal just as they are.

---

### Post by Frogster on 2008-06-26
I wish it was a case of copy and paste :-) I have two computers running one monitor and everything has to be typed in, written down and then retyped!

I will get the outputs up "soonish" thank very much for you patients and help

---

### Post by mcduck on 2008-06-26
> **Frogster said:**
> I wish it was a case of copy and paste :-) I have two computers running one monitor and everything has to be typed in, written down and then retyped!

I will get the outputs up "soonish" thank very much for you patients and help

IF you have any removable drive, USB stick or anything then just redirect the output of those comamnds into text files and then move those files to the other machine..

```
sudo fdisk -l > disks.txt
cat /boot/grub/menu.lst > grub.txt
```

---

### Post by Frogster on 2008-06-28
Thank you everybody for your help. At present I cant even get a live cd to work! I have been into the bios and made the cd drive the first boot option and disabled the other options but it seems that grub will do what it wants and loads the knacked kernel, run fdisk and hang! I think this disk may be heading for the bin unless I can completely reformat it and start afresh.

---

### Post by mcduck on 2008-06-28
> **Frogster said:**
> Thank you everybody for your help. At present I cant even get a live cd to work! I have been into the bios and made the cd drive the first boot option and disabled the other options but it seems that grub will do what it wants and loads the knacked kernel, run fdisk and hang! I think this disk may be heading for the bin unless I can completely reformat it and start afresh.

If you have correctly configured BIOS to boot from the CD before any hard disks, the machine should never even get as far as loading GRUB.. So if you aren't able to boot from the CD, GRUB sure isn't causing your problems but they are result of something else.

---

### Post by Frogster on 2008-06-28
Thanks mcduck, that is exactly what is causing me to scratch my head at the moment.

---

### Post by VMC on 2008-06-28
> **Frogster said:**
> Thanks mcduck, that is exactly what is causing me to scratch my head at the moment.

Are you sure you have inserted a bootable cdrom disk?

---

