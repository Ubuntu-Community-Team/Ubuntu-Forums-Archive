---
title: "Using Ubuntu Live CD to save a computer"
date: 2007-06-12
forum: General Help
---

### Post by Fireblend on 2007-06-12
Hey, a friend of mine's XP computer seems to be in that classic eternal "loading windows->computer resets" loop and I was wondering what I could do with the live CD. I know I could probably install ntfs-3g and recover files from the hard drive assuming it's not that what's damaged in the first place, but is there anything else I can do? Also, Ubuntu doesn't come already with ntfs-3g, and it worries me that I won't be able to connect to internet, so what's another distro that has a LiveCD with ntfs-3g included? I already have Knoppix's and PCLinux's .isos around somewhere, do any of those come with it?

---

### Post by trak87 on 2007-06-12
You can read ntfs partitions without ntfs-3g. Knoppix will do this by default. I'm not sure if the Live Ubuntu will do this. Ntfs-3g adds the ability to write to ntfs but if you are trying to pull data off of that partition, you won't need write capabililties anyway. You just read the ntfs and copy it over to an ext3 or even fat32 partition.

This is what I might do. Remove this HD and attach it to a working Linux box. Boot up and mount the new drive at the command line. Copy the relevant data from the problem drive to another drive. Then move the problem HD back to the original box and reformat/reinstall the target OS. Later you can transfer the data back to the original box via a network. That's one way anyway.

---

### Post by Fireblend on 2007-06-12
That sounds good. How do I mount a NTFS partition while in Ubuntu's Live CD? Something tells me there's no such thing as an intuitive program to mount em (except for ntfs-config, but then again, I have the internet limitation). So what commands should I follow in order to mount it?

I looked for my Knoppix iso but it seems it got lost :( I'll download it again in case this doesn't get any more replies.

---

### Post by srt4play on 2007-06-12
I fixed a Windows PC that had this exact same problem with the utility "ntfsfix" which is in the package "ntfsprogs."

---

### Post by Fireblend on 2007-06-12
> **srt4play said:**
> I fixed a Windows PC that had this exact same problem with the utility "ntfsfix" which is in the package "ntfsprogs."

Ok, I'll take that into account in case I can connect it to the internet... Is there some other way to transfer packages to an offline computer? ;_; Can't I store them in my USB drive or something?

---

### Post by srt4play on 2007-06-12
Yeah you can download ntfsprogs and it's dependency libntfs9 from [http://packages.ubuntu.com](http://packages.ubuntu.com) and put them on a flash drive or external hdd or whatever.

---

### Post by hsweet on 2007-06-12
You can check out the Linux Rescue CD at [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page).  It's not 'Buntu but it has just about any utility you can imagine, including the ability to read and write to ntfs drives.  At least you should be able to get your files copied to some other media

---

### Post by srt4play on 2007-06-12
Hey that system rescue cd looks pretty cool, thanks.

---

### Post by ubuntu27 on 2007-06-12
Xubuntu mounts local Hard Drives by default. 
You can try it: [http://www.xubuntu.org](http://www.xubuntu.org)

---

### Post by tact on 2007-06-12
I had exactly the same problem with my company laptop a few months ago.  the HDD would not boot.  

Using the XP install CD as a recovery tool just told me that the partition is unreadable, like unpartitioned space.  I had so much data I wanted to get OFF that HDD....  *sigh*

Then I tried to use other windows recovery tools like BartPE to boot from CD and windows rescue CD but they also told me the XP NTFS partition was either unreadable or "unpartitioned space".

Then in sheer desperation I grabbed an ubuntu desktop LiveCD  (then it was Edgy Eft, v6.10) and let it boot from CD.   Guess what....  

- it booted fine and recognised ALL the hardware in my Dell laptop.
- It connected to my corporate LAN automatically and the internet
- I could access the windows server shares on my LAN 
- I could mount and READ my so-called unreadable NTFS partition (you DONT need NTFS-3G for this
- I could copy ALL the essential data from the "unbootable and unreadable" drive to my server share on the company file server and at the SAME TIME also:
-- use firefox to access my corporate MS-Exchange server, and work with documents, presentations and spreadsheets,  to do some real work while the file copying went on in the background etc etc etc...

Thats why ubuntu is now a permanent fixture on my corporate Dell laptop today.  I don't even have a windows partition on my HDD at all now.  I just keep a winXP VM on the side in case I ever need to look at XP again.

So how do you mount a NTFS partition while booted from an ubuntu LiveCD?
Even tho booted from CD and your HDD Is not used by ubuntu at all - it is clever and uses a "ram disk" so that even while booted from CD you can create folders etc...you need to create a directory to use as a mount point so 
1.  at a command prompt:
```
mkdir /media/win_drive 
```

2. then find out the name of the windows partition (if not already known) by typing this at a command prompt:
```
sudo fdisk -l
```

The result should look something like this...
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   16  Hidden FAT16
/dev/sda3               6         776     6193057+       NTFS
/dev/sda4             777        9729    71914972+   whatever
/dev/sda5             777        9473    69858621   something else
/dev/sda6            9474        9729     2056288+  who knows

```

If this were your machine then perhaps /dev/sda3 is the partition that is your windows partition (see the file type is NTFS)...  so now to mount /dev/sda3 to the directory you already created (/media/win_drive) you type....
```
sudo mount  /dev/sda3 /media/win_drive
```

done - with a bit of luck an icon representing your windows partition will now appear on your ubuntu desktop (read only).  If not then just click on places and see it its there...  if not then click places>home and go up one level...  see your /media/win_drive folder and then open it.

---

### Post by Fireblend on 2007-06-12
That's great, thanks for all the help, I really appreciate it :D

---

