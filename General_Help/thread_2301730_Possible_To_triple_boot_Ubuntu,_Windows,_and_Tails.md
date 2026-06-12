---
title: "Possible To triple boot Ubuntu, Windows, and Tails"
date: 2015-11-04
forum: General Help
---

### Post by Henry_Fisher on 2015-11-04
Hello I just had a quick question. I am very very eager to install tails but I would like to keep my current Ubuntu 15.10+Windows 10 Dual boot config. Is it possible to triple boot with Tails? If so, can I just install Tails on top of my current config or do I have to reinstall all of my Operating systems? 

Thanks so much!

---

### Post by Geoffrey_Arndt on 2015-11-04
Tails is just another Linux distro . . . . i know of users that have a dozen or more distros installed along with windows.   But, these require their own partitions (unless installing to external usb drives or usb flash-sticks).   Just be careful though, as Vista 10 updates may hose other OS's via messing up bootloaders including Grub2.   Safest course is to use VM's (virtual box, etc.).     Unless you're also a gamer, Windows as a guest OS installs just fine in an Ubuntu host.

---

### Post by DK1993 on 2015-11-05
Just to throw my two cents in, the Linux distribution Tails is supposed to be used in a live environment and it is extremely cautioned not to use it on a hard disk. It completely diminishes from its primary use of remaining anonymous and keeping your information secure, as this distro is supposed to run in RAM and delete all information on the computer is powered down.

---

### Post by Bucky Ball on 2015-11-05
> **DK1993 said:**
> ... the Linux distribution Tails is supposed to be used in a live environment ...

^^^
This. Tails is not intended for hard drive installs. Otherwise, considering distros that are intended for install on hard drive, yes, you can triple boot without issue. You just need free space on the drive to create a partition and install to. You can even use the existing /swap partition and the existing /home partition, if you have one. 

I currently have four installs, Win7, mini installs of 12.04 and 14.04 and an old 10.10 I've been meaning to get rid of for awhile. Still boots, though, not that it ever gets used anymore. :)

(* Sorry, make that five. I have a couple of 14.04s. All the Linux installs use the same /swap, same /data partition. No confusion, folders are linked to the same data regardless of which I boot into.)

PS: Just to reiterate, no, you don't need to wipe the lot and reinstall all your OSs. Just make free space for the new install and you're good to go. If you have to, shrink Win OS partitions by booting into Win and using its disk management software, Linux using live media and Gparted from the 'Try Ubuntu' desktop.

---

### Post by mastablasta on 2015-11-05
you can also use virtual box or similar so you don't need to keep booting and rebooting.

---

### Post by Geoffrey_Arndt on 2015-11-05
Good info about Tails and running it live in dynamic ram  . . . . all data except off-loaded saves are wiped upon reboot or shutdown.    The possibility to actually install it to usb flash-stick is very interesting.   Think I'll do that as a mini-project.

---

### Post by gordintoronto on 2015-11-06
Bucky: if you share a /home partition, it is possible to get into difficulty with incompatible config files. One solution is to have user Bucky under Ubuntu 12.04, and user Ball for Xubuntu 15.10, for example.

---

### Post by Bucky Ball on 2015-11-06
Cool. I actually leave /home as a directory in /, delete all the folders in there after install, like Documents, Pictures, Videos, etc., and create symlinks to folders of the same name on /data. I don't have a /home partition, as such. Haven't used the separate /home method myself in about four or five years. Having a separate /data partition does the same thing without storing the config files for all users on a /home partition. 

Therefore, all installs have the symlink, for instance, Documents in their /home directory and they all link to one single directory, /data/Documents on the one partition, /data. :D I have four installs all linked to the same /data partitions and the personal data in directories inside that. I only need to backup /data to back up my personal stuff. 

Much better option.

---

### Post by pauljw on 2015-11-06
> **Geoffrey_Arndt said:**
> Good info about Tails and running it live in dynamic ram  . . . . all data except off-loaded saves are wiped upon reboot or shutdown.    The possibility to actually install it to usb flash-stick is very interesting.   Think I'll do that as a mini-project.

This is extremely easy.  Download the iso and install it on a CD.  Live boot the CD and use the install software to install it to the usb stick.  Be sure to read all the documentation regarding the proper use.  I just did this yesterday, everything went very smoothly and Tails is an interesting distro.

Good luck.

---

### Post by Mike_Walsh on 2015-11-07
You can have as many distros on your machine as you like....I currently have five. Just need space for them, as Bucky says. But I will echo the other posters (from experience); Tails **is **intended for 'live' environment only. If you want a permanent 'icognito' browser, just use Tor.....which is based on FireFox. Works fine. You really don't need the whole incognito **system**.

[http://www.webupd8.org/2013/12/tor-browser-bundle-ubuntu-ppa.html](http://www.webupd8.org/2013/12/tor-browser-bundle-ubuntu-ppa.html)

I've installed its PPA using the instructions on this page before, with no issues.

If you still want to **install** Tails, use UNetbootin to create a 'live' USB. That's the recommendation on the Tails home page.....and what I did myself when I tried it last year. Works A-OK like that.

You do **NOT** want to install it to your hard drive. Tails uses use a rather peculiar bastardized form of EFI, which will overwrite whatever your system uses (either MBR or UEFI)....and leave it unable to boot into anything else. I say this from experience; I tried that, too. **Never** again. Don't go there!

You'll have to re-install everything from the ground up; and gParted will complain about formatting the disk, as the partition table needs to be re-created.

A 'live' USB is best; trust me..!


Regards,

Mike. ;)

---

