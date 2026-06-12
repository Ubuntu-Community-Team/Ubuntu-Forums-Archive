---
title: "Getting &quot;Blank DVD-R Disc&quot; icon with any media inserted on TSSTcorpCD/DVDW TS-H552U"
date: 2007-04-05
forum: General Help
---

### Post by carlbastos on 2007-04-05
Hi there!
This is my first post here, and yes, I'm a noob :(  ...

I just installed Ubuntu 6.10 and noticed that my DVD writer isn't reading any media(DVD or CD) that I insert in it. I can see the drive icon on the gnome desktop, but it's labeled "Blank DVD-R Disc" and when I open it, Nautilus gives me an empty drive folder.
The odd thing is that my other drive (a LG 52x cd-rom drive) works normally.

I can still access the DVD content by mounting it manually with:

```
mount /dev/hdc
```

but from "Places > Computer" and the Desktop Icon it doesn't work...

Maybe a fstab issue?

My drive is a Samsung Writemaster (TSSTcorpCD/DVDW TS-H552U), and here's my fstab:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=a7722f59-e0d6-438f-87d9-884ea9daa88d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=2079-D0BC  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=535ed3b6-ceb3-43db-9f7a-166f4af36989 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


hda1 is my WinXP partition
hda2 is my ubuntu fsystem
hda3 is swap
hdd is my CD drive
[COLOR="Red"]hdc is my DVD drive[/COLOR](the one mentioned on this post)

Does anyone know the reason?

thanks in advance,

carL

---

### Post by chewearn on 2007-04-06
I have seen some users reporting a similar problem now and again in this forum.  Personally, I have also seen similar problem in two different ubuntu systems (one Dapper system almost a year ago, and an Edgy system recently).  In both cases, the DVD drive were the same make/model.

I found this bug report, which might explain the problem:
[https://launchpad.net/ubuntu/+source/hal/+bug/14692](https://launchpad.net/ubuntu/+source/hal/+bug/14692)

---

### Post by carlbastos on 2007-04-15
I also discovered a workaround, but it&#347; a little bit inconvenient.
Every boot (sometimes even after restarting X) I have to use the following command on a terminal:
```
sudo /etc/initd.d/dbus restart
```

and get this output:
```

 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 
 * Starting system message bus dbus                                      [ OK ] 
 * Starting Hardware abstraction layer hald                              [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Starting System Tools Backends system-tools-backends                  [ OK ] 

```


This command makes all my drives available on the desktop/computer, like it would have to work...
I could use this command automatically on boot, but it opens a annoying nautilus window every time i type it =/

(PS: I upgraded to Feisty, and the issue continues)

---

### Post by mckryptyk on 2007-05-10
Hi just thought I comment because I have the same drive.

I've tried it on i386 an amd64 versions of dapper and feisty.
I have had no problems at all with either dvd, cd-r or cd-rw media.

I assume that your drive works perfectly in windows.

what firmware version do you have for it?
I have US07, perhaps that might affect communication between the drive and dbus subsystem.

I am currently using feisty amd64 with multiverse and universe  repositories enabled and no other repositories added besides those.

Are you using a beta (herd) cd to install ubuntu? (that could be partly responsible for setting things up incorrectly)

Hope that helps, I'll check back here later.

Cheers.

---

### Post by carlbastos on 2007-05-12
I realized that my drive works with cd's, not with DATA DVD's, but the mount points are a mess... sometimes my TSS drive mounts on the other driver(LG) mount point. Whatever... when it's a DATA DVD I have to mount it manually, and I can only access it throug /media/ folder 'cause it doesn't appear on desktop/my computer.

I installed it with 6.10 edy livecd and upgraded to Feisty 7.04(i386).

same repositorys here(with some additional not related to "drives").

I don't know anything about firmwares on this drive :(

Still not working correctly.

---

### Post by mckryptyk on 2007-05-13
Could you post your /etc/fstab so I could see?

Also  these two files should look like this:

"ls -la /" 
lrwxrwxrwx   1 root root    11 2005-02-01 07:16 cdrom -> media/cdrom

"ls -la /media"
lrwxrwxrwx  1 root root       6 2005-02-01 07:16 cdrom -> cdrom0

And at boot, your bios should display something like this:

"TSST-Samsung US07"  ( From memory, I mean who remembers this :) )

Also I assume that under: 
"System > Administration > Users and Groups > YourUserName >Properties" 
that you have permission to use cdrom.

I'll check back later.

Cheers.

---

### Post by carlbastos on 2007-05-15
Hi there!

My FSTAB now:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=a7722f59-e0d6-438f-87d9-884ea9daa88d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=2079-D0BC  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=535ed3b6-ceb3-43db-9f7a-166f4af36989 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc	/media/cdrom1	udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1	/media/hdb	vfat	defaults,utf8,umask=007,gid=46	0	1
```
---
ls -la /:

```
$ ls -la /
total 132
drwxr-xr-x  23 root root  4096 2007-05-02 14:53 .
drwxr-xr-x  23 root root  4096 2007-05-02 14:53 ..
drwxr-xr-x   2 root root  4096 2007-04-12 16:29 bin
drwxr-xr-x   3 root root  4096 2007-04-16 08:14 boot
lrwxrwxrwx   1 root root    11 2007-04-05 07:22 cdrom -> media/cdrom
drwxr-xr-x   3 root root  4096 2007-04-10 00:48 debian
drwxr-xr-x  12 root root 13840 2007-05-15 01:59 dev
drwxr-xr-x 117 root root  8192 2007-05-15 01:57 etc
drwxr-xr-x   4 root root  4096 2007-04-10 13:22 home
drwxr-xr-x   2 root root  4096 2006-10-25 10:26 initrd
lrwxrwxrwx   1 root root    33 2007-04-16 07:53 initrd.img -> boot/initrd.img-2.6.20-15-generic
drwxr-xr-x  14 root root  8192 2007-04-18 01:47 lib
drwxr-xr-x   2 root root 49152 2007-04-05 07:20 lost+found
drwxr-xr-x   9 root root  4096 2007-05-15 01:43 media
drwxr-xr-x   2 root root  4096 2006-10-19 19:49 mnt
drwxr-xr-x   5 root root  4096 2007-04-23 01:21 opt
dr-xr-xr-x 128 root root     0 2007-05-14 22:39 proc
drwxr-xr-x   2 root root  4096 2007-05-03 20:51 Recycled
drwxr-xr-x  26 root root  4096 2007-05-12 18:40 root
drwxr-xr-x   2 root root  4096 2007-05-08 16:06 sbin
drwxr-xr-x   2 root root  4096 2006-10-25 10:26 srv
drwxr-xr-x  11 root root     0 2007-05-14 22:39 sys
drwxrwxrwt  15 root root  4096 2007-05-15 02:34 tmp
drwxr-xr-x  13 root root  4096 2007-05-06 23:41 usr
drwxr-xr-x  15 root root  4096 2006-10-25 10:39 var
lrwxrwxrwx   1 root root    30 2007-04-16 07:53 vmlinuz -> boot/vmlinuz-2.6.20-15-generic
```

--
ls -la /media:

```
$ ls -la /media
total 50
drwxr-xr-x  9 root root        4096 2007-05-15 01:43 .
drwxr-xr-x 23 root root        4096 2007-05-02 14:53 ..
lrwxrwxrwx  1 root root           6 2007-04-05 07:22 cdrom -> cdrom0
drwxr-xr-x  2 root root        4096 2007-04-05 07:22 cdrom0
drwxr-xr-x  2 root root        4096 2007-04-05 07:22 cdrom1
lrwxrwxrwx  1 root root          45 2007-04-10 08:40 .directory -> /etc/kubuntu-default-settings/directory-media
lrwxrwxrwx  1 root root           7 2007-04-05 07:22 floppy -> floppy0
drwxr-xr-x  2 root root        4096 2007-04-05 07:22 floppy0
-rw-r--r--  1 root root          69 2007-05-15 01:43 .hal-mtab
-r-x--x--T  1 root root           0 2007-04-10 08:17 .hal-mtab-lock
drwxrwx--- 13 root plugdev    16384 1969-12-31 21:00 hda1
drwxr-xr-x  2 root root        4096 2007-05-10 20:47 hdb
lrwxrwxrwx  1 root root          42 2007-04-06 16:53 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwxr-xr-x  2 root root        4096 2007-04-29 04:24 isoimage
dr-xr-xr-x  3 carl 4294967295    92 2005-02-19 09:23 Marie_2
```

and yup, I have cdrom permissions

what about that dbus restart command? why does it solve my problem and create a lot more?

[]'s

---

### Post by mckryptyk on 2007-05-23
Hi, I know this is a late reply but, I am wondering if you have tried searching bugtraq, launchpad, or kde's bug listings for "dbus cdrom". 

I wish I could have been of more help but I don't have any answers for you other than it appears to be some sort of strange "installation/dbus bug". 

When kubuntu was installed it may have handled your drives incorrectly, and that is why it does not work correctly with dbus, or it could be a dbus only problem.

If I think of anything, I will post here and message you to let you know to look here for the answer, but as of right now, I'm at a loss.

Sorry for the late reply,

---

### Post by jrickard on 2007-05-30
Same problem with a Fiesty 7.04 64-bit installation and a Plextor DVD drive.  Insert data DVD and am informed that it is blank - demonstrably not.

This seems to be a VERY old bug that just hasn't been fixed.

Jack Rickard

---

### Post by carlbastos on 2007-05-30
I can't understand a word of those launchpads/bugs pages...

---

