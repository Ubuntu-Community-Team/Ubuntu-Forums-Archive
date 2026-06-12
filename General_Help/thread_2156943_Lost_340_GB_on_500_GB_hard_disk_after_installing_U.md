---
title: "Lost 340 GB on 500 GB hard disk after installing Ubuntu..."
date: 2013-06-23
forum: General Help
---

### Post by SpiritFuzz on 2013-06-23
Hi all. I have a 500 GB hard disk and am dual booting Ubuntu and Windows 8. It's been a while since I've had to install Ubuntu, but am very familiar with the process due to previous trial and error. I would prefer to stay away from windows entirely, but due to several worldly factors that's not possible at the moment. Anyway, I'm not sure during which install this occurred, but noticed it when I tried to re-size my Windows partition. I know there is a way to restore the missing partition, but am at a loss as to how. I tried Parted Magic, but wound up messing up my MBR, and after fixing it and searching to no avail for a solution on these forums I've decided to post this. Any help would be greatly appreciated, thanks in advance. P.S. I know my way around the command prompt. P.P.S. I won't be able to reply back until tomorrow, just wanted to get this post in and give you all a chance to respond. TTYS.

---

### Post by oldfred on 2013-06-23
May be best to post screen shot from gparted. Go Advanced and use the paperclip icon to attach to post.

Have you booted back into Windows and its run its chkdsk to repair itself? 

Is Windows 8 a pre-installed system with secure boot, or one your installed? 

Mount all partitions and run these
df -h

Post these in code tags (# in advanced editor)
       sudo parted /dev/sda unit s print
      
 sudo blkid -c /dev/null -o list

---

### Post by grahammechanical on 2013-06-23
This is what makes me curious

> [COLOR=#000000]I'm not sure during which install this occurred,[/COLOR]

How many times has Ubuntu been installed? And how many partitions were used? The same ones over again or new ones. How do you know that the 340Gb is "lost?"

Regards.

---

### Post by SpiritFuzz on 2013-06-24
Here's the screenshot from GParted:
[ATTACH=CONFIG]244109[/ATTACH]

And the code:

sudo parted /dev/sda unit s print:
```
william@RAINBOWDATASTORAGE:~$ sudo parted /dev/sda unit s print
[sudo] password for william: 
Model: ATA Hitachi HTS54501 (scsi)
Disk /dev/sda: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system     Flags
 1      2048s       718847s     716800s     primary   ntfs            boot
 2      718848s     229607423s  228888576s  primary   ntfs
 3      229609472s  306823167s  77213696s   primary   ext4
 4      306823168s  312580095s  5756928s    extended                  lba
 5      306825216s  312580095s  5754880s    logical   linux-swap(v1)
```

sudo blkid -c /dev/null -o list:
```
william@RAINBOWDATASTORAGE:~$ sudo blkid -c /dev/null -o list 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    System Reserved (not mounted) 3AD09C95D09C5949
/dev/sda2  ntfs             (not mounted)  3EFEA147FEA0F873
/dev/sda3  ext4             /              5414601a-7cec-4a5d-806b-b824d36ba218
/dev/sda5  swap             <swap>         92a969b8-834f-467f-8c6c-c9b8cd682af3
/dev/sr0   udf     NACHO_LIBRE_PS /media/william/NACHO_LIBRE_PS 
/dev/sdb1  vfat    PENDRIVE /media/william/PENDRIVE 14ED-305F

```

---

### Post by SpiritFuzz on 2013-06-24
P.S. I know you said to mount all partitions, but it wouldn't let me mount the NTFS ones. Sorry for my semi-noobness, but I have a lot of remembering and learning in general to do.

---

### Post by oldfred on 2013-06-24
It looks like gparted did mount your NTFS partition as it shows it and it does not have any red or yellow warning icons.

Did you run chkdsk on the Windows partition from Windows? Or  a Windows repairCD?

Is Windows hibernated? Normally the Linux NTFS driver will not mount a NTFS partition that needs chkdsk or is hibernated.

---

### Post by SpiritFuzz on 2013-06-24
I ran chkdsk from Windows upon restart so it could unmount the partition, and it shouldn't be hibernated because I restarted from Windows to boot into Ubuntu.

---

### Post by oldfred on 2013-06-24
I am not seeing anything else as an issue?

---

### Post by SpiritFuzz on 2013-06-24
Do you have any suggestions for recovering the lost space? I have Parted Magic and it seems as though there are many good tools on it, I just don't know where to begin.

---

### Post by oldfred on 2013-06-24
Virtually everything is saying it is a 160GB hard drive not a 500GB drive?

If you mutliple sectors time sector size you get a 160GB drive.
 Disk /dev/sda: 312581808s
Sector size (logical/physical): 512B/512B

---

### Post by SpiritFuzz on 2013-06-24
Wow, that's just weird. Guess I'll play around a little and see if I can find something. It's about time for another computer anyway. Thanks again for your help.

---

### Post by oldfred on 2013-06-24
Have you looked in Disks or Disk utility, click on drive and on right side it show Smart Status. It can run a lot of tests, but all I know is green or pass is good.

You can also run this & it will show model & serial. Size is embedded in most models.

```
fred@fred-Precise:~$ sudo lshw -C Disk -short
[sudo] password for fred: 
H/W path             Device      Class       Description
========================================================
/0/100/1f.2/0        /dev/sda    disk        160GB MAXTOR STM3[COLOR=#ff0000]160[/COLOR]81
/
```

---

