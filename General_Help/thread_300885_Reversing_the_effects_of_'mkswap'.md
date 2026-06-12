---
title: "Reversing the effects of 'mkswap'"
date: 2006-11-16
forum: General Help
---

### Post by MJN on 2006-11-16
Hi all,
 
I was experimenting rebuilding a new machine using my backups and, in the process, had to build the necessary partitions for the machine.
 
Following the restore all seemed hunkydory until I realised that my swap partition wasn't being used. I believe this to be down to me having created the swap partition, and marking as type swap with fdisk, but not doing anything further...
 
Hence, the solution was simple enough - just run **sudo mkswap /dev/hda2** and turn swap on with **sudo swapon -a /dev/hda2**.
 
Easy. Although of course in my case /dev/hda2 was actually my root partition and I should've run it on /dev/hda5! D'oh! End result was perhaps unsurprising - a seemingly empty root partition and it certainly won't boot.
 
Given that the mkswap command took all of half-a-nanosecond to complete I am assuming that whatever it did was relatively small - perhaps a marker/signature/identifier of some sort? Anyone know? Or, more to the point, anyone know how to get back to where I was?
 
As I said, this was just an backup/restore experiment on a test machine however I don't want to miss this opportunity of learning from this 'mistake' hence would still appreciate any advice/suggestions on how to recover from this error... an error which I could easily see happening again, to someone else if not to me!
 
Happy to provide any diagnostic output if required (e.g. partition tables etc).
 
Mathew

---

### Post by MJN on 2006-11-16
Thought this might be useful for the archive and the next poor bugger that makes this mistake...

Thanks to a PM from *woedend* (I noticed in the archive that he'd done something similar but no details of the fix were given!) it's now fixed!

Turns out that a simple **e2fsck** run on the broken partition is all it takes! For what it's worth, the 'fixes' didn't appear to be particularly along the lines of 'looks like a swap partition but is actually standard ext3 so I'll fix it' - more just various inode issues and other things I can't remember... (I didn't think it was going to work so didn't pay much attention at the time!) so I'm still none the wiser as to what **mkswap** actually did in the first instance.

Mathew

---

### Post by kolesarm on 2007-02-24
> **MJN said:**
> Thought this might be useful for the archive and the next poor bugger that makes this mistake...



Matthew, that sure was - i did the same thing - ran mkswap on my main, rather than swap, partition, to lose all my data. spent two days messing around, until i found your thread - thanks a lot for posting it, saved me - now everything is back!

---

### Post by MJN on 2007-02-25
Good to hear it! The archives have certainly saved my bacon in the past!

Mathew

---

### Post by sibun on 2007-10-04
Hi, a Linux noob here!

I'm dual booting with Ubuntu 7.04 on one HDD and XP on another.

I accidentally ran mkswap on one of my XP partitions :confused:  

I only allow Ubuntu to read my XP disk using NTFS config tool and the partition appears unchanged under XP but Ubuntu of course, no longer recognises it other than as swap!

Can anyone explain to me how to change it back using e2fsck (ie. what commands to put into a terminal), assuming that's what I need to do?

Thanks in advance.

Edit:
After thinking about it I'm guessing that e2fsck will reformat to Ext2 when I actually need to reformat to NTFS.  I'm assuming that in reality it still is NTFS, it's just that I need Ubuntu to somehow be told to "see it"  as such again?

---

### Post by MJN on 2007-10-04
e2fsck isn't a file system formatter, but rather a file system repair tool. However, as the name implies, it's meant only for (and hence therefore presumably will only work with) ext2/3 file systems.

You could try **fsck <partition e.g. /dev/hda1>** which is a frontend to e2fsck as well as several other filesystem repair tools however not having used NTFS within Linux I don't know if there is a suitable tool for it. The worst that can happen is that it'll complain about not being compatible as it won't go ahead with anything unless forced/told to do so.

It's interesting that you say the NTFS partition still works fine in XP. Although, having said that, I really don't know what the mkswap tool is actually doing.

Post the output of **sudo fdisk -l <device e.g. /dev/hda> **as it could be simply a case of it having set the partition ID to 82 (as opposed to 86/87 for NTFS).

Mathew

---

### Post by sibun on 2007-10-04
Here's what I got from **sudo fdisk -l /dev/hda5**   :-



Disk /dev/hda5: 1077 MB, 1077479424 bytes
255 heads, 63 sectors/track, 130 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/hda5p1   ?       13578      119522   850995205   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(368, 111, 45) logical=(13577, 238, 11)
Partition 1 has different physical/logical endings:
     phys=(371, 101, 51) logical=(119521, 238, 60)
Partition 1 does not end on cylinder boundary.
/dev/hda5p2   ?       45382       79243   271987362   74  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(67, 115, 32) logical=(45381, 70, 3)
Partition 2 has different physical/logical endings:
     phys=(299, 114, 44) logical=(79242, 34, 29)
Partition 2 does not end on cylinder boundary.
/dev/hda5p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(114, 111, 32) logical=(10498, 56, 41)
Partition 3 has different physical/logical endings:
     phys=(353, 115, 52) logical=(10498, 56, 40)
Partition 3 does not end on cylinder boundary.
/dev/hda5p4          167628      167631       25817+   0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(167627, 190, 52)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(167630, 245, 26)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order



Under XP the partition is working and properties indicates that it is still NTFS format.
It looks like mkswap has simply made it appear to Ubuntu as being a linux swap partition.

If it is the case that the partition ID is the only thing that has been changed by mkswap would I be able to correct it manually?

---

### Post by MJN on 2007-10-04
Drop the **5** off the end of the command as fdisk is looking for the partition table which covers the whole disk...

---

### Post by sibun on 2007-10-04
Oops!

sudo fdisk -l /dev/hda

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         447     3590496   1b  Hidden W95 FAT32
/dev/hda2   *         448        2798    18884407+   7  HPFS/NTFS
/dev/hda3            2799        9729    55673257+   f  W95 Ext'd (LBA)
/dev/hda5            2799        2929     1052226    7  HPFS/NTFS
/dev/hda6            2930        4236    10498446    7  HPFS/NTFS
/dev/hda7            4237        9467    42017976    7  HPFS/NTFS
/dev/hda8            9468        9729     2104483+   7  HPFS/NTFS


hda5 is the offending partition!

Cheers,
Simon.

---

### Post by MJN on 2007-10-04
Hmm... the ID type says 7 which is indeed NTFS so no problems there (my earlier 86/87 guess was wrong).

I'm running short of ideas now as I've got no experience of accessing NTFS partitions under Linux so don't know the methods of access.

Out of interest, what does your /etc/fstab look like?

Mathew

---

### Post by sibun on 2007-10-04
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hdc2 :
UUID=e197bbd7-0599-4485-9ceb-732f577c477f / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hdc1 :
UUID=bba0465e-5573-4e80-874a-34cbb8bc3867 /boot ext3 defaults 0 2
# Entry for /dev/hdc4 :
UUID=41f7d30c-7e0d-46d8-97be-5959fb906b92 /home ext3 defaults 0 2
# Entry for /dev/hdc3 :
UUID=3a128a3d-aae2-4d54-ba24-6cdaa1ca08ca none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda8 /media/Hodes\040Docs ntfs umask=222,utf8 0 0
/dev/hda7 /media/Reservoir ntfs umask=222,utf8 0 0
/dev/hda6 /media/Simes\040Docs ntfs umask=222,utf8 0 0
/dev/hda5 /media/Temp\040Files ntfs umask=222,utf8 0 0
/dev/hda2 /media/HDD ntfs umask=222,utf8 0 0
/dev/hdc5 none swap sw 0 0


Here's my Linux HDD partitions aswell :-

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1          12       96358+  83  Linux
/dev/hdc2   *          13        1763    14064907+  83  Linux
/dev/hdc3            9067        9729     5325547+   5  Extended
/dev/hdc4            1764        9066    58661347+  83  Linux
/dev/hdc5            9067        9328     2104483+  82  Linux swap / Solaris
/dev/hdc6            9329        9729     3221001    7  HPFS/NTFS

---

### Post by MJN on 2007-10-04
I thought perhaps your fstab may have been updated to use /dev/hda5 as your swap but evidently not.

I'm afraid I'll have to leave you here and hopefully someone with NTFS-mounting experience can jump in to take it further..

Did you try sudo e2fsck /dev/hda5 (or, better still, sudo fsck /dev/hda5) just to see what it reckoned? You might need to run sudo umount /dev/hda5 first (just in case it is mounted - actually.. post the output of **mount** just to confirm it's not mounted already).

Mathew

---

### Post by sibun on 2007-10-04
**mount**

/dev/hdc2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hdc1 on /boot type ext3 (rw)
/dev/hdc4 on /home type ext3 (rw)
/dev/hda8 on /media/Hodes Docs type ntfs (rw,umask=222,utf8)
/dev/hda7 on /media/Reservoir type ntfs (rw,umask=222,utf8)
/dev/hda6 on /media/Simes Docs type ntfs (rw,umask=222,utf8)
/dev/hda5 on /media/Temp Files type ntfs (rw,umask=222,utf8)
/dev/hda2 on /media/HDD type ntfs (rw,umask=222,utf8)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

Just to add, when I initially ran mkswap incorrectly, hda5 was mounted (i meant to do hdc5)!
GParted shows it as swap and when I try partition>swapoff it gives error "invalid argument" ?

---

### Post by sibun on 2007-10-04
**sudo umount /dev/hda5** successfully unmounted hda5
then
**sudo fsck /dev/hda5**
fsck 1.40-WIP (14-Nov-2006)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/hda5

Both OS are working ok and I don't need to access the problem partition from Ubuntu but it's just frustrating that I can't correct my error and it will continue to nag me til I sort it!  I might try restoring my / and /boot partitions from a backup image and see what happens (of course I'll never know then).

Thanks for your time Mathew, much appreciated.

---

### Post by MJN on 2007-10-04
That means there's no NTFS handler for fsck - stands to reason really given the NTFS standard is not completely understood hence being able to check/repair it is asking a bit much.

I'm sure someone will be along soon enough with some ideas...

Mathew

---

### Post by mar_rud on 2007-10-07
I had similar (not the same, but worse) problem and finally fixed it.

But from the beginning:
I played with mkswap and forgot, that sda1 is my primary Windows XP partition (NTFS). I didn't run swapon, so only damage was from mkswap. I tried to boot Windows unfortunately without success (black screen with nothing).

After some investigation I discovered, that mkswap overwrites 3kB skipping first 1kB of device/file which it was run on. I don't really know, what it is on disk on nonboot partition there, but in my case (boot partition) it made my WinXP unable to start.

What I did was to copy this 3kB from another machine with working windows XP. I checked last bytes of first untouched 1kB of partition and it was identical, so what could go worse than it is now ;)

I did on Machine A (working) with Windows boot partition /dev/hdb1:
# dd if=/dev/hdb1 of=working.dd bs=1024 count=4
and on Machine B (nonworking because of mkswap) with broken /dev/sda1 partition:
first backup in case of something going wrong:
# dd if=/dev/sda1 of=backup.dd bs=1024 count=4
and finally fix (hopefully):
# dd if=working.dd of=/dev/sda1 bs=1024 skip=1 seek=1 count=3

And now, I can again boot to my Windows XP box.

I don't know if it helps in other then mine cases and this procedure can be dangerous so really check what partitions You modify this time, or things will get worse. I'm not really sure if everything is fine in my case (I was just happy enough, that I could boot to Windows again). Probably best solution would be running some recovery tools instead, but I hadn't any in hand and laptop disk is uneasy to connect to other machine.

---

### Post by sibun on 2007-10-08
Interesting. Thanks for sharing.

Turns out my partition had been altered by mkswap but XP didn't seem to notice!?!  Only Ubuntu saw it as linux swap format.

Luckily I was able to repair my WinXP partition relatively easily because it wasn't the boot partition.  I just backed up the files contained on it, formatted it back to NTFS with GParted and copied the files back.

I've learned my lesson though - from now on i'll make regular backups and double check everything before hitting enter! :wink:

---

