---
title: "No desktop icon for external drives"
date: 2007-03-18
forum: General Help
---

### Post by rogblake on 2007-03-18
Suddenly I've been having problems with external USB drives connected to my Dapper system not automatically showing up as desktop icons when they are plugged in. Although it's not all that big a deal to manually mount them (have done that with every other Unix and Unix-like system I've used for many years), I have to admit getting lazy and accustomed to that particular automation feature.

Looking at the system log file, what happens is that the drives are properly recognized by the system, creating an appropriate device node such as /dev/sdb1. From there things work differently depending on which external drive is plugged in...

With my 250GB external drive (1 partition formatted ext3), the drive automatically mounts into /media/usbdisk. (The 'usbdisk' directory is automatically created if it is not present.) However, no desktop icon appears, so the disk has to be umounted from the command line before unplugging.

When I connect either of my USB flash drives in (1GB Lexar and 4GB Simpletech, formatted FAT32), the drive is recognized and the device node created, but it is *not* automatically mounted. (And of course no desktop icon either.)

I have not installed any new software packages lately, and for that matter being on a very slow dialup connection (19.2k), the system has not had any updates since its initial installation. There have also been been no recent changes to /etc/fstab (no entries for any of the /dev/sd* devices).

I'm not real familiar with the magic behind the automounting. Any ideas how to get this working again?

---

### Post by Patrick Urs on 2007-03-18
I'm having a very similar problem in edgy, except with my dvd drive.

---

### Post by tacubuntuforums on 2007-03-18
Me too.

Suddenly I've been having problems with external USB drives.

After booting, when plugged in:
1. The system is no longer automatically showing its corresponding desktop icon.
(With whichever USB connector i try).
2. /dev/sda1 des not exist, so I can't even mount the drive manually.
3. Menu:Applications>Desktop prefs>Removable media settings are ok.
4. If I run lsusb the cursor blinks without returning control. I can't kill the process (in state D+) neither with 'Ctrl-c' nor 'kill -9'  until I close the tty from where I launched the command.

But, everything is fine when I boot with the same USB drive plugged in.


The only 'strange' things I can think i've made are:
a) I have installed a damn small linux in it
b) Since I'm using a new screen (new for me, but a bit old) my sistem sometimes freezes and i have to turn power off. I still don't know exactly when this happens, but generally when it's idle or off for a certain time and screensaver starts, but not always, though.

I don't have the slightest idea where to start looking what's going on.

---

