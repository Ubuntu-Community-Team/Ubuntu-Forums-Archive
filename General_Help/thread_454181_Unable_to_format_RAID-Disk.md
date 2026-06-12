---
title: "Unable to format RAID-Disk"
date: 2007-05-25
forum: General Help
---

### Post by H0rst on 2007-05-25
Hello!

I've installed ubuntu 7.04 server amd64 and now I try to get my little RAID-System working. The RAID is attached via SCSI to an Adapted 29160SCSI adapter. It is recognized by the kernel and accessable through /dev/sda:

> 
dmesg:
...
[   60.199954] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   60.199955]         <Adaptec 29160 Ultra160 SCSI adapter>
[   60.199957]         aic7892: Ultra160 Wide Channel A, SCSI Id=7, 32/253 SCBs
[   60.199958]
[   60.200366] scsi 0:0:0:0: Direct-Access     FX-1200U 3-R              0001 PQ: 0 ANSI: 3
...
lshw:
...
  *-disk:0
       description: SCSI Disk
       product: 3-R
       vendor: FX-1200U
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 0001
       serial: 00006789300211
       size: 1035GB
       capacity: 1035GB
       capabilities: 5400rpm partitioned partitioned:dos
       configuration: ansiversion=3
     *-volume
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 1035GB
          capabilities: primary
...



/dev/sda1 was a NTFS partition and I was also able to mount it. But now I want to format the filesystem to ext3. 
Like in the [doc]("https://help.ubuntu.com/community/InstallingANewHardDrive") I used fdisk to delete the existing partition and to create a new one (primary, linux). Then I invoke mke2fs -j /dev/sda1 and wait..... until it ends with:

> 
Writing inode tables: done
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir


When I now try to mount the device I get a "mount: /dev/sda1 is not a valid block device" message. And when I look at lshw I only see 
> 
...
  *-disk UNCLAIMED
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@0:0.0.0


So, does anyone has an idea what the reason for this could be or how this problem could be solved?

Thanks in advance, 
Till

---

