---
title: "Mounting NTFS disk"
date: 2006-10-30
forum: General Help
---

### Post by ephie on 2006-10-30
Hello,

How can I mount a NTFS disk onto Ubuntu.

I must have some kind of user priviledge problem because when I "cd" to the directory where my disk is mounted I only have access if I'm root and not a normal user!

How can I mount a NTFS disk so that a "normal" user on Ubuntu has access to the files?

Thanks

eph!e

---

### Post by pay on 2006-10-30
sudo chown -R <your user name>:<your user name> /path/to/ntfs/

---

### Post by raven12 on 2006-10-30
I was going to ask the same thing lol

---

### Post by robertwoes on 2006-10-30
eph!e, raven12:

Adding the parameter [FONT="Fixedsys"]umask=000[/FONT] to the *fstab* (the filesystem tabular file) should fix your permissions issue.

[FONT="Arial Black"][COLOR="DarkRed"]**Warning:  If you make a mistake while editing /etc/fstab, you may not be able to boot into Ubuntu (without a big pain in the neck!) ](*,)   Make sure you know what you are doing BEFORE you edit!**[/COLOR][/FONT]

I highly recommend that you take a look at Långstedt's article on */etc/fstab* and the Gentoo Wiki (the last two links below)**[COLOR="DarkRed"] before[/COLOR]** editing, as this post is by no means exhaustive.

With superuser priveleges start your favorite text editor (If you don't know how, try [FONT="Fixedsys"]info sudo[/FONT] from a terminal and/or check out "*RootSudo*" from The Ubuntu Community Documentation at [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")).  Open */etc/fstab*.  If you are adding the first disk of the first partition insert this (or append to the existing line):

[FONT="Fixedsys"]/dev/hda1 /mnt/win-ntfs ntfs user,ro,auto,exec,umask=000   0     0[/FONT]

[COLOR="Navy"]If your NTFS partition is the second disk, second partition, it would be [FONT="Fixedsys"]hdb2[/FONT].  Of course, if you already have a line for that partition in your */etc/fstab*, you may be using another mount point, e.g. [FONT="Fixedsys"]/media/windows[/FONT].  Whatever the mount point, just check the [FONT="Fixedsys"]/dev/hdxy[/FONT]  part of the line to add the [FONT="Fixedsys"]umask=000[/FONT] parameter to the one that corresponds to the correct disk/partition (where [FONT="Fixedsys"]x[/FONT] is the disk number and [FONT="Fixedsys"]y[/FONT] is the partition letter).[/COLOR]

The parameters above ([FONT="Fixedsys"]user,ro,auto,exec,umask=000[/FONT])  will allow users read-only access to the drive (which is very important because writing to an NTFS filesystem in Linux is still risky at this point), mount the partition automatically at boot ([FONT="Fixedsys"]auto[/FONT]), and allow you to execute something from the drive ([FONT="Fixedsys"]exec[/FONT]).  The [FONT="Fixedsys"]umask[/FONT] parameter sets the octal file permissions.  This is explained nicely on the Gentoo Wiki link I've included below.

To mount on the fly, or if you decide not to mess around with your */etc/fstab* file, do (from a terminal with superuser priveleges):

[FONT="Fixedsys"]mkdir /mnt/win-ntfs
mount -t ntfs /dev/hda1 /mnt/win-ntfs ro umask=000
cd /mnt/win-ntfs
ls[/FONT]

I'm pretty sure you can have *GRUB* mount it too (though it certainly is not the usual way of doing it)

There's a lot of information about this here:

"*Mounting an NTFS partition/hard disk*" by nil:
[http://www.linuxforum.com/linux_tutorials/1/1.php](http://www.linuxforum.com/linux_tutorials/1/1.php)

"*How to edit and understand /etc/fstab - 1.1*" by Nana Långstedt:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

"*HOWTO Mount Windows partitions (DOS, FAT, NTFS)*" from Gentoo Wiki:
[http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS)](http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS))

If anything here is unclear feel free to ask me to clarify for you.  There's no shame in it.  :)

GOOD LUCK!
 
-Robert

P.S. Recommended Reading (Amazon.com has them cheap):

_Linux Desktop Pocket Guide_
By David Brickner

_Ubuntu Hacks: Tips & Tools for Exploring, Using, and Tuning Linux_
By Jonathan Oxer, et al.

---

### Post by ephie on 2006-10-30
Wow!

Thank you for the answer!

I will try it out when I get home!

Thanks!

eph!e

---

### Post by robertwoes on 2006-10-30
My Pleasure.   :grin: 
-Robert

---

### Post by ephie on 2006-10-30
hi robertwoes,

I got my hda1 (ntfs) mounted as read only. Apparently I won't be able to write on it....

Now I would like to get my second HD mounted (hdb1) but it's formated as SFS:

```

root@fanny-desktop:/mnt/hdb1# sudo fdisk -l

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3451    27720126    7  HPFS/NTFS
/dev/hda2            3452        7308    30981352+  83  Linux
/dev/hda3            7309        7476     1349460    5  Extended
/dev/hda5            7309        7476     1349428+  82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36483   293049666   42  SFS


```

How can I mount a SFS and can I get read AND write access to it?

thank again for your help!

eph!e

---

### Post by robertwoes on 2006-11-05
Sorry, eph!e, my computer was down for a week...  Well, I haven't the slightest idea.  I saw your post @ [http://ubuntuforums.org/showthread.php?t=192275](http://ubuntuforums.org/showthread.php?t=192275) and I'm curious if you might consider making a 15 GB shared partition in vfat at the end of your hdb1 until you can write to the SFS partition?

I did it back in the day before i knew how to mount my NTFS partition.  I would just drop stuff there from windows and pick it up from linux, and vice versa.  lol -- those were the days...

Wish I could help out more, but I just don't know.  

Happy Hunting.

-Robert

---

### Post by evil_cat on 2008-04-04
> **pay said:**
> sudo chown -R <your user name>:<your user name> /path/to/ntfs/

Thank U works out fine for me

---

