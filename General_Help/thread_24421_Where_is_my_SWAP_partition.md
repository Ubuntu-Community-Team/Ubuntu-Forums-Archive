---
title: "Where is my SWAP partition?"
date: 2005-04-06
forum: General Help
---

### Post by amerigo5 on 2005-04-06
When I installed Ubuntu 4.10, I have the following partitions:

- 1 GB for swap
- 100 MB for "/boot" (ext3)
- 20 GB for "/" (ext3)
- 20 GB for "/home" (ext3)

I have a Windows XP dual boot.

Now, after several upgrade/update for Ubuntu 5.10 Preview/RC, the System Monitor (Resources) shows the following:

Used Swap: 0 bytes of 0 bytes nan%

Devices: (Device - Directory - Type - Tota)

/dev/hda9 -  /              - ext3   - 20.4 GB
none         - /dev         - tmpfs  - 5.0 MB
/dev/hda8  - /home     - ext3    - 18.3 GB
/dev/hda7  - /boot       - ext3   - 88.2 MB
tmpfs         - /dev/shm - tmpfs - 236.0 MB

My questions are:
1. What happened to my Swap partition? It is not showing in System Monitor.
2. Is it normal to have the additional partitions/devices - none and tmpfs?
3. Anyone noticed the above issue?

Thanks.

---

### Post by Xian on 2005-04-06
[QUOTE=amerigo5]My questions are:
1. What happened to my Swap partition? It is not showing in System Monitor.
2. Is it normal to have the additional partitions/devices - none and tmpfs?
3. Anyone noticed the above issue?[/QUOTE]
My swap partition doesn't show in the sysmon either, but it does list it as being used (2.8 of 878 -LOL). You could check your /etc/fstab to make sure it is being properly mounted, or just open a terminal and do this command:

$ sudo fdisk -l

Check the output and look for a line like this:

/dev/hda2            3266        3377      899640   82  Linux swap / Solaris

---

### Post by amerigo5 on 2005-04-06
Here's the output of 'fdisk -l":

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        9729    62790052+   f  W95 Ext'd (LBA)
/dev/hda5            1913        4462    20482843+   7  HPFS/NTFS
/dev/hda6            4463        4586      995998+  83  Linux
/dev/hda7            4587        4598       96358+  83  Linux
/dev/hda8            4599        7030    19535008+  83  Linux
/dev/hda9            7031        9729    21679686   83  Linux

There is no Linux Swap. Thanks.

---

### Post by amerigo5 on 2005-04-07
Here's my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda9       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /boot           ext3    defaults        0       2
/dev/hda8       /home           ext3    defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda5       /media/windows/d  ntfs    umask=0222      0       0

Is there anything unusual about this file?

Thanks.

---

### Post by Xian on 2005-04-07
[QUOTE=amerigo5] Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        9729    62790052+   f  W95 Ext'd (LBA)
/dev/hda5            1913        4462    20482843+   7  HPFS/NTFS
/dev/hda6            4463        4586      995998+  83  Linux
/dev/hda7            4587        4598       96358+  83  Linux
/dev/hda8            4599        7030    19535008+  83  Linux
/dev/hda9            7031        9729    21679686   83  Linux

There is no Linux Swap.[/QUOTE]
Your fstab notation for mounting the swap partition looks fine, but as you say the fdisk output shows that your /dev/hda6 is not formatted properly as a swap file. I would think the easiest way to approach this would just be to load the Ubuntu installation CD, go to the partition section, select manual partitioning, and then just reformat /dev/hda6 as swap. Then quit the installer at that point and reboot your computer.

---

### Post by amerigo5 on 2005-04-07
I am sure I formatted the /dev/hda6 properly as was shown in the System Monitor tool before. I didn't do anything with my computer/installation except upgrade/update using Synaptic tool. What could have happened to change the partition type of /dev/hda6?

I am now almost tempted to re-install Ubuntu from scratch but I would try to reformat the /dev/hda6 as Xian have suggested.

Thanks.

---

### Post by astoltz on 2005-04-07
You could have a look at dmesg to see if there are any errors reported when trying to mount the swap partition.  That might give you some clues.  

Then I'd try ```
fdisk /dev/hda
``` and change /dev/hda6 back to type "82" which is Linux swap.  Then ```
mkswap /dev/hda6
``` to "format" the swap partion for use.  After that you'd either have to re-boot or do a "swapon" command.  You should probably have a look at the mkswap and swapon man pages before going ahead.

good luck.  don't re-install just yet.

Warning:  changing /dev/hda6 from type 83 to type 82 will kill any data you happen to have on that partition - just be sure.

---

### Post by amerigo5 on 2005-04-07
I used QParted to convert the /dev/hda6 from Linux partition type to Linux-Swap partition type. Then I rebooted my computer. When I opened the System Monitor tool, the tool displayed the percentage of the Linux-Swap patition being used. Then, I did the 'sudo fdisk -l' command but the output didn't reflect the change of partition type of /dev/hda6. 

So, I followed the instructions by astoltz by changing the partition type of /dev/hda6 from 83 to 82 using 'sudo fdisk /dev/hda' command. Then, I did 'sudo mkswap /dev/hda6' command. I rebooted my computer. The 'sudo -fdisk -l' command reflected the change on /dev/hda6 partition. It now shows /dev/hda6 having 'Linux Swap/Solaris' partition type.

Thanks for all the help.

---

### Post by rupe on 2005-05-07
I had this exact problem- but it's been fixed by the tips you kind folks gave.

Cheers!

PS: I suspect it was caused by trying to suspend to disk... I tried that a while ago, but it failed. That writes the RAM to swap doesn't it? So I read in a related thread at least.

---

