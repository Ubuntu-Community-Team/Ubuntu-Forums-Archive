---
title: "Mounting problems"
date: 2014-03-06
forum: General Help
---

### Post by gerard3 on 2014-03-06
After I upgraded my Ubuntu kernel from 9.10 (yes, very old) to 10.04, my computer wasn't able to boot anymore, due to this error:
kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0)

I found this thread: [http://ubuntuforums.org/showthread.php?t=1751574](http://ubuntuforums.org/showthread.php?t=1751574)

And I was so dumb to execute the following:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
While I didn't boot from CD. So now my computer doesn't boot at all, it will prompt grub rescue.

How can I undo above mounting?

Thanks,

Gerard

---

### Post by Bashing-om on 2014-03-06
gerard3; Hi ! Wecome to the forum.

That command sequence is applicable to a separate '/boot' partition as installed to device partition 1 of the 1st hard drive. MOst likely NOT what your configuration is. EDIT, here: The commands are valid to install grub to the MBR.

I can not say that there is now no damage to the file system that is on sda1.( maybe the command failed and did nothing to the file system ?) However, we can look and try and salvage this situation.

Are you still running release 10.04 - as a desk top edition - ?? No longer supported and now may be a good time to upgrade to a current release ?

For now to attempt to repair this install:
Boot the liveCD to "try ubuntu" mode -> terminal, and post back to us the output of terminal command:
```

sudo fdisk -lu

```
to show the present configuration of the hard drive.
We can then advise the correct command sequence to install grub properly.

[INDENT][INDENT]it is all 
[INDENT][INDENT][INDENT]a process of learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gerard3 on 2014-03-06
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11db7f45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   613072529   306536233+  83  Linux
/dev/sda2       613072530   625137344     6032407+   5  Extended
/dev/sda5       613072593   625137344     6032376   82  Linux swap / Solaris
ubuntu@ubuntu:~$
```

---

### Post by Bashing-om on 2014-03-06
gerard3; Well !

I stand corrected, your command sequence to install grub to the Master Boot Record of the 1st hard drive (sda) is correct ! A good thing !
My bad !

[color=red]So from the liveCD[/color] -> terminal;
terminal commands:
```

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```
reboot into the installed system:
```

sudo shutdown -r now

```

and from the install; terminal code:
```

sudo update-grub

```

I expect all is better now, gooder if/when you upgrade to a current release.

Again, I regret my error in jumping to a wrong conclusion.

[INDENT][INDENT]it's ubuntu
[INDENT][INDENT][INDENT]it's fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gerard3 on 2014-03-06
Hi,

Thanks for your quick response again!

I executed the following commands:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
And rebooted. 
It won't start grub rescue anymore, the state is exactely the same as it was after I did the upgrade from 9.10 to 10.04. So this problem is solved, thanks! (I don't understand why, the commands where exactely the same as the ones who broke it?)

So now we have the same problem again which I had right after the upgrade.
When I boot, GNU GRUB asks me which recovery version to boot.
When I pick the one on the top (Ubuntu, Linux 2.6.32-56-generic) I got the error I mentioned before:
[I][COLOR=#000000]kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0)
[/COLOR][/I]
The second one is the same, but recovery mode, when I pick the 3rd (2.6.31-23-generic) it gives several errors, but it boots, but in non-graphical modus. It starts all services (apache, mysql...) and I am even able to acces it via my browser but not via SSH somehow.
I was not able to type [COLOR=#000000][FONT=Ubuntu Mono]sudo update-grub[/FONT][/COLOR] because in this mode I cannot type. I just see it boot all services..

Any clue?

Gerard

---

### Post by Bashing-om on 2014-03-06
gerard3l Hey !

This is a server install ? .. Then yeah !
IF this is a server we are working on:
go to the rescue mode and run these commands
```

mount -o remount rw /
sudo apt-get update
sudo apt-get upgrade

```
IF there are errors reported, post them back for our inspection.
Reboot, and see if now you can boot into the "normal" kernel.

Else: we can try and purge grub and (re-)install grub.

[INDENT][INDENT]we be cooking with Crisco now
[/INDENT][/INDENT]

---

### Post by gerard3 on 2014-03-07
I'm not sure whether it is a server or desktop installation. I use it as a server, but not sure which installation it is (it's dated from 2009, too long ago).

Should I run above commands though?
P.S. I can only run commands using the LiveCD and open the terminal.

---

### Post by Bashing-om on 2014-03-07
gerard3; Welp.

As to attempting to update your system,

Boot the install to that "recovery" console to a terminal, and from there run the commands.

Post back here the errors that are generated, will see what can be done.

I think, from my perspective, you would be better served with a current Long Term Support release 12.04. The quick thing is to backup your data, and clean install the server edition.
The big thing is saving your "personal data" and the config files for the services you are running. I do enjoy solving a puzzle, and this is still a puzzl'n thing. But, that is your call as to what you want to do.

we can
[INDENT][INDENT]do this
[/INDENT][/INDENT]

---

### Post by gerard3 on 2014-03-08
I agree it is better to upgrade to the latest LTS version, that's why I started this kernel upgrade anyway. But you have to upgrade from version to version.. I also like puzzles, so let's see where we can come. If it takes too long, I try to save my data and make a clean install.

When I boot and choose any version from the recovery console I get this message:

[I]Error: no argument specified
Press any key to continue...

[/I]Then the Ubuntu logo is shown, and then it switches to terminal (?) mode, starts several services, ends with "* Checking battery state... [ OK]". A blinking underscore is shown, but I am not able to type.

---

### Post by Bashing-om on 2014-03-08
gerard3; OK,

Logically, as this is an End Of Life upgrade attempt (from 9.04), let's take a look at what we are booting and the sources' control files contents.
By accessing the install from a liveCD and having a looksee.

Boot the liveCD -> try ubuntu -> terminal;
Post back the output of the 'cat' commands and 'blkid' .
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work #because 'sda1' is the location of the '/' directory (fdisk says so)#
cat /mnt/work/etc/fstab
cat /mnt/work/etc/apt/sources.list
cat /mnt/work/etc/apt/sources.list.d/*.list
sudo blkid ##so we can compare fstab's UUIDs

```

When all done poking about, you MUST (UN-)mount the install:
```

sudo umount /mnt/work

```

There is a small thing that bothers me:
your fdisk output:
> 
/dev/sda1   *          63   613072529   306536233+  83  Linux

That '+' at the end of the block count, I do not recall what it denotes - shame on me ! -> may have to attend to that at a later time (??).

Get these ducks lined up, and then we look at the kernel/booting issue.
[INDENT]it is though,
[INDENT][INDENT]one thing at a time
[/INDENT][/INDENT][/INDENT]

---

### Post by gerard3 on 2014-03-08
Okay! Thanks for your time helping me so far!

Here's the output:

ubuntu@ubuntu:~$ sudo mkdir /mnt/work
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/work
ubuntu@ubuntu:~$ cat /mnt/work/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6306bc89-535b-4b1a-b57a-c8bf4b8469bf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a06e711b-5aa6-44cd-970e-cff4e43cc24b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
ubuntu@ubuntu:~$ cat /mnt/work/etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
ubuntu@ubuntu:~$ cat /mnt/work/etc/apt/sources.list.d/*.list
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main # uitgeschakeld bij upgrade naar lucid
# channel for the karmic (9.10) partner channel
# 
#:description:This channel contains the partner software for karmic
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sr0: LABEL="Ubuntu 12.04.4 LTS amd64" TYPE="iso9660" 
/dev/sda1: UUID="6306bc89-535b-4b1a-b57a-c8bf4b8469bf" TYPE="ext4" 
/dev/sda5: UUID="a06e711b-5aa6-44cd-970e-cff4e43cc24b" TYPE="swap" 
ubuntu@ubuntu:~$ sudo umount /mnt/work

---

### Post by Bashing-om on 2014-03-08
gerard3; Hey ,

No fault found, looks good to me.

OK, What are we trying to boot up, a desk top or a server install ?
From the liveDVD (12.04 Hah !) as before mounting the install '/' root partition;
then show us the output of:
```

ls -la /mnt/work/boot
ls -la /mnt/work/usr/src

```
Which will show the kernel situation.

Then -> we see what the booting situation is from grub's perspective.
*************
Whoh !, May have just occurred to me what is going on // Like using version 12.04 grub installing to 10.04 ??? No will workie ! A lot of difference between 10.04 and 12.04 grub (???) tell me it ain't so. 
**************8

[INDENT][INDENT]still, just small steps
[/INDENT][/INDENT]

---

### Post by gerard3 on 2014-03-08
The LiveDVD is version 12.04 indeed. The installation is upgraded (unsuccessfully) to 10.04. I didn't manually upgrade the grub version.

Here's the output again:

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/work
ubuntu@ubuntu:~$ ls -la /mnt/work/boot
total 115308
drwxr-xr-x  3 root root    4096 Mar  4 20:34 .
drwxr-xr-x 22 root root    4096 Mar  8 19:39 ..
-rw-r--r--  1 root root  629174 Oct 16  2009 abi-2.6.31-14-generic
-rw-r--r--  1 root root  629174 Dec  8  2009 abi-2.6.31-16-generic
-rw-r--r--  1 root root  629446 Dec 10  2009 abi-2.6.31-17-generic
-rw-r--r--  1 root root  629446 Jan 28  2010 abi-2.6.31-19-generic
-rw-r--r--  1 root root  629742 Mar 12  2010 abi-2.6.31-20-generic
-rw-r--r--  1 root root  629853 Mar 24  2010 abi-2.6.31-21-generic
-rw-r--r--  1 root root  629853 Feb 11  2011 abi-2.6.31-22-generic
-rw-r--r--  1 root root  629853 Mar 18  2011 abi-2.6.31-23-generic
-rw-r--r--  1 root root  653345 Jan  6 19:47 abi-2.6.32-56-generic
-rw-r--r--  1 root root  111371 Oct 16  2009 config-2.6.31-14-generic
-rw-r--r--  1 root root  111371 Dec  8  2009 config-2.6.31-16-generic
-rw-r--r--  1 root root  111371 Dec 10  2009 config-2.6.31-17-generic
-rw-r--r--  1 root root  111371 Jan 28  2010 config-2.6.31-19-generic
-rw-r--r--  1 root root  111382 Mar 12  2010 config-2.6.31-20-generic
-rw-r--r--  1 root root  111349 Mar 24  2010 config-2.6.31-21-generic
-rw-r--r--  1 root root  111349 Feb 11  2011 config-2.6.31-22-generic
-rw-r--r--  1 root root  111349 Mar 18  2011 config-2.6.31-23-generic
-rw-r--r--  1 root root  116036 Jan  6 19:47 config-2.6.32-56-generic
drwxr-xr-x  3 root root   12288 Mar  6 20:50 grub
-rw-r--r--  1 root root 7648814 Nov 30  2009 initrd.img-2.6.31-14-generic
-rw-r--r--  1 root root 7647638 Dec 31  2009 initrd.img-2.6.31-16-generic
-rw-r--r--  1 root root 7647601 Jan 28  2010 initrd.img-2.6.31-17-generic
-rw-r--r--  1 root root 7647817 Feb  5  2010 initrd.img-2.6.31-19-generic
-rw-r--r--  1 root root 7652207 Mar 19  2010 initrd.img-2.6.31-20-generic
-rw-r--r--  1 root root 7652227 Apr 29  2010 initrd.img-2.6.31-21-generic
-rw-r--r--  1 root root 7654419 Mar  1  2011 initrd.img-2.6.31-22-generic
-rw-r--r--  1 root root 7252602 Mar  4 19:53 initrd.img-2.6.31-23-generic
-rw-r--r--  1 root root  160280 Mar 23  2010 memtest86+.bin
-rw-r--r--  1 root root 1664737 Oct 16  2009 System.map-2.6.31-14-generic
-rw-r--r--  1 root root 1665323 Dec  8  2009 System.map-2.6.31-16-generic
-rw-r--r--  1 root root 1665500 Dec 10  2009 System.map-2.6.31-17-generic
-rw-r--r--  1 root root 1665617 Jan 28  2010 System.map-2.6.31-19-generic
-rw-r--r--  1 root root 1666793 Mar 12  2010 System.map-2.6.31-20-generic
-rw-r--r--  1 root root 1668296 Mar 24  2010 System.map-2.6.31-21-generic
-rw-r--r--  1 root root 1668417 Feb 11  2011 System.map-2.6.31-22-generic
-rw-r--r--  1 root root 1668444 Mar 18  2011 System.map-2.6.31-23-generic
-rw-r--r--  1 root root 1695798 Jan  6 19:47 System.map-2.6.32-56-generic
-rw-r--r--  1 root root    1196 Oct 16  2009 vmcoreinfo-2.6.31-14-generic
-rw-r--r--  1 root root    1196 Dec  8  2009 vmcoreinfo-2.6.31-16-generic
-rw-r--r--  1 root root    1196 Dec 10  2009 vmcoreinfo-2.6.31-17-generic
-rw-r--r--  1 root root    1196 Jan 28  2010 vmcoreinfo-2.6.31-19-generic
-rw-r--r--  1 root root    1196 Mar 12  2010 vmcoreinfo-2.6.31-20-generic
-rw-r--r--  1 root root    1196 Mar 24  2010 vmcoreinfo-2.6.31-21-generic
-rw-r--r--  1 root root    1196 Feb 11  2011 vmcoreinfo-2.6.31-22-generic
-rw-r--r--  1 root root    1196 Mar 18  2011 vmcoreinfo-2.6.31-23-generic
-rw-r--r--  1 root root    1196 Jan  6 19:47 vmcoreinfo-2.6.32-56-generic
-rw-r--r--  1 root root 3890400 Oct 16  2009 vmlinuz-2.6.31-14-generic
-rw-r--r--  1 root root 3892032 Dec  8  2009 vmlinuz-2.6.31-16-generic
-rw-r--r--  1 root root 3890560 Dec 10  2009 vmlinuz-2.6.31-17-generic
-rw-r--r--  1 root root 3891264 Jan 28  2010 vmlinuz-2.6.31-19-generic
-rw-r--r--  1 root root 3898528 Mar 12  2010 vmlinuz-2.6.31-20-generic
-rw-r--r--  1 root root 3901472 Mar 24  2010 vmlinuz-2.6.31-21-generic
-rw-r--r--  1 root root 3902368 Feb 11  2011 vmlinuz-2.6.31-22-generic
-rw-r--r--  1 root root 3903360 Mar 18  2011 vmlinuz-2.6.31-23-generic
-rw-r--r--  1 root root 4055424 Jan  6 19:47 vmlinuz-2.6.32-56-generic
ubuntu@ubuntu:~$ ls -la /mnt/work/usr/src
total 72
drwxrwsr-x 18 root src  4096 Mar  4 20:41 .
drwxr-xr-x 10 root root 4096 Oct 28  2009 ..
drwxr-xr-x 23 root root 4096 Dec 31  2009 linux-headers-2.6.31-16
drwxr-xr-x  7 root root 4096 Dec 31  2009 linux-headers-2.6.31-16-generic
drwxr-xr-x 23 root root 4096 Jan  6  2010 linux-headers-2.6.31-17
drwxr-xr-x  7 root root 4096 Jan  6  2010 linux-headers-2.6.31-17-generic
drwxr-xr-x 23 root root 4096 Feb  5  2010 linux-headers-2.6.31-19
drwxr-xr-x  7 root root 4096 Feb  5  2010 linux-headers-2.6.31-19-generic
drwxr-xr-x 23 root root 4096 Mar 19  2010 linux-headers-2.6.31-20
drwxr-xr-x  7 root root 4096 Mar 19  2010 linux-headers-2.6.31-20-generic
drwxr-xr-x 23 root root 4096 Apr 29  2010 linux-headers-2.6.31-21
drwxr-xr-x  7 root root 4096 Apr 29  2010 linux-headers-2.6.31-21-generic
drwxr-xr-x 23 root root 4096 Feb 24  2011 linux-headers-2.6.31-22
drwxr-xr-x  7 root root 4096 Feb 24  2011 linux-headers-2.6.31-22-generic
drwxr-xr-x 23 root root 4096 May  7  2011 linux-headers-2.6.31-23
drwxr-xr-x  7 root root 4096 May  7  2011 linux-headers-2.6.31-23-generic
drwxr-xr-x 24 root root 4096 Mar  4 20:41 linux-headers-2.6.32-56
drwxr-xr-x  7 root root 4096 Mar  4 20:41 linux-headers-2.6.32-56-generic
ubuntu@ubuntu:~$ sudo umount /mnt/work

---

### Post by Bashing-om on 2014-03-08
gerard3; Yup, then

We did from 12.04 liveDVD
> 
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda


Which uses the files on the liveDVD 12.04 to install on the 10.04 install... uhh ohh !
So what we NEED to do now is download and burn a 10.04 liveCD, and from that (re-)install grub to the install.
Available here:
[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)
Then (RE-)RE-install grub from the 10.04 liveCD

Then if we get it booting, lets clean up /boot in the install - bet part of the problem is '/boot' is full and there is "no space left on device" errors (??) Way too many old kernels in residence, And this is by the way a desk top install, as the images and headers are not "linux-image-server".
-in 12.04 and above the same kernel is used -!!

Then let us see if we can perform a LTS to LTS upgrade 10.04 to 12.04, Get away from the No Longer Supported desktop version 10.04.

That now
[INDENT][INDENT]is my thoughts on the matter
[/INDENT][/INDENT]

---

### Post by gerard3 on 2014-03-10
Hi Bashing-om,

Ok, I wasn't aware we were using some code from LiveDVD (which wasn't compatible).
I use LiveDVD version 10.04 and executed:
[COLOR=#000000][I]
sudo mount /dev/sda1 /mnt[/I][/COLOR]
[COLOR=#000000][I]sudo grub-install --root-directory=/mnt /dev/sda

[/I][/COLOR]First command wasn't neccessary I think. I rebooted and got the error again:
[COLOR=#000000]kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0)
[/COLOR]
After rebooting again, I came to the recovery menu again. First option gives above error also, a later version brings me to the screen with Ubuntu logo, and switches to 'terminal mode' again, like before. First giving some mounting related errors btw (it scrolls so I wasn't able to write them down).

So actually: nothing changed.

---

### Post by Bashing-om on 2014-03-10
gerard3; Huh ??
> 
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

First command wasn't neccessary I think. I rebooted and got the error again:sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda


Are you booting from the liveCD ? as I assure you that from that liveCD that 1st command - or similar - is mandatory to even have access to the installed system partition.
Then one must also UN - Mount that partition prior to shutting the system down - else file system corruption - at some level will result.

So now do we have a corrupted file system to cope with ? Might be good insurance at this point to run the file system check/repair routine and just see what results:

from the liveCD (10.04 !) with nothing else mounted ( can not operate on a mounted file system):
#From liveCD so everything is unmounted,swap off if necessary, WHERE sda1 is the installed's "root [/]" partition.
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo fdisk -lu ## make sure that sda1 is still sda1 and that is the partition to be worked over.
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

```

Then we will attempt to (re-)install grub once more from the liveCD, see what results, if problems still will use terminal commands to attempt to see why grub is being so contrary.

[INDENT][INDENT]what does it take 
[INDENT][INDENT]just to boot 
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gerard3 on 2014-03-11
Ok, I'm feeling a little bit like a noob now... :)

Fortunately the file system is not corrupted:
```
ubuntu@ubuntu:/$ sudo e2fsck -C0 -p -f -v /dev/sda1
                                                                               
  410709 inodes used (2.14%)
     351 non-contiguous files (0.1%)
     466 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 374576/245
10012307 blocks used (13.07%)
       0 bad blocks
       2 large files

  311989 regular files
   54785 directories
      68 character device files
      26 block device files
       2 fifos
     593 links
   43829 symbolic links (35781 fast symbolic links)
       1 socket
--------
  411293 files
ubuntu@ubuntu:/$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  410709 inodes used (2.14%)
     351 non-contiguous files (0.1%)
     466 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 374576/245
10012307 blocks used (13.07%)
       0 bad blocks
       2 large files

  311989 regular files
   54785 directories
      68 character device files
      26 block device files
       2 fifos
     593 links
   43829 symbolic links (35781 fast symbolic links)
       1 socket
--------
  411293 files
ubuntu@ubuntu:/$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:/$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:/$ sudo umount /mnt
```

I will reboot now to see what's happening.

---

### Post by gerard3 on 2014-03-11
The Recovery menu is prompted again, the first version is again showing the error:
[COLOR=#000000]kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0)

[/COLOR]Im not able to do anything (even CTRL+ALT+DEL doesn't work).

Of course I checked if sda1 was the right disk, and it was.

---

### Post by gerard3 on 2014-03-11
I was able to see some errors if I select an older version from the recovery menu:
mount: mounting none on /dev failed: No such device
chroot: cannot execute /etc/apparmor/initramfs: No such file or directory

---

### Post by Bashing-om on 2014-03-11
gerard3; OK !

Different approach.

Can you now boot through the recovery console, and do you have a working internet connection ?

We going to back up
[INDENT][INDENT]and punt 
[/INDENT][/INDENT]

---

### Post by gerard3 on 2014-03-11
Yes I can boot through recovery console (using the second version available). Now I CAN connect with putty via SSH to the machine! Samba shares are still not working.
I have a working internet connection on that machine (wget [http://google.com](http://google.com) works)!

I'm ready when you're ready!

---

### Post by Bashing-om on 2014-03-11
gerard3; OK !

Let's purge and (RE-)install grub from the repository.
Boot to the recovery console -> root  AND enable networking ; option "with network access" (??);
terminal command to get r/w access:
```

mount -o remount rw /

```

in terminal remove all grub, then reinstall grub2 and recreate the config files:
```

fdisk -lu ## to make sure no assignments have changed and we still working on drive sda !
apt-get remove --purge grub grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sda
update-grub ##once more just to make sure !

``` ( you have a root console so the use of "sudo" is not required)

Remember to exit out of "root" .

Reboot and tell me ya boot up just fine now !

[INDENT][INDENT]more than one path to an end
[/INDENT][/INDENT]

---

### Post by gerard3 on 2014-03-11
Hi Bashing-om,

Before I will execute this;

When I boot I see something like this:
[http://1.bp.blogspot.com/-iQCTxZYkYAo/TYzLHrRwfcI/AAAAAAAAO_4/op1EpcovM5U/s1600/resetpasswordlucid01.png](http://1.bp.blogspot.com/-iQCTxZYkYAo/TYzLHrRwfcI/AAAAAAAAO_4/op1EpcovM5U/s1600/resetpasswordlucid01.png)

When I select an option with recovery mode I go to the Recovery Menu, but my keyboard (nor mouse) respond.

When I select a version (not being the newest) without recovery mode, the system boots in a non-graphical environment, but as I mentioned before, I can't type there. I just see some services booting.

So, I can only use terminal with LiveCD, or via Putty / SSH.

Gerard


EDIT: When I use one older version, I CAN use keyword. I'll execute above commands.

---

### Post by gerard3 on 2014-03-11
I just mentioned that I didn't tell you about te cause of the problem.
As I said was upgrading (via update manager) from 9.10 to 10.4. When it runs for a very long time, the system asked me about replacing a configuration or not. Then I mentioned that the system was frozen; both keyboard and mouse didn't respond. So the only thing I could do is rebooting the system. Causing this actual problem. So I just thought about the possibility that maybe the upgrade wasn't even finished?

Gerard

---

### Post by gerard3 on 2014-03-11
When I execute
```
[COLOR=#000000][FONT=Ubuntu Mono]apt-get remove --purge grub grub-pc grub-common[/FONT][/COLOR]
```

I got an error: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure ,a' to correct the problem.

What should I do?

---

### Post by Bashing-om on 2014-03-11
gerard3; Lemme play catch up on the link you provided,

For now , my memory of 10.04 is very hazy, But in the installed grub boot menu there is a kernel item marked "recovery".
What results when you choose that option ?

Do not know how far in the upgrade process it is when ask'd about the config change - it may well be significant -.
The easier course to pursue is within the install to repair anything; Where we are now in an attempt to boot the install.
Else, what we can do is a change root routine from the liveCD into the install environment. It is not that big of a deal and we may be forced to that route.

From the chroot environment we can run some commands to check the integrity of the installed system.
-----------------------------
> 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure ,a' to correct the problem.

looks like we will do the change root routine.

I will be back most ricky tic.

[INDENT][INDENT]keeps getting deeper
[INDENT][INDENT][INDENT]alla the time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-03-11
gerard3; ump ,

Not looking good for the home team !

> 
EDIT: When I use one older version, I CAN use keyword. I'll execute above commands.


OK, from the kernel you can activate to a CLI, what results from terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```

So we have an idea of where we stand and as well the condition of the package manager.

[INDENT]a puzzle indeed
[/INDENT]

---

### Post by gerard3 on 2014-03-12
Hi Bashing-om,

Ok, so I used the terminal from recovery mode > with network acces. That is what you meant, right?

Both commands (apt-get update and apt-get upgrade) result in the exact same error:
```

[COLOR=#000000]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.[/COLOR]
```

---

### Post by Bashing-om on 2014-03-12
gerard3;
Yeah, should work,

Un- good that result ! : Let's see if we can fix the packages.
Same same to the recovery console with network access, terminal commands:
```

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get update
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update ##again##
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Fingers and toes are crossed ->
[INDENT][INDENT]let's see what happens
[/INDENT][/INDENT]

---

### Post by gerard3 on 2014-03-12
WOW
You just saved my DEV machine!!!!!!!!!!!

When I ran the first command, I received a LOT of packages. 
After executing all the other commands and rebooted the system, I was so happy to see my login screen again and was able to login! Everything seems to work fine!!! APACHE / PHP, MYSQL, SAMBA, SVN... 

Wow, many thanks mate! And sorry for my poor English some times.. :)

THANKS AGAIN, for your expertise and also for your time!

---

### Post by Bashing-om on 2014-03-12
gerard3; Outstanding !

It is what is called ->
Panic not. Just proceed in a calm and orderly fashion.

keep poking and prodding 'till something gives. Once we had an interface and the real problem identified, piece of cake !

You are quite welcome to my help, just pass it on !

[INDENT]ubuntu
[INDENT][INDENT]1 for all and all for one
[/INDENT][/INDENT][/INDENT]

---

