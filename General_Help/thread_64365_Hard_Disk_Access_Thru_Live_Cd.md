---
title: "Hard Disk Access Thru Live Cd"
date: 2005-09-10
forum: General Help
---

### Post by naive on 2005-09-10
How can i access my hard disk thru live cd?
If it matters i am using FAT32 fs on win98

---

### Post by nuk130n on 2005-09-10
I'm not sure if the live cd does automatic mounting of windows (fat32/ntfs) partitions like knoppix does. If it does, check /mnt. You'll probably find what you're looking for there.

If not, here are some pointers;
What you need to do is create a folder and then use mount to "tell" the system that a partition are to be mounted on it.

Think of it as giving a name and location to your partition.
I.e if you mount /dev/hdc1 to /mnt/videos you're telling ubuntu that you want to access partition /dev/hdc1 at /mnt/videos.

Open up a console window and type "sudo fdisk -l" (without the brackets).
This should give you information about your system's harddrives.

Any partition of type ntfs are (shock!) ntfs drives. I don't remember what fat32 disks are called but it should be easy to spot.

When you have found the name of the partition you want to mount (look under device), you're ready to mount it.

Create a folder under /mnt (i.e sudo mkdir /mnt/videos) and mount it (sudo mount <device name here> <folder name here>) 
This could look like this : sudo mount /dev/hdc1 /mnt/videos
All the data on your partition should now be accessible under the new folder.
Note that it may be useful for you to read the man pages on mount.
To do so, open up a console window and run man mount.

---

### Post by krusbjorn on 2005-09-10
Fat32 partitions are usually called vfat in linux, afaik.

---

### Post by jzke on 2005-09-11
I really need to access my Linux HDD, which won't because of an Xorg bug... I looked in /mnt/ but there's nothing there... Then I tried your above instructions, and got this error...

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4677    37567971   83  Linux
/dev/hda2            4678        4865     1510110    5  Extended
/dev/hda5            4678        4865     1510078+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mkdir /mnt/linux-hdd
ubuntu@ubuntu:~$ sudo mount /dev/hda1 /mnt/linux-hdd
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Any help would me much appreciated. What I'm trying to do is access my Breezy hard drive from a Hoary Live CD.

---

### Post by nuk130n on 2005-09-12
Are you trying to access a fat32 partition?
If so you're looking at the wrong harddrive.
Do you have a linux install on /dev/hda1?

---

