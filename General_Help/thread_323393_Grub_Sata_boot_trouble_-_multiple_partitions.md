---
title: "Grub Sata boot trouble - multiple partitions"
date: 2006-12-22
forum: General Help
---

### Post by SupRspi on 2006-12-22
Ok..this could be a long one.  I'm new to linux, and ubuntu is working awesome for me at the office, however, I've managed to create a serious mess on my home pc.

First off - hardware.

I have three harddrives:

250Gb Sata
80GB Pata
80Gb Pata

My motherboard is a GA-K8NF-9 which has an Nforce4 chipset.

I have WinMCE installed on my main partition of my SATA drive.  I have 4 partitions on that drive, as follows

1) WinMCE (NTFS)
2) Storage (NTFS, resized with gparted during install)
3)Swap
4) Ubuntu Edgy x86 (Ext3)

On my second 80gb drives, I have one with a bunch of partitions, including an old NTFS partition that had a copy of XP Pro on it, and now has as well a swap and an Ext3 with Dapper x64 on it.

This is what happened.

I made partitions on my 80GB PATA drive to install x64 Ubuntu.  It installed, and seems to have written grub to hd0 - that drive which doesn't boot.  I decided to reinstall and use an x86 version and made new partitions on my SATA drive.  I installed grub to hd2 which is ID'd as my SATA drive.

Eventually I want to delete the partitions on my 80 and use it as a fat32 partition for storage.

When I boot, grub loads and finds both my linux installs.  I can only boot to the one on the 80 (dapper).  My SATA partitions are not bootable - when I choose them they say:

```
 Error 22. No Such Partition. 
```

I'd like to be able to boot to those SATA partitions...I can still mount them in Dapper, and I can see the data, just for some reason any partition I choose on that SATA drive generates that error.

I've included the cat outputs of my menu.lst and my devices.map below incase that helps.

Cat of devices.map
```

suprspi@Quicksilver:/media/sda4/boot/grub$ cat device.map
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda

```

Cat of menu.lst
```

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd2,4)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd2,4)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb7.
title           Ubuntu, kernel 2.6.15-23-amd64-generic (on /dev/hdb7)
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hdb7 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb7.
title           Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode) (on /dev/hdb7)
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hdb7 ro single
initrd          /boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows XP Media Center Edition
root            (hd2,2)
savedefault
chainloader     +1

suprspi@Quicksilver:/media/sda4/boot/grub$


```

If anyone can help I'd be very, very appreciative - want to play guildwars and I'm stuck out of my windows - although I'm learning a bit about linux in the process, which was the intention! 

Cheers!

---

### Post by SupRspi on 2006-12-22
Am at work, so I don't have all the details, but I downloaded GAG last night and made a bootable CD.

It could see my partitions with Windows on them, and an Ext2 partition I don't have, and I could not boot to any partition with GAG.  

Just thought I'd throw that out there in case it helps - I can post more details if required when I get home this afternoon.

Thanks in advance for any help anyone can offer.

Cheers.

---

### Post by SupRspi on 2006-12-27
No suggestions or anything as people are home for the holidays?

I managed to tear my rotator cuff in mr\y shoulder skiing yest. so it looks like i'll be stuck @ home for a bit trying to fix this....

Of i run "fixboot" and/or "fixmbr" from the winxp mce cd, will this at least nuke grub so I can boot o windows again??


*edit:
hmm..I'm an awesome one-handed typer...at least it's my left I hurt...

---

### Post by SupRspi on 2007-01-03
Still have not managed to fix this.

I'd thought that if I run fixboot and/or fixmbr from the windows xp recovery console it would rewrite the bootsector and get rid of grub to let me into windows again - that might work but for some reason the recovery console doesn't see my Win Media install - I think it's only seeing my 80's - I probably have to specify additional drivers to see that SATA drive - I seem to remember having to when I installed windows.

If it helps, my motherboard is a Gigabyte GA-K8NF-9  F6

When my drives are detected my two 80's show up as:

Maxtor 6Y080L0 YAR41BWO x2 as primary master and slave.  One of these has the old old windows xp pro partition on it that I eventually want to delete and the dapper x64 install that I can currently get to.

My sata shows up after and is a Samsung SP2504C VT10033 - this has the two non bootable installs on it, my original windows media center and my ubuntu edgy i386 - these are the ones that come up with error 22 (see above) when I try to boot to them, no matter which partition I try.

Am I missing something in Grub?  Something that lets it boot Sata controllers or something?  The same or similiar thing to why my windows recovery won't seem to see my SATA drive w/o specifying additional drivers?

Any help here?  I really want to get out of Dapper x64 - I can't even get wine to work in it - and this machine is the one I go to when I want to relax and play my games.

---

### Post by SupRspi on 2007-01-04
Still stuck - not even a flame to tell me to use the search function or that I'm posting in the wrong forum.

A google search turned up this post: [http://www.ubuntuforums.org/showthread.php?t=30233](http://www.ubuntuforums.org/showthread.php?t=30233)

Which while readign through it seems like it might be appropriate - it's a little old, does anyone know offhand what the module is for sata/raid support for nforce 4?  The last questioners question is not answered in the thread.....

Does this look like I could be on the right track, that for some reason grub doesn't like booting to a sata drive on an Nforce4 chipset if it isn't the primary drive - or doesn't ID as a primary drive? 

In that case, could I just change my device.map to change the numbering around then edit my grub file to point to different drive numbers - or does this not change the actual behaviour of the drives?  I'm a little loopy on painkillers and caffeine so this may not be making much sense, but I feel like I'm finally on to something.

Man I need to get SSH setup at home so I can do this from work! Grrr.!

---

### Post by smoker on 2007-01-04
hi, i' m not an expert, but i do have two sata drives and i had to adjust a setting to make them bootable from in the bios setup, maybe that is something you could look into,

if your sata is not 'marked' as bootable, this is probably why you cannot get into the recovey console for windows.

there are ways to change the grub menu to suit i believe from reinstalling from the live-cd, though, again, i am no expert. hopefully someone more knowledgable will see your thread soon and maybe post some better answers for you,

hope at least something i've said helps in some way,

---

### Post by SupRspi on 2007-01-04
Hmm.

I`ve changed my bios back and forth, enabling and disabling onboard RAID on the SATA controller, doesn`t seem to make a difference either way.

I did resize some partitions with gparted - perhaps that removed the `bootable` flag from the bootable partitions.  I`ll check this tonight and post back - can I have more than one partition on a drive marked as bootableÉ

---

### Post by quartzy on 2007-01-04
I'm no expert either, but do have a SATA drive called hd seems funny to me, all the SATA drives i've ever seen are called sd something, for example my SATA HDD is /dev/sda whereas my normal PATA is /dev/hdc.

Just a thought.

As a side note I had a really funny thing with GRUB that didn't see my PATA very well, even though the drive is /dev/hdc i had to tell grub to write the MBR to /dev/hda.  Also if your BIOS has a boot list make sure the sata's are on there (some have a boot order that uses specific HDDs).

---

### Post by SupRspi on 2007-01-05
I made some changes last night.

I edited device.map to look like this:

```

(hd0)   /dev/sda
(hd1)   /dev/hdb
(hd2)   /dev/hda

```

Then I edited my menu.lst to point like this:

```

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

**and***

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows XP Media Center Edition
root            (hd0,2)
savedefault
chainloader     +1


```

Now when booting I get different error messages.  

One is an error 17, the other I don't remember.  I'll look them up when I get home and see what they are, but I feel like I'm getting accurate error messages now, I think I'm half way there.  Although, I could be crazy.

I can still boot to my hdb which is where my working x64 dapper install is, just not to my sda which is where my Edgy i386 and XP MCE installs are.

I have SSH installed on my dapper install, and if someone wants to take a look I can give you some login info - it requires mounting one of my drives to see my edgy install, but if someone thinks they can get more info than I can by SSH'ing, I'm up for it.  Just pm me and I'll hook you up with login info.

In my reading I figured out how to do a fdisk -l - I'm posting that info below in case it can help.

```

suprspi@Quicksilver:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        3187    25591545    f  W95 Ext'd (LBA)
/dev/sda2   *        3188       27843   198049320    7  HPFS/NTFS
/dev/sda3           27844       28109     2136645   82  Linux swap / Solaris
/dev/sda4           28110       30401    18410490   83  Linux
/dev/sda5               2        3187    25591513+   7  HPFS/NTFS

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8612    69175858+   7  HPFS/NTFS

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7411    59528826    7  HPFS/NTFS
/dev/hdb2            7412        9964    20506972+   f  W95 Ext'd (LBA)
/dev/hdb5            7412        7418       56196   83  Linux
/dev/hdb6            7419        7553     1084356   82  Linux swap / Solaris
/dev/hdb7            7554        8127     4610623+  83  Linux
/dev/hdb8            8128        9964    14755671    b  W95 FAT32

```

Thanks!

-Jeff

---

### Post by quartzy on 2007-01-06
> **SupRspi said:**
> 
[code]
title           Ubuntu, kernel 2.6.17-10-generic
root            **(hd0,4)**
kernel          /boot/vmlinuz-2.6.17-10-generic **root=/dev/sda4** ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

There is a problem (the bolded bits), grub starts counting from 0 so 0=1 and /dev/sda4 is (hd0,3) in your case.

Also wouldn't it be more logical to map /dev/sda to sd0? and /dev/hda to hd0 etc..

---

### Post by SupRspi on 2007-01-07
Right.


Somehow, I knew that, but needed someone else's eyes to point it out.  I'll try that tomorrow and see if that gets me into my edgy install.

As to what the drives are mapped to, I basically left them as grub found them, except for changing hd0 to sda, as sda originally was hd2 - that's easy enough for me to live with though.

Thanks for the help, I'll try it and post back.

Cheers.

-Jeff

---

### Post by tommcd on 2007-01-07
You might want to try a super grub disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Download from here:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
This is mainly for people who have messed up their boot/grub/menu.lst and can't boot into linux (for example, after reinstalling windows). But it might help in your situation. That is, it might set up grub so both of your ubuntu installs and windows boot properly.
Hope this helps.

---

### Post by SupRspi on 2007-01-07
Thanks guys...here's the latest update, and pretty much the final answer for me.

Quartzy was right, 100%.  I though grub only counted from zero for drive numbers, not partitions. (duh, in hindsight)

I changed my settings to what he suggested, and presto - I'm in Edgy!  Now I have lots of downloading and configuring, but I'm in the linux install I want to be in.

I can also boot to my XP partition as well - just subtracted a number from the partition I was trying to boot to and it works like magic...well, almost.

Turns out I somehow messed up my hardware abstraction layer - so I'll have to do a repair install of XP to rebuild my hal.dll - otherwise that should work.    I'll take your advice Tomcd and make a supergrub disk - that way if my repair install blows up my grub I can back into linux to fix it again.  I seem to be on the right track.

Thanks guys!

---

### Post by quartzy on 2007-01-08
Glad to see you got it working :)

---

