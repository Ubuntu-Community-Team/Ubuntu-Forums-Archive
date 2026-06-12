---
title: "Want to move music, videos, maybe photos to Windows space on my dual-boot"
date: 2015-02-02
forum: General Help
---

### Post by t0p on 2015-02-02
I have a Packard Bell EasyNote TS that came with Windows 7.  I made it into a dual-boot with Ubuntu.  I split the HDD in half, 50% for Windows amd 50% for Ubuntu (don't ask me why, I can't remember what I was thinking of).

Anyway, I have a large collection of videos, music and photos, and it's taken up loads of my Ubuntu partition.  So, as I almost never use Windows, I think I could use some of that Windows HDD space for my video/music/photo collection.  But I don't know the best way to go about this.  I suppose thge simplest way would be to defrag Windows 7, shrink the Windows-dedicated disk space, and enlarge the Ubuntu space?  But I'm not really up to speed on partitioning/repartitioning disks.  Could someone please explain how to do this?  And how much HDD space does Windows 7 need as a minimum?  I don't use Windows much at all, but I *do* use it sometimes, and so want it to be usable (otherwise I could just get rid of it and give the entire HDD to Ubuntu... which I don't really want to do.

Cheers.

---

### Post by Bucky Ball on 2015-02-02
Defrag the Windows partition (2 or 3 times is best) and then look at how much space is being taken up by Win on its partition. Do the resize by booting into Win and using its disk management tools. DO NOT use Gparted. This can severely screw things up. Shrink to an appropriate size after defrag. Leave some headroom, e.g. if the Win install takes up 30Gb, make the partition 40Gb so you have room to move. No headroom can cause issues. 

Boot Ubuntu and open Gparted. Create the data partition on the free, uallocated space that has been left by the resize. NTFS if you want to share the files with Win, EXT4 if not. Either way, you will need to add the new partition to the /etc/fstab file if you want it to mount when you boot Ubuntu. We can show you how to do this.

Depending on whether you are using UEFI or BIOS: If you are using BIOS mode install, the physical disk is limited to four partitions per drive. This is NOT the case with UEFI. If BIOS and you already have four partition on the drive, your alternative is to shrink Win, as explained previously, then boot to a Live session (boot from the Ubuntu installer disk/USB), open Gparted, and expand the Ubuntu partition into the free, unallocated space left by the Win shrink. 

Hope that helps. Fire away with any questions if you hit a brick wall. Good luck. ;)

---

### Post by t0p on 2015-02-05
Thanks for the info.  I haven't used the computer for a while so I haven't tried your suggestions yet.  But I will, probably later today.  I'll let everyone know what happens.

---

### Post by t0p on 2015-02-10
I don't have an Ubuntu iso. However, I do have a kubuntu-13.04-desktop-amd64.iso and a lubuntu-13.04-desktop-amd64.iso.  I could use one of them rather than having to download an Ubuntu image, right?  But I'm not a Kubuntu or Lubuntu user, I don't know what the required tools may be called... so can someone perhaps enlighten me on this?  Otherwise I have to wait until my data allowance increases so I can download an Ubuntu image (I access the internet via tethered smartphone unfortunately).  So, in Kubuntu and/or Lubuntu, is Gparted called Gparted?  Or has it a different name (eg "Kparted"... I know how the Kubuntu devs like the letter K...).   Thanks.

---

### Post by slickymaster on 2015-02-10
As you asked, just to let you know that Windows 7 (32 bit) takes a minimum of 16 GB and Windows 7 (64 bit) takes a minimum of 20 GB HDD space.

---

### Post by t0p on 2015-02-10
> **slickymaster said:**
> As you asked, just to let you know that Windows 7 (32 bit) takes a minimum of 16 GB and Windows 7 (64 bit) takes a minimum of 20 GB HDD space.
Thanks for that slickymaster.

I've resized the Windows partition, and now I've run into a problem.  As I don't have an Ubuntu Live image, I used a Kubuntu 13.04 iso that I happen to have already.  Unfortunately I am not a Kubuntu person, and the Kubuntu partition manager seems very different to Gparted.  I can't figure out how to make the new unallocated space into ext4 format.  I need a quickie doofus lesson on how to do it.  I've attached a screenshot of what the partition manager is showing me.

I want to make the unallocated space into ext4 format, then extend sda5 to absorb the new chunk of disk (the partition manager claims I can't make a new partition as I've already reached my limit, and anyway I think it is probably preferable to make the pre-existing partition bigger... is there any reason why it would be better to make a new partition, even if that were possible?).  I've looked at all the menus and clicked on the unallocated space box, and can't find a **format to..** option anywhere.  No doubt this is because I'm used to using Gparted, and if I were a Kubuntu user I'd slap myself round the back of the head for overlooking the obvious...

Anyway... could someone please tell me how to do what I need to do?  I have googled, but the results all seem to go into some depth on the matter which really isn't helpful.  A "do this and this and this" explanation of what I need to do would be much appreciated.

Cheers.

---

### Post by Mark Phelps on 2015-02-10
It looks like you may already have the maxium of 4 upper-level partitions on that drive -- which will prevent ANY partition manager from allowing you to create another partition.

Please open a terminal, enter "sudo fdisk -lu" (lowercase L, not a one) and post the output back here.

---

### Post by yancek on 2015-02-10
Your image shows sda4 as an Extended partition and then of course, sda5 inside it with another small partition (swap?) at the end of the Extended partition.
If sda5 is your Ubuntu partition and you are using the Grub bootloader to boot, I can see potential problems.
You can re-size and move to the left but it will move the data in sda5 also as I understand the process.  This means your boot files are moving so if you have an MBR install it will be looking for the boot files at a specific location and they will no longer be there.  You will get a warning when moving to the left in most case, at least with GParted.

I wouldn't try it without backing up first.  Take a look at the GParted manual dealing specifically with this situation.  I imagine the Kubuntu partitioner will be similar.

[http://gparted.org/display-doc.php?name=help-manual#gparted-advanced-partition-actions](http://gparted.org/display-doc.php?name=help-manual#gparted-advanced-partition-actions)

---

### Post by Bucky Ball on 2015-02-10
Resize the partitions by booting from 13.04, sure, but don't install it. It has reached end-of-life and is no longer supported. But you probably know that ...

Resize the Windows partition with Windows disk management tools ONLY. Don't use Gparted or anything Linux. ;)

---

### Post by slickymaster on 2015-02-10
> **Bucky Ball said:**
> Resize the partitions by booting from 13.04, sure, but don't install it. It has reached end-of-life and is no longer supported. But you probably know that ...

Resize the Windows partition with Windows disk management tools ONLY. Don't use Gparted or anything Linux. ;)
This ^^^

---

### Post by t0p on 2015-02-11
> **Mark Phelps said:**
> It looks like you may already have the maxium of 4 upper-level partitions on that drive -- which will prevent ANY partition manager from allowing you to create another partition.

Please open a terminal, enter "sudo fdisk -lu" (lowercase L, not a one) and post the output back here.

**Mark Phelps:**
```
t0p@mars:~$ sudo fdisk -lu[sudo] password for t0p: 


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4ac3d5d8


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    41945087    20971520   27  Hidden NTFS WinRE
/dev/sda2   *    41945088    42149887      102400    7  HPFS/NTFS/exFAT
/dev/sda3        42149888   246532609   102191361    7  HPFS/NTFS/exFAT
/dev/sda4       432680958   976771071   272045057    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       432680960   964491263   265905152   83  Linux
/dev/sda6       964493312   976771071     6138880   82  Linux swap / Solaris


Disk /dev/mmcblk0: 2045 MB, 2045247488 bytes
47 heads, 46 sectors/track, 1847 cylinders, total 3994624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1             247     3994623     1997188+   6  FAT16


Disk /dev/mapper/cryptswap1: 6286 MB, 6286213120 bytes
255 heads, 63 sectors/track, 764 cylinders, total 12277760 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x75175c72


Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table



```

[B]Yancek & Bucky Ball:
[/B]I have already shrunk the Windows partition with the Windows disk management tool.  Now I have some unallocated space, which I would like to use for storing my videos and music collections.  I am hoping to use the Kubuntu partition Manager to turn the unallocated space into ext4 and ultimately use that space for my media storage.  But I don't know how to use the Kubuntu partition manager to turn the unallocated space into ext4.  And from the above comments it appears my plan won't work anyway. Please note, I am an Ubuntu/Gparted user (Ubuntu 12.04 right now, I'll upgrade when I get a new laptop later this year) so althoughb I kn ow how to use Gparted, I have no clue regarding Kubuntu partition editor.

If there's no way to do what I initially planned, I have another idea.  To use the Windows partition editor to regrow the Windows partition to its initial size, then store my vids/music on the Windows partition (I assume I'll still be able to access and use them while using Ubuntu)?  Is that a viable plan?  If I regrow the Windows partition, how will I make it NTFS?  Will the Windows disk manager do that automatically, or maybe give me a clear option to do so?

All input gratefully received!

---

