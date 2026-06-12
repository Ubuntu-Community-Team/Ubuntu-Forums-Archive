---
title: "Gnome Disk + LUKS Partition: No Such Device"
date: 2024-08-10
forum: General Help
---

### Post by linuxguy2 on 2024-08-10
I am trying to create a LUKS volume on an 18TB Backup drive. It was previously partitioned and used with LUKS without issue. But now that I am trying to format the whole drive to use with LUKS (Ext4) and I get an error every time saying:

```
Failed to Mount "Backup Drive".
Error Unlocking /dev/sda1: Failed to activate device: No such device
```

What is going on? I've dug around and seen that a potential solution includes dealing with FStab. But I've never had to do this before.
Why is Gnome Disk responding this way? Is there some TB limit for LUKS or Ext4? Is this a bug? Does anybody know what is going on and how I resolve this?

---

### Post by #&amp;thj^% on 2024-08-10
What command did you use? (Details may be important)
Also will you show us this:
```
sudo lsblk
```

---

### Post by linuxguy2 on 2024-08-10
I did it from the Gnome Disks GUI. I just clicked on the drive on the left pane and clicked on the format command on the right pane and told it to format in Ext4 with LUKS. It tried, but then gave me the error I mentioned.

Here is my lsblk output:

```


NAME                   MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTS
loop0                    7:0    0     4K  1 loop  /snap/bare/5
loop1                    7:1    0  74.2M  1 loop  /snap/core22/1380
loop2                    7:2    0  74.2M  1 loop  /snap/core22/1439
loop3                    7:3    0 268.4M  1 loop  /snap/firefox/4650
loop4                    7:4    0 269.8M  1 loop  /snap/firefox/4698
loop5                    7:5    0 504.2M  1 loop  /snap/gnome-42-2204/172
loop6                    7:6    0 505.1M  1 loop  /snap/gnome-42-2204/176
loop7                    7:7    0  91.7M  1 loop  /snap/gtk-common-themes/1535
loop8                    7:8    0  38.7M  1 loop  /snap/snapd/21465
loop9                    7:9    0  38.8M  1 loop  /snap/snapd/21759
sda                      8:0    1     0B  0 disk  
sdb                      8:16   0   3.6T  0 disk  
&#9492;&#9472;sdb1                   8:17   0   3.6T  0 part  
sdc                      8:32   0  16.4T  0 disk  
&#9492;&#9472;sdc1                   8:33   0  16.4T  0 part  
nvme0n1                259:0    0   3.6T  0 disk  
&#9500;&#9472;nvme0n1p1            259:1    0   512M  0 part  /boot/efi
&#9500;&#9472;nvme0n1p2            259:2    0   1.7G  0 part  /boot
&#9492;&#9472;nvme0n1p3            259:3    0   3.6T  0 part  
  &#9492;&#9472;nvme0n1p3_crypt    252:0    0   3.6T  0 crypt 
    &#9500;&#9472;vgxubuntu-root   252:1    0   3.6T  0 lvm   /var/snap/firefox/common/host-hunspell
    &#9474;                                             /
    &#9492;&#9472;vgxubuntu-swap_1 252:2    0   1.9G  0 lvm   [SWAP]


```

---

### Post by #&amp;thj^% on 2024-08-11
Anyway to persuade you not to use Gnome Disks?

Please have a look here: [https://www.cyberciti.biz/security/howto-linux-hard-disk-encryption-with-luks-cryptsetup-command/](https://www.cyberciti.biz/security/howto-linux-hard-disk-encryption-with-luks-cryptsetup-command/)
I as a rule first run this before any formating takes place:
```
fdisk -l
```
As root.
If you have any questions just reply back with that question.

---

### Post by linuxguy2 on 2024-08-12
I've never had a problem with Gnome Disks, but it does look like I will  have to go another route this time and maybe from now on.
I guess you didn't find anything particularly off with that output then...?

The only thing interesting I noticed from fdisk about the disk in question is this message:

```

Partition 1 does not start on physical sector boundary.

```

---

### Post by The Cog on 2024-08-12
**[FONT=Courier New]lsblk -fmp[/FONT]** would give more information. But I think the clue is in the first post: > trying to format the whole drive - if you format the whole drive, then it won't have a partition table and won't have any partitions. In that case, there won't be an sda1 partition, just the formatted sda drive. So try unlocking /dev/sda instead of /dev/sda1.

---

