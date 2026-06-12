---
title: "Need help to reduce size of virtualised Raid1 Disk"
date: 2021-01-08
forum: General Help
---

### Post by mpalmer22 on 2021-01-08
Hi, I'm a complete Noob at Ubunto and I did a job for one of my clients where they had a old Linux App that they wanted to keep using, so I pulled a hard-drive from their old Linux server (which was part of a RAID1 array), and connected it externally to another computer and used DD from a Ubunto Boot disk to convert it to a raw Image.

I then converted it again from a RAW to a VDI using VBoxManage and then again to VMDK as to host in using VMware Workstation Player on their new Windows Server

Miraculously this has worked perfectly (even though I was oblivious to what I was doing), but I noticed that when I virtualised the disk, rather then virtualising just the used storage (around 40GB) it virtualised the entire 800GB drive. Now this is starting to cause storage issues on the server because t's taking up a huge amount of necessary space in the backups.

I've tried to do my own research on how to compress this storage, and I've spent a few sleepless nights doing this, but I just can't figure it out. I can't switch my thinking from Windows Volumes, to Linux Volumes. I don't understand what the difference between /dev/md2 and /dev/sda4 is. Why can't I simply browse these directories using "ls /dev/md2" (keeps giving me file doesn't exist errors). Most forums seem to assume you know what they are.

Here's the information I gathered so far about the current config
-----------------------------------------------------------------------------------------------
Server Name is Shrek (running Ubunto 12.04 (64-bit))
 - Checked Storage "df -h --total"
 - - Total Size: 909GB / Used: 783GB (91%) / Available: 81GB
 - - Directory /dev/md2 is using 770GB

 - Researched dev/md2 - Found that this is part of a RAID Config
 - - nano /etc/mdadm/mdadm.conf (took note of UUID Details)
 - - - ARRAY /dev/md/0 UUID=74d16840:784552c6:2f3c46fa:9b2d69ec
 - - - ARRAY /dev/md/1 UUID=3f1352a8:ef68d0c8:149029b4:4c910b25
 - - - ARRAY /dev/md/2 UUID=fcb4ecc2:b0d59674:f6e92feb:da8c4630


 - - cat /proc/mdstat
 - - - MD0: Active Raid1 sda1(0)
 - - - MD1: Active RAID1 sda2(0)
 - - - MD2: Active RAID1 sda4(0)
-----------------------------------------------------------------------------------------------

Just need help figuring out how to get the actual file size breakdown of /dev/md2 and how to reduce the disk size to match the storage actually used (because I know it's not 783GB)

---

### Post by TheFu on 2021-01-09
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

might help clarify how 
  simple partitions --> SW-RAID --> file system -->  mount point

I think you'll have to backup the files, create a new, smaller, array, create a file system, mount the file system, then restore it.  Last, update the fstab to mount the file system.

---

### Post by SeijiSensei on 2021-01-10
Names like /dev/sdX refer to disks, originally SCSI disks but now expanded to include SATA.  (The older disk format before SATA appears as /dev/hdX.)

Names like /dev/mdX refer to RAID arrays created with the mdadm utility.

Like TheFu, I think you should back up all the data and recreate the file systems. Also if you're going to be using that server, you'll want to upgrade to 20.04.  12.04 has been out of support for years now.

---

