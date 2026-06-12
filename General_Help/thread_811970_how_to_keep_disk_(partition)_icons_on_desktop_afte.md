---
title: "how to keep disk (partition) icons on desktop after reboot ?"
date: 2008-05-29
forum: General Help
---

### Post by tomaasj on 2008-05-29
Anyone,

once partitions are mounted on my desktop everything is OK. However, the disk icons are not there anymore after restart.  I have to go to "places" and remount again.  Why is that ?  This situation occured since upgrading to Hardy.  Under Gutsy the partition icons remained on the desktop after restart.  I'm curious and looking for a solution.

Tomaasj

---

### Post by bmac on 2008-05-29
Open configuration editor.
Select apps/nautilus/desktop/
Check "volumes_visible"

Hope this helps....

---

### Post by tomaasj on 2008-05-29
Hi,

thanks for responding.  I tried it and see the icons appear after putting the volume visible setting on"true".  However, after reboot (twice) the icons do not appear on the desktop.  If computer icon visible is set on true it appears after reboot.

---

### Post by WRDN on 2008-05-29
To get the disk icons for the respective drives to always appear, you could try mounting the disks at startup.

You may find the information [here]("http://ubuntuforums.org/showthread.php?t=465789") and [here]("http://www.dedoimedo.com/computers/linux_commands.html") useful.

---

### Post by tomaasj on 2008-05-29
I looked already at the links.  Have to study it.  Tried some of the recommendations (gedit fstab) but was not able to solve the problem so far...

---

### Post by tomaasj on 2008-05-29
worked to get my Data (FAT32) partition on the desktop after reboot.  I'll try also to get the ntfs partition on the desktop. Thanks to both of you for help.

Tomaasj

---

### Post by Ziggy72 on 2008-05-29
If you're still having difficulty, if you post the output of fdisk -l I can probably let you know what to do.

---

### Post by werries on 2008-05-29
yeah, show us your fdisk -l and your /etc/fstab. That way we can help you with what to do so it mounts.
I did this same thing when i upgraded to hardy.

---

### Post by BLTicklemonster on 2008-05-29
Here's my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=b25d84a0-6d07-4744-8cd8-e2ec31702e9a /               reiserfs notail,relatime 0       1
# /dev/hda3
UUID=b791cdda-83d1-4ac4-9056-e8c7b8f371bc none            swap    sw              0       0
# /dev/hdb6
UUID=49d2c741-9972-42f3-b11c-c6f1ca98c176 none            swap    sw              0       0
# /dev/hdd5
UUID=6e4d7df9-832e-4e2a-91f2-2a622b47ab44 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

and here's my fdisk -l

```
bill@bill-desktop:~$ fdisk -l
bill@bill-desktop:~$
```

I should be showing like 7 usable partitions there. Here's my conky config to show what ought to be there:

```
${color}Local File systems:
 Right Here $color${fs_used /}/${fs_size /} ${fs_bar /}
 XP  $color${fs_used /media/disk-2}/${fs_size /media/disk-2} ${fs_bar /media/disk-2}
 Movies  $color${fs_used /media/disk-4}/${fs_size /media/disk-4} ${fs_bar /media/disk-4} 
 Dork  $color${fs_used /media/disk-1}/${fs_size /media/disk-1} ${fs_bar /media/disk-1}
 Storage  $color${fs_used /media/STORAGE}/${fs_size /media/STORAGE} ${fs_bar /media/STORAGE}
 VMWare XP  $color${fs_used /media/disk}/${fs_size /media/disk} ${fs_bar /media/disk}
 Gutsy Beta $color${fs_used /media/disk-3}/${fs_size /media/disk-3} ${fs_bar /media/disk-3}
```

So what is it, like sudo mkdir /media/disk-2 then what over and over again for each partition/drive?

I could swear that I had everything at one time, and set conky up specifically for Hardy. Where did they all go, and why, and is someone aware of this and going to fix it? Wait a cotton picking minute... Nautilus shows every one of them! How? Wait a minute again!!!! I right clicked them all and mounted them and there they are on the desktop!! Bet they won't be there later, huh?

---

### Post by Ziggy72 on 2008-05-30
Well, BLTicklemonster, if something as basic as fdisk -l gives no output, it looks as though you've managed to mess something up very badly and so it's not worth worrying about anything much else until you sort that out. Sorry

---

### Post by BLTicklemonster on 2008-05-30
> **Ziggy72 said:**
> Well, BLTicklemonster, if something as basic as fdisk -l gives no output, it looks as though you've managed to mess something up very badly and so it's not worth worrying about anything much else until you sort that out. Sorry

Tell me about it! I knew when I saw that "you've got upgrades" icon I was going to be in trouble! New kernel, new woes... But like I said, in nautilus, it all shows up, and now the icons are back on the desktop even though fdisk -l shows nothing. Nice thing is, I can use the fstab from gutsy to edit fstab on hardy and bring it all back.

---

### Post by danwood76 on 2008-05-30
You need to have root access for the fdisk command.
So:

```

sudo fdisk -l

```

---

### Post by tomaasj on 2008-05-30
> **Ziggy72 said:**
> If you're still having difficulty, if you post the output of fdisk -l I can probably let you know what to do.

Hi,

below you see the output and the fstab file.  I would like to get my ntfs partition visible on the desktop, with read and write possibility.  I succeeded to get my data partition on the desktop (sda3), which works (read and write).


fdisk -l output:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        2805     2048287+  82  Linux swap / Solaris
/dev/sda3            2806        5355    20482875   83  Linux
/dev/sda4            5356       14593    74204235    c  W95 FAT32 (LBA)

the fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=b36da0b7-2339-4e6f-aa0d-eaafe000e0a2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=67b9ad7f-6e09-4e80-98e1-3551df0c0889 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda4  /media/data    vfat    iocharset=utf8,umask=000  0    0

---

### Post by Ziggy72 on 2008-05-30
tomaasj... 

1) As root, make the directory /media/sda1
2) In fstab add the following two lines:

# /dev/sda1
/dev/sda1 /media/sda1	ntfs	defaults,umask=007,gid=46 0       1
 
If you now do a sudo mount -a you should see the drive ok and it will now show up after every reboot.

You can actually call the directory (which I called sda1) anything you want, as long as you edit the fstab line appropriately - experiment and see for yourself. Good luck. Hope this works ok:)

---

