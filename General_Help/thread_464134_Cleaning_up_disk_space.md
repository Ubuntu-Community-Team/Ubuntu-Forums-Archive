---
title: "Cleaning up disk space"
date: 2007-06-04
forum: General Help
---

### Post by Temujin_12 on 2007-06-04
I recently installed Ubuntu using the [Wubi installer]("http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html").  At the time, there was a bug that wouldn't let you create disk images greater than 4GB.  Not a problem as I mostly just wanted to test it out and do some lightweight development on it and was happy just to get Linux onto my laptop.  Well, after installing libraries and some basic editors (not even eclipse) I only have ~300MB left.  It still runs great, but the space remaining is steadily declining.

My question is where are the places I should go to to free disk space?  I noticed that /var/cache/apt has over 400MB in it.  Is it safe to remove its contents?  Where else should I look?

Thanks.

---

### Post by jimbob on 2007-06-04
Wouldn't recommend fooling around with /var/cache/apt.

How many disks do you have?  Could your Ubuntu partition be expanded?

Post the output of[COLOR="RoyalBlue"] fdisk -l[/COLOR]
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Temujin_12 on 2007-06-04
Output of 'fdisk -l':
```
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4863    39062016    7  HPFS/NTFS
```

This appears to be the NTFS disk that my Wubi disk images reside on.

Output of 'df':
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/loop7             4031676   3474500    352380  91% /
varrun                  224964       240    224724   1% /var/run
varlock                 224964         0    224964   0% /var/lock
procbususb              224964        72    224892   1% /proc/bus/usb
udev                    224964        72    224892   1% /dev
devshm                  224964         0    224964   0% /dev/shm
lrm                     224964     33788    191176  16% /lib/modules/2.6.20-16-generic/volatile
/dev/loop6             1007892    138992    817704  15% /home

```

'/dev/loop7' is the disk image that is running out of space.  I have more space on '/dev/loop6' but I'd like to avoid moving system files over there.

One option I've thought of, but not yet researched, is if there is a way to resize these disk images.  Note that these aren't normal partitions but virtual disks created by the [Wubi installer]("http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/faq.html#internals").

EDIT: Hmm... I just ran across [lvpm]("https://launchpad.net/lvpm") which looks like it is made to modify these disk images.  Anyways, I'd still like to know where to go to free disk space in general.

---

### Post by jimbob on 2007-06-04
Well, you have completely lost me here because I have zero experience with the Wubi installer.

If it was me I would shrink my Windows partition and install Ubuntu in the conventional way on the remaining unallocated disk space in a dual-boot configuration.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by pak33m on 2007-06-04
In my experience with Wubi I have noticed and it has been announced that the program is buggy.  It is a great solution and I have recommended it to Windows user who wan to try Ubuntu.

However, I would suggest that you try [http://www.virtualbox.org](http://www.virtualbox.org) and put together your own Ubuntu image.  This is if you are into virtuals.  I have found this to be the best alternative to virtuals for me and is not as memory intensive as the rest! And it runs very well on my laptop. Oh, and Virtualbox is for Windows and Linux users.

If you are trying to remove unused packages try here (from [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-remove):](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-remove):)

3.6 Removing unused package files: apt-get clean and autoclean

When you install a package APT retrieves the needed files from the hosts listed in /etc/apt/sources.list, stores them in a local repository (/var/cache/apt/archives/), and then proceeds with installation, see Installing packages, Section 3.2. 

In time the local repository can grow and occupy a lot of disk space. Fortunately, APT provides tools for managing its local repository: apt-get's clean and autoclean methods. 

apt-get clean removes everything except lock files from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. Thus, if you need to reinstall a package APT should retrieve it again. 

apt-get autoclean removes only package files that can no longer be downloaded. 

The following example show how apt-get autoclean works: 
     # ls /var/cache/apt/archives/logrotate* /var/cache/apt/archives/gpm*
     logrotate_3.5.9-7_i386.deb
     logrotate_3.5.9-8_i386.deb
     gpm_1.19.6-11_i386.deb

In /var/cache/apt/archives there are two files for the package logrotate and one for the package gpm. 
     # apt-show-versions -p logrotate
     logrotate/stable uptodate 3.5.9-8
     # apt-show-versions -p gpm
     gpm/stable upgradeable from 1.19.6-11 to 1.19.6-12

apt-show-versions shows that logrotate_3.5.9-8_i386.deb provides the up to date version of logrotate, so logrotate_3.5.9-7_i386.deb is useless. Also gpm_1.19.6-11_i386.deb is useless because a more recent version of the package can be retrieved. 
     # apt-get autoclean
     Reading Package Lists... Done
     Building Dependency Tree... Done
     Del gpm 1.19.6-11 [145kB]
     Del logrotate 3.5.9-7 [26.5kB]

Finally, apt-get autoclean removes only the old files. See How to upgrade packages from specific versions of Debian, Section 3.9 for more information on apt-show-versions.

---

### Post by Temujin_12 on 2007-06-04
> apt-get clean removes everything except lock files from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. Thus, if you need to reinstall a package APT should retrieve it again.

That did the trick.  There are now only 20MB in /var/cache/apt/ and df gives the following:
```
/dev/loop7             4031676   3072300    754580  81% /
varrun                  224964       240    224724   1% /var/run
varlock                 224964         0    224964   0% /var/lock
procbususb              224964        72    224892   1% /proc/bus/usb
udev                    224964        72    224892   1% /dev
devshm                  224964         0    224964   0% /dev/shm
lrm                     224964     33788    191176  16% /lib/modules/2.6.20-16-generic/volatile
/dev/loop6             1007892    139116    817580  15% /home

```

So /dev/loop7 went from 91% used (352MB free) to 81% used (754 free).

> However, I would suggest that you try [http://www.virtualbox.org](http://www.virtualbox.org) and put together your own Ubuntu image. This is if you are into virtuals. I have found this to be the best alternative to virtuals for me and is not as memory intensive as the rest! And it runs very well on my laptop. Oh, and Virtualbox is for Windows and Linux users.

I'll give that a try someday.  I mainly wanted to try out Wubi as my laptop has little RAM and I wanted a fairly performant installation w/o having to mess with partitions and/or reinstalling Windows.

---

