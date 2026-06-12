---
title: "[SOLVED] only root can burn CD in Hardy!"
date: 2008-06-26
forum: General Help
---

### Post by quixote on 2008-06-26
If I try to burn a CD as an ordinary user, it tells me I don't have the right permissions.  This happens whether I use Brasero, K3b (my favorite), or anything else I've tried.  If I start K3b as root, I get security warnings ... :rolleyes:

My CD drive is mounted on /dev/hdc,  which lists the following:

brw-rw----+       root   cdrom

When I check in groups, though, there is no group "cdrom" so it's not too surprising that quixote-user is not a member of it!

I assume the solution is not as simple as adding group "cdrom" and making myself a member of it?  That would be too easy.

How can I get this sorted out so I don't have to burn all my CDs as root?

---

### Post by p_quarles on 2008-06-26
Are you positive no cdrom group exists? Run this to make certain:
```
cat /etc/group | grep cdrom
```
If it exists, you would simply run this to fix the problem:
```
sudo adduser $(whoami) cdrom
```
If not, run this to find out the appropriate group user for your CD drive:
```
ls -l /dev | grep cd
```

---

### Post by mc4man on 2008-06-26
If your on hardy and your cd drive is 'showing' /dev/hdc that might be something you want to address.
run ```
sudo lshw -C disk
``` and it may be interesting to see the contents of the 70-persistent-cd rules in  /etc/udev/rules.d

edit: if you see your drive listed twice in ......rules then read here
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)

---

### Post by quixote on 2008-06-27
Very interesting.  group "cdrom" doesn't show up via the GUI, but it's there if I run cat /etc/group.  And, apparently I am a member:

```
cdrom:x:24:quixote
```

What kind of sense does that make?

This is the output of the other commands:

```
$ ls -l /dev | grep cd
lrwxrwxrwx  1 root   root           3 2008-06-26 20:18 cdrom -> hdc
lrwxrwxrwx  1 root   root           3 2008-06-26 20:18 cdrw -> hdc
brw-rw----+ 1 root   cdrom    22,   0 2008-06-26 13:18 hdc
crw-rw-rw-  1 root   tty       2, 221 2008-06-26 13:18 ptycd
crw-rw-rw-  1 root   tty       3, 221 2008-06-26 13:18 ttycd
```
Should be okay, right?

```
$sudo lshw -C disk  
      *-cdrom
       description: DVD reader
       product: UJDA765 DVD/CDRW
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: 1.00
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
       configuration: mode=udma2 status=nodisc
```
that's just the cd entry.  Otherwise there's the main HD (/hda) and pcmcia HD (/sda).  No duplication, it seems.

The output of /etc/udev/rules.d/70-persistent-cd.rules:
```
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0e.0-ide-1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0e.0-ide-1:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0e.0-ide-1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
```

Looking at links in /dev shows that cdrom, cdrw, and dvd all point to "hdc", but that's it.  There's no cdrw1, cdrom1, for instance.

Am I missing something?  Or is this just weird?

---

### Post by p_quarles on 2008-06-27
Hmm. This is a bit strange. My first thought was that this is something to do with dbus or hal, but (I think) that would create the same issues running as root or as an unprivileged user. 

Could you post the entire output of this ?:
```
groups
```

---

### Post by quixote on 2008-06-28
output of groups:
```
$ groups
quixote adm dialout fax cdrom floppy tape audio dip video plugdev scanner fuse lpadmin admin
```

I noticed another interesting thing in the meantime.  Both nautilus and krusader list both /media/cdrom and /media/cdrom0.

So, even though there are no duplicate entries in the code I posted a bit earlier, that Hardy bug mc4man was talking about is lurking *somewhere*.

Where might the GUI file managers be getting that incorrect cdrom info from? That might also be the source of my problem.

---

### Post by p_quarles on 2008-06-28
> **quixote said:**
> output of groups:
```
$ groups
quixote adm dialout fax cdrom floppy tape audio dip video plugdev scanner fuse lpadmin admin
```

I noticed another interesting thing in the meantime.  Both nautilus and krusader list both /media/cdrom and /media/cdrom0.

So, even though there are no duplicate entries in the code I posted a bit earlier, that Hardy bug mc4man was talking about is lurking *somewhere*.

Where might the GUI file managers be getting that incorrect cdrom info from? That might also be the source of my problem.
I doubt that's the same issue. You didn't say exactly *where* the file managers are listing these two instances of the drive: if this is while you're displaying the /media directory, that's expected. If it's while displaying attached storage devices, you may be on to something here.

If you look closely, you'll see that /media/cdrom is a symbolic link to /media/cdrom0.

---

### Post by mc4man on 2008-06-28
> that Hardy bug It's not the same thing. 
I still think it's interesting that at this point (running 8.04) your drive is on ide instead of scsi bus. (maybe some hardware will continue to be setup in that manner or in case of upgrades the issue's been resolved by not creating a new entry)

---

### Post by quixote on 2008-06-28
Yes, the cdrom cdrom0 are listed under /media.  And yes, you're right, "cdrom" is a link to cdrom0.  So that's not it.

Harrumph.

Does this mean we're out of ideas?  :(

---

### Post by p_quarles on 2008-06-28
Well, I am certainly running out of ideas, but I'd give it some time if I were you -- other people may have encountered and fixed this.

In any case, one thing to try would burning a cd from the command line. This may either A) work just fine; or B) give us some useful error messages. For a CD image called ubuntu-desktop.iso (e.g.), you would need to enter this command:
```
wodim -v speed=4 dev=/dev/hdc /path/to/ubuntu-desktop.iso
```
The "-v" argument adds verbosity incrementally. In other words, if you add another v to that, it will give you more output. So, if the command fails and doesn't give you much of a reason why, try adding another v to that command.

---

### Post by VMC on 2008-06-28
> **mc4man said:**
> I still think it's interesting that at this point (running 8.04) your drive is on ide instead of scsi bus. (maybe some hardware will continue to be setup in that manner or in case of upgrades the issue's been resolved by not creating a new entry)

I think this is the key to the whole thing. How did it get assigned IDE instead of SCSI.

For comparisions, here's my output of "sudo lshw -C disk":
> *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM GSA-H22N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.01
       serial: [HL-DT-STDVD-RAM GSA-H22N1.0106/09/21
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open

I wonder how this was installed. You didn't install the DVD Drive after installation, correct? I would be grasping at straws here, but output this so we can get better picture of your machine:

```
sudo lshw -short
```

---

### Post by mc4man on 2008-06-28
I'm sorta guessing 8.04 was an update - the hdd is hdx also. The pcmcia hdd is on scsi. 
While it may not have any benefit, because there is no peril involved I'd try deleting the entry in ......cd.rules and rebooting. Just leave the file exactly like this (delete everything_ below_ these lines)
```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
```
You've never posted your fstab and atm it's somewhat irrelevant, though wouldn't hurt to see it

---

### Post by quixote on 2008-06-28
My Hardy was actually a clean install, not an upgrade.  I have a rather old (2005) Sharp MP30 laptop, and the ATI Radeon 7500 graphics card refused to work under Gutsy.  So I stayed with Feisty, found an xorg.conf tweak that enabled me to run Hardy, and just did a clean install.  I did that before the official release, once it was in beta (I was feeling impatient ;) ), and then applied upgrades as they came out.  The CD drive (actually a CDRW-DVDreadonly drive) is an integral part of the machine, and, no, I've never done any special installing or tweaking on it.  Now that you mention it, it *is* rather bizarre for a CD drive to be considered ide.

I will try the command line cd burn soonest.  Thanks for the giving me the command!

Output of sudo lshw -short:
```
H/W path          Device     Class          Description
=======================================================
                             system         PC-MP Series
/0                           bus            PC-MP Series
/0/0                         memory         101KiB BIOS
/0/4                         processor      Transmeta Efficeon(tm) Processor TM8000
/0/4/7                       memory         192KiB L1 cache
/0/4/8                       memory         1MiB L2 cache
/0/16                        memory         1GiB System Memory
/0/16/0                      memory         1GiB DIMM DDR Synchronous
/0/100                       bridge         TM8000 Northbridge
/0/100/1                     bridge         TM8000 AGP bridge
/0/100/1/0                   display        Radeon Mobility M7 LW [Radeon Mobility 7500]
/0/100/2                     bridge         M5249 HTT to PCI Bridge
/0/100/3                     bridge         M1563 HyperTransport South Bridge
/0/100/3.1                   bridge         M7101 Power Management Controller [PMU]
/0/100/4                     multimedia     M5455 PCI AC-Link Controller Audio Device
/0/100/4.1                   communication  M5457 AC'97 Modem Controller
/0/100/6          wifi0      network        AR5212/AR5213 Multiprotocol MAC/baseband processor
/0/100/9                     bridge         RL5c475
/0/100/9/0                   storage        SEAGATE
/0/100/a          eth0       network        RTL-8139/8139C/8139C+
/0/100/e                     storage        M5229 IDE
/0/100/e/0        ide0       bus            IDE Channel 0
/0/100/e/0/0      /dev/hda   disk           40GB FUJITSU MHT2040AT SP
/0/100/e/0/0/1    /dev/hda1  volume         7593MiB Windows FAT volume
/0/100/e/0/0/3    /dev/hda3  volume         27GiB Extended partition
/0/100/e/0/0/3/5  /dev/hda5  volume         101MiB Linux filesystem partition
/0/100/e/0/0/3/6  /dev/hda6  volume         1961MiB Linux swap / Solaris partition
/0/100/e/0/0/3/7  /dev/hda7  volume         11GiB W95 FAT32 partition
/0/100/e/0/0/3/8  /dev/hda8  volume         6196MiB Linux filesystem partition
/0/100/e/0/0/3/9  /dev/hda9  volume         8620MiB Linux filesystem partition
/0/100/e/0/0/4    /dev/hda4  volume         2196MiB Windows FAT volume
/0/100/e/1        ide1       bus            IDE Channel 1
/0/100/e/1/0      /dev/hdc   disk           UJDA765 DVD/CDRW
/0/100/f                     bus            USB 1.1 Controller
/0/100/f.3                   bus            USB 2.0 Controller
/0/1              scsi0      storage        
/0/1/0.0.0        /dev/sda   disk           8GB ST68022CF
/0/1/0.0.0/0      /dev/sda   disk           8GB 
/0/1/0.0.0/0/1    /dev/sda1  volume         7624MiB Windows FAT volume
/1                           power          Lithium Ion Battery

```

My fstab: (sorry for the dreadful formatting, I can't seem to get it looking better)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                      0  0  
# /dev/hda8 hardy heron root
UUID=16733f5d-d9b3-47c8-90e3-16c5b7abc746  /    ext3      relatime,errors=remount-ro    0  1  
# /dev/hda9  home partition
UUID=2059e7d0-c925-4936-ba43-43bf3affaafe  /home            ext3         relatime                      0  2  
# /dev/hda7  vfat data partition
UUID=428A-9544                             /mnt/datamm    vfat           utf8,auto,users,exec,umask=0000 0  0  
# /dev/hda1  windows partition
UUID=D0D9-52FD                             /media/hda1      vfat         noauto,utf8,users,exec         0  0  
# /dev/hda4  "pqservice" partition
UUID=3D40-315D                             /media/hda4      vfat         noauto,utf8,umask=007,gid=46  0  0  
# /dev/hda5 "dvd" partition
UUID=8d777a38-681d-4d1a-bdc3-f35a8be4f87e  /media/hda8      reiserfs     noauto,defaults               0  0  
# /dev/sda1  8GB pcmcia hard drive
UUID=053C-18E6                             /mnt/8GB-pcmcia  vfat     noauto,users,utf8,exec,umask=0000  0  0  
# /dev/hda6
UUID=55d54e4e-2583-473a-beb8-0b4f0218b9a2  none             swap         sw                            0  0  
#original entry for cdrom, which nobody can use...
#/dev/hdc                                   /media/cdrom0    udf,iso9660  users,noauto,exec,utf8         0  0  
#entry for HP 500GB drive :
hpmediavault:/shares/Volume1/miafiles      /mnt/mediavault  nfs          noauto,users        0  0  
#cdrom
/dev/cdrom				/media/cdrom	iso9660		noauto,users		0  0

```

I see now that in a previous struggle with this issue (when even root couldn't burn CDs) I found a workaround somewhere that involved commenting out /dev/hdc. . . .  But /dev/cdrom is mounted on /media/cdrom, which is a link to /media/cdrom0, which points to /dev/hdc . . .  .  It's making me feel cross-eyed.

I'm afraid I don't know what "atm" is. What's the command I should run?

Thanks much to everyone for all your time on this!

---

### Post by mempman on 2008-06-29
> **quixote said:**
> 


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                      0  0  
# /dev/hda8 hardy heron root
UUID=16733f5d-d9b3-47c8-90e3-16c5b7abc746  /    ext3      relatime,errors=remount-ro    0  1  
# /dev/hda9  home partition
UUID=2059e7d0-c925-4936-ba43-43bf3affaafe  /home            ext3         relatime                      0  2  
# /dev/hda7  vfat data partition
UUID=428A-9544                             /mnt/datamm    vfat           utf8,auto,users,exec,umask=0000 0  0  
# /dev/hda1  windows partition
UUID=D0D9-52FD                             /media/hda1      vfat         noauto,utf8,users,exec         0  0  
# /dev/hda4  "pqservice" partition
UUID=3D40-315D                             /media/hda4      vfat         noauto,utf8,umask=007,gid=46  0  0  
# /dev/hda5 "dvd" partition
UUID=8d777a38-681d-4d1a-bdc3-f35a8be4f87e  /media/hda8      reiserfs     noauto,defaults               0  0  
# /dev/sda1  8GB pcmcia hard drive
UUID=053C-18E6                             /mnt/8GB-pcmcia  vfat     noauto,users,utf8,exec,umask=0000  0  0  
# /dev/hda6
UUID=55d54e4e-2583-473a-beb8-0b4f0218b9a2  none             swap         sw                            0  0  
#original entry for cdrom, which nobody can use...
#/dev/hdc                                   /media/cdrom0    udf,iso9660  users,noauto,exec,utf8         0  0  
#entry for HP 500GB drive :
hpmediavault:/shares/Volume1/miafiles      /mnt/mediavault  nfs          noauto,users        0  0  
#cdrom
/dev/cdrom				/media/cdrom	iso9660		noauto,users		0  0

```



This may sound redundant, but I would try to completely remove from fstab, the file that begins with #/dev/hdc and then give it a shot.

What if you go into computer:/// , and then right click on your cdrom drive and look up its properties...what does it say?

---

### Post by quixote on 2008-06-29
mempman: without a disk in the drive there's no useful info.  With a disk, under the first tab there's info about the disk.  The permissions tab says "permissions could not be determined" and under the volume tab with disk in drive:

mount point:  /media/cdrom0
filesystem:    iso9660
mount options: ro nosuid nodev noexec

I'll try removing the /dev/hdc line completely.  But shouldn't a comment line be invisible to the system??

---

### Post by mempman on 2008-06-29
> **quixote said:**
> mempman: without a disk in the drive there's no useful info.  With a disk, under the first tab there's info about the disk.  The permissions tab says "permissions could not be determined" and under the volume tab with disk in drive:

mount point:  /media/cdrom0
filesystem:    iso9660
mount options: ro nosuid nodev noexec

I'll try removing the /dev/hdc line completely.  But shouldn't a comment line be invisible to the system??


Yes, a commented line should have no effect; however, it may be possible that you got some combo of word-wrap/white spaces that are messing up your fstab.

---

### Post by mc4man on 2008-06-29
> I'm afraid I don't know what "atm" is 'At the moment'
If anything, in fstab I'd try commenting out your bottom line or writing it the same as the hdc line as far as options. (try both, won't hurt)
Your partitioning is a bit of a mess, while that's not to say it's not 'workable' if that was my machine I'd want to clean it up and give Hardy a chance to install in a more 'typical' manner

---

### Post by quixote on 2008-07-02
re "atm": oh, yes, read that wrong!  :oops:

> Your partitioning is a bit of a mess
Well, that's a polite way to put it. ;)  It's a long story to do with Windows and stuff.  Believe it or not, it's actually better than it used to be.  I'm afraid to mess with it too much more so long as things are working, which is what it was doing pre-Hardy.  But I guess things have changed now, and maybe I should go at it again.  

Still haven't had a chance to try some of the suggestions, and will post again as soon as I do.

---

### Post by quixote on 2008-07-04
Completely deleting the /dev/hdc line in /etc/fstab worked!

Why, I can't imagine.  I checked carefully: it was all on one line, there didn't seem to be anything weird about it, and yet there must have been, because commenting it out got rid of the problem!

:lolflag:

I also changed the cdrom line to mount at /media/cdrom0, so that the various links didn't point in a circle.  That bothered me.  The one remaining cd line now looks like this:
```
#cdrom
/dev/cdrom	/media/cdrom0	iso9660		noauto,users
```

Thanks to all!  (I've forgotten how to attach thanks to posts.  Gaaaa.  Will look it up and come back.)

---

### Post by mempman on 2008-07-04
> **quixote said:**
> Completely deleting the /dev/hdc line in /etc/fstab worked!

Why, I can't imagine.  I checked carefully: it was all on one line, there didn't seem to be anything weird about it, and yet there must have been, because commenting it out got rid of the problem!

:lolflag:

I also changed the cdrom line to mount at /media/cdrom0, so that the various links didn't point in a circle.  That bothered me.  The one remaining cd line now looks like this:
```
#cdrom
/dev/cdrom	/media/cdrom0	iso9660		noauto,users
```

Thanks to all!  (I've forgotten how to attach thanks to posts.  Gaaaa.  Will look it up and come back.)



glad u worked it out.  i assume that it was a white space issue, eh?

---

### Post by tipiglen on 2008-07-05
This might help

[http://ubuntuforums.org/showthread.php?t=847645&highlight=cdrom+mount](http://ubuntuforums.org/showthread.php?t=847645&highlight=cdrom+mount)

I had a similar problem, and simply changing the device name in fstab sorted it all out.

Hope it works for y'all

Salaam/Shalom/Shanthi/Dorood/Peace
-ed

---

