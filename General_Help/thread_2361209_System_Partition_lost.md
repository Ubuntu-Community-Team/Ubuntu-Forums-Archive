---
title: "System Partition lost"
date: 2017-05-13
forum: General Help
---

### Post by lokin2 on 2017-05-13
Hello,
iam using a laptop with dual boot windows/kubuntu. After the windows creator update the laptop was unable to start (grub boot manager was in recovery mode). I tried to fix this with the Ubuntu repair tool on an live system, which didn't work (grub was still in recovery mode). After switiching back to the live system and checking gparted i can't find any ext4 partion. Is their any way to recover the partition and system?
The linux system should be on nvme0n1p4. (Iam sory for the bad picture quality.)
[IMG]https://picload.org/image/rigldarw/792b971f-8eca-4dee-ad07-1707d9.jpg[/IMG]

I hope someone can help me. Thanks in advance.

---

### Post by oldfred on 2017-05-13
Is this a BIOS/MBR install but on a very new NVMe drive? Systems that new almost always are UEFI with gpt that does not have the MBR issue.

With BIOS installs Windows since maybe before Windows 7 has a bug that deletes logical Linux partitions in extended partitions when using MBR(msdos) partitioning. Partition is still there just that Windows updates partition table and forgets to include the Linux partition.
In your case the 106GB. And the extended partition is nvme0n1 drive and partition are the  p1, p2 etc  after drive. 

       backup partition table before any changes, so you can get back to current if changes not correct  (these commands are for standard sda, sdb drives, in your case replace with the newer NVMe drive.
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 

These are all the same fix with either parted rescue or testdisk. Read several to better understand process. 
One or two user incorrect saved partition table data with testdisk, so make sure you have the backup.

---

### Post by lokin2 on 2017-05-14
First of all thank you for your reply. I have no idea if it was MBR or GPT. Iam using a thinkpad with nvme drive. The Windows installation was not older than 2 month, so I guess it was not MBR.
I did the backup with sfdisk and parted. 
sfdisk result
```

label: dos
label-id: 0xbe951eec
device: /dev/nvme0n1
unit: sectors


/dev/nvme0n1p1 : start=        2048, size=     1024000, type=7, bootable
/dev/nvme0n1p2 : start=     1026048, size=   383161809, type=7
/dev/nvme0n1p3 : start=   384188416, size=     1624064, type=27
/dev/nvme0n1p4 : start=   385816574, size=   360491010, type=5
/dev/nvme0n1p5 : start=   609591296, size=    39059456, type=82
```

parted result
```
ubuntu@ubuntu:~$ sudo parted /dev/nvme0n1 unit s print
Model: Unknown (unknown)
Disk /dev/nvme0n1: 1000215216s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start       End         Size        Type      File system     Flags
 1      2048s       1026047s    1024000s    primary   ntfs            boot
 2      1026048s    384187856s  383161809s  primary   ntfs
 3      384188416s  385812479s  1624064s    primary   ntfs            diag
 4      385816574s  746307583s  360491010s  extended
 5      609591296s  648650751s  39059456s   logical   linux-swap(v1)

```
After this i tried running TestDisk. Not iam stucking again. If I run testdisk it will only show me the usb stick (even if it runs as root/sudo).
TestDisk Result
```
TestDisk 6.14-WIP, Data Recovery Utility, September 2012
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


  TestDisk is free software, and
comes with ABSOLUTELY NO WARRANTY.


Select a media (use Arrow keys, then press Enter):
>Disk /dev/sdb - 126 GB / 117 GiB - JetFlash Transcend 128GB


>[Proceed ]  [  Quit  ]


Note: Disk capacity must be correctly detected for a successful recovery.
If a disk listed above has incorrect size, check HD jumper settings, BIOS
detection, and install the latest OS patches and disk drivers.

```

I guess iam doing something wrong. Currently iam trying to follow [this ]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")tutorial for TestDisk. Can you further explain the steps? Maybe i missed something. Iam working on an live KNOPPIX system now, because testdisk was preinstalled.

---

### Post by oldfred on 2017-05-14
Part of issue maybe that you have the new NVMe drive. Testdisk may not be updated to handle those.
It also could be that Knoppix is not updated either. Use Ubuntu live installer.
Many Linux tools are designed to look for all drives, it used to be hda, then sda, but now some are NVMe.

Try parted rescue as it does work with NVMe.

---

### Post by lokin2 on 2017-05-14
Thank you very much. Parted worked.

---

### Post by oldfred on 2017-05-14
Glad that worked.

But if new system, some how you converted drive to MBR(msdos). 
If you reinstalled Windows that would do that as Windows booting in BIOS mode only works from MBR, And Windows in UEFI mode only works from gpt partitioned drives.
And how you boot install media UEFI or BIOS is then how it installs.

I have yet to see lost partition issue with gpt partitioned drives, but Windows often ignores Linux partitions and loses them with MBR.

---

