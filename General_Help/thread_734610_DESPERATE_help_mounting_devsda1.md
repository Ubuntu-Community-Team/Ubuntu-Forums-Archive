---
title: "DESPERATE help mounting /dev/sda1"
date: 2008-03-24
forum: General Help
---

### Post by Jonnybeeee on 2008-03-24
I've been tryin to solve this problem on my own for a few days now, because i figured that is the best way to learn, but i'm stuck where I am now..

Originally i had a problem logging into Gutsy 7.10 . When it got to the login screen it was flashing the login and the background color (light blue) it would show me the login box and everything but just kept flashing infinitively so i couldnt do anything until i hard-powered off.

using terminal in recovery mode i deleted some recently upgraded programs including various used for MythTV, but I was having the same problem. i figured maybe ubuntu was having a hard time mounting my hard drive being /dev/sda1 (i'm learning this as i go sorry) After awhile of troubleshooting, i managed to delete GRUB  (error 17) comes up. so now i'm using the live cd, trying to mount my sda1 with no prevail :(  someone please help i love using ubuntu, and i'd rather fix the problem then avoid it by re-installing ubuntu.
I should also mention that i'm using a partition for VMware which i think is /dev/sda5, and its all a single sata hard drive (its a laptop)

THANK u

---

### Post by alexforcefive on 2008-03-24
> **Jonnybeeee said:**
> i'm using the live cd, trying to mount my sda1 with no prevail :( 

You can't just go to **places > computer** and then **right click > mount volume**?

Are you getting an error message?

---

### Post by Jonnybeeee on 2008-03-24
Using the live cd, everything on the computer is as if its brand new, it says the file system is only 1 gb capacity!

the only error messages i have is error 17 while trying to boot w/o the Live cd.

heres my fdisk -lu

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0db651f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   306568394   153284166   83  Linux
/dev/sda2       306568395   312576704     3004155    5  Extended
/dev/sda5       306568458   312576704     3004123+  82  Linux swap / Solaris

what comes first, try to mount my sda1, or fixing grub?

---

### Post by alexforcefive on 2008-03-25
When you're on the livecd, I'd guess that the partition called "filesystem" is actually the livecd, rather than a physical hard drive. Ok, check out the screenshot attached. The drive labelled "76.3GB Volume" isn't currently mounted, but "Big One" and "Filesystem" are. Do you have anything that looks like the unmounted volume? That's the one you're looking for.

After you get that mounted, you can hopefully fix grub

---

### Post by Jonnybeeee on 2008-03-25
Nope I get my dvd rw drive and file system. the file system doesnt look like a hard drive like yours though, it looks like a hard drive enclosure :P

Thank you for your patience

---

### Post by dcstar on 2008-03-25
> **Jonnybeeee said:**
> I've been tryin to solve this problem on my own for a few days now, because i figured that is the best way to learn, but i'm stuck where I am now..

Originally i had a problem logging into Gutsy 7.10 . When it got to the login screen it was flashing the login and the background color (light blue) it would show me the login box and everything but just kept flashing infinitively so i couldnt do anything until i hard-powered off.

using terminal in recovery mode i deleted some recently upgraded programs including various used for MythTV, but I was having the same problem. i figured maybe ubuntu was having a hard time mounting my hard drive being /dev/sda1 (i'm learning this as i go sorry) After awhile of troubleshooting, i managed to delete GRUB  (error 17) comes up. so now i'm using the live cd, trying to mount my sda1 with no prevail :(  someone please help i love using ubuntu, and i'd rather fix the problem then avoid it by re-installing ubuntu.
I should also mention that i'm using a partition for VMware which i think is /dev/sda5, and its all a single sata hard drive (its a laptop)

THANK u

Do a forum search for **reinstall grub** and follow the instructions.

---

