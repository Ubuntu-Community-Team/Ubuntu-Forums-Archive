---
title: "rescue mode"
date: 2006-07-05
forum: General Help
---

### Post by cheeseman557 on 2006-07-05
Hi,

I found this link that tells me how to get into rescue mode: [http://ubuntuguide.org/wiki/Dapper#How_to_use_Ubuntu_Installation_CD.2C_to_gain_root_user_access](http://ubuntuguide.org/wiki/Dapper#How_to_use_Ubuntu_Installation_CD.2C_to_gain_root_user_access).  The problem is that I don't know where to find the boot: prompt.  Thanks for your help.

---

### Post by tonyr on 2006-07-05
Those instructions are old, I think, and refer to an earlier version of the install cd.  
The release version of Ubuntu has three different install CDs: the Live CD that 
can boot into a full Ubuntu environment, a Server CD, and an Alternate CD.  The last 
two give you a boot choice menu when booting frim the CD.  One of the choices is a 
rescue mode of some kind.  The LiveCD may actually give you that choice, also (I don't 
remember exactly at the moment).  If you only have the LiveCD and it doesn't have a boot
menu with a rescue mode selection, download one of the other versions.

Actually, anything you need to do with rescue mode you should be able to do
with the LiveCD.

---

### Post by cheeseman557 on 2006-07-05
Ok, thanks.  How would I reinstall GRUB if I installed XP after Ubuntu?

---

### Post by tonyr on 2006-07-05
[Here's]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") how, in glorious detail.

---

### Post by cheeseman557 on 2006-07-05
Thank you again, but another problem arises. I get error 22 when I do setup (hd0,5).  When I use gparted to look at my hard drive, it sees it as one big unallocated space with nothing on it.  It does not see my NTFS windows drive, my FAT32 drive or my previous Ubuntu installation.  Any suggestions? Thanks.

---

### Post by tonyr on 2006-07-05
Describe you configuration a little more, please.  How many physical hard drives
do you have, and what kind are they, if you know?

If you are booting the LiveCD, open a terminal (**Applications->Accessories->Terminal**
in Ubuntu, **Kmenu->System->Konsole** in Kubuntu,  type
```

sudo fdisk -l

```
and post the output of that here.

---

### Post by cheeseman557 on 2006-07-05
I have just one physical drive.  It is a 80GB 5400rpm hard drive. The info is all here: [http://www.fujitsu.com/us/services/computing/storage/hdd/mobile/mhv2120bh-sata.html](http://www.fujitsu.com/us/services/computing/storage/hdd/mobile/mhv2120bh-sata.html).
It should have a windows xp ntfs partition, an extended partition for linux and the swap, and a fat32 partition.  The output is here:
```

omitting empty partition (5)

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8492    68211958+   7  HPFS/NTFS
/dev/sda2            8493        9291     6417967+   5  Extended
/dev/sda3            9259        9291      265072+  82  Linux swap / Solaris
/dev/sda4            9292        9546     2048287+   b  W95 FAT32
/dev/sda5            8493        9258     6152832   83  Linux

```

---

### Post by tonyr on 2006-07-05
For your situation, I read the instructions like this:

4. Type: root (hd0,4)
5. Type: setup (hd0)

The partitions on the disk have the names **/dev/sda1**, **/dev/sda2**, etc.
They correspond to the **grub** partion names like this:
/dev/sda1 = (hd0,0)
/dev/sda2 = (hd0,1)
...
/dev/sda5 = (hd0,4)

You are installing the grub control information on **/dev/sda5**, so the **grub**
name is (hd0,4).

Notice that Step 5 does not use the same kind of partition name,  only the
**disk** name, **(hd0)**.

---

### Post by cheeseman557 on 2006-07-05
I followed your instructions several times but I get this error when I type root (hd0,4): Filesystem type unknown, partition type 0x5.  When I type in setup (hd0), I get: Error 17: Cannot mount selected partition.

---

### Post by cheeseman557 on 2006-07-05
I just burned a copy of the Super Grub Disk and after running it automatically, it says no sucess. I noticed a number of Error 21.

---

### Post by tonyr on 2006-07-05
I think this is because **grub** does not know that your **(hd0)** is really
**/dev/sda**.  The way to fix this is to create a file that has this line in it:
```

(hd0) /dev/sda

```
If you have a floppy drive on your machine, the file would need to contain two lines:
```

(fd0)  /dev/fd0
(hd0) /dev/sda

```
In a terminal you can do this by typing
```

echo "(fd0)  /dev/fd0" > device.map
echo "(hd0) /dev/sda" >> device.map

```
and to see the result type
```

cat device.map

```

Then at Step 3, type **grub --device-map=device.map** instead of just **grub**.
Notice that there are **two** hyphens before device-map, not one.

If this doesn't work, I'm out of ideas.

---

### Post by cheeseman557 on 2006-07-06
Unfortunately, that didn't work so I just reformatted my hard drive and installed xp THEN ubuntu.  Thanks for your help through; everything is working fine now.

---

