---
title: "Unknown devices on fdisk -l or blkid"
date: 2022-03-16
forum: General Help
---

### Post by dwlamb on 2022-03-16
Recently, I did a listing of hard drives connected to my system using blkid.  To utter surprise I found a lot more than I thought I might.  Aside from /dev/sd* I discovered 11 entries similar to '/dev/loop0: TYPE="squashfs"' where the only difference is loop0 through loop10.

I have no idea what created these entries.  They appear with date stamps equal to each time I reboot the PC. Here is a sample of the output from  'stat /dev/loop0'
```
  File: /dev/loop0
  Size: 0             Blocks: 0          IO Block: 4096   block special file
Device: 6h/6d    Inode: 126         Links: 1     Device type: 7,0
Access: (0660/brw-rw----)  Uid: (    0/    root)   Gid: (    6/    disk)
Access: 2022-03-16 17:25:19.754310955 -0400
Modify: 2022-03-16 17:20:05.475940929 -0400
Change: 2022-03-16 17:20:05.475940929 -0400
 Birth: -

```


Listing using: `ls -l /dev/loop*` yields:
```

brw-rw---- 1 root disk  7,   0 Mar 16 17:20 /dev/loop0
brw-rw---- 1 root disk  7,   1 Mar 16 17:20 /dev/loop1
brw-rw---- 1 root disk  7,  10 Mar 16 17:20 /dev/loop10
brw-rw---- 1 root disk  7,  11 Mar 16 17:20 /dev/loop11
brw-rw---- 1 root disk  7,   2 Mar 16 17:20 /dev/loop2
brw-rw---- 1 root disk  7,   3 Mar 16 17:20 /dev/loop3
brw-rw---- 1 root disk  7,   4 Mar 16 17:20 /dev/loop4
brw-rw---- 1 root disk  7,   5 Mar 16 17:20 /dev/loop5
brw-rw---- 1 root disk  7,   6 Mar 16 17:20 /dev/loop6
brw-rw---- 1 root disk  7,   7 Mar 16 17:20 /dev/loop7
brw-rw---- 1 root disk  7,   8 Mar 16 17:20 /dev/loop8
brw-rw---- 1 root disk  7,   9 Mar 16 17:20 /dev/loop9

```

The only package I installed recently that might account for this is qemu.  I was unhappy with the installation and removed that plus all dependencies, rebooted and removed many packages associated with the initial installation and are not loner required using 'sudo apt autoremove'.

"squashfs" I have seen before as a utility Parted Magic relies on.  Though I have not used the utility on this machine.

The only other major package I have installed that might account for additional hard  drive devices is VirtualBox.

I looking for input as to what might have added these devices to my system and what to do to remove them.  While the show up using fdisk -l or blkid they do not show up using Partition Manager.

Does anyone have a clue as to what these are and how to go about removing them?

---

### Post by grahammechanical on 2022-03-16
Please run this command:

```
snap list
```

That will list all the snap packaged application and packages on your system. I think that snap packages get listed as loop devices and use the squashfs file system.

Open the Disks utility and see if any loop devices are listed and you will that they are snap packaged and use the squashfs file system.

Regards

---

### Post by #&amp;thj^% on 2022-03-16
Welcome to Snap!
use this to understand what is:
This is off one of my now defunct drives
```
lsblk  
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT  
loop0    7:0    0  14.5M  1 loop /snap/gnome-logs/37  
loop1    7:1    0   2.3M  1 loop /snap/gnome-calculator/170  
loop2    7:2    0  86.6M  1 loop /snap/core/4486  
loop3    7:3    0  86.6M  1 loop /snap/core/4650  
loop4    7:4    0   1.6M  1 loop /snap/gnome-calculator/154  
loop5    7:5    0  14.5M  1 loop /snap/gnome-logs/34  
loop6    7:6    0   3.3M  1 loop /snap/gnome-system-monitor/36  
loop7    7:7    0   2.3M  1 loop /snap/gnome-calculator/178  
loop8    7:8    0    13M  1 loop /snap/gnome-characters/101  
loop9    7:9    0   3.7M  1 loop /snap/gnome-system-monitor/45  
loop10   7:10   0 139.5M  1 loop /snap/gnome-3-26-1604/64  
loop11   7:11   0   140M  1 loop /snap/gnome-3-26-1604/59   
loop12   7:12   0   3.7M  1 loop /snap/gnome-system-monitor/41  
loop13   7:13   0    21M  1 loop /snap/gnome-logs/25  
loop14   7:14   0  12.2M  1 loop /snap/gnome-characters/69  
loop15   7:15   0    13M  1 loop /snap/gnome-characters/96  
```

---

### Post by GhX6GZMB on 2022-03-16
Yep, snap.
snapd is first my deinstall when I set up a machine. Saves me a lot of trouble later.

---

### Post by dwlamb on 2022-03-16
Yes, snap was indeed the culprit for creating all of these devices.  Only having one package installed with snap, I remove it and the snap package and all of the devices were gone.

---

