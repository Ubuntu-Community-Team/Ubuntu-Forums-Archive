---
title: "Deleting ubuntu 12.10 from ssd (dual boot)"
date: 2013-09-13
forum: General Help
---

### Post by edd13 on 2013-09-13
Hi

I am running windows 8 and ubuntu on 2 separate ssds and would like to know how can I get rid of ubuntu completely without any issues.


Thanks

---

### Post by sudodus on 2013-09-13
If there are no secrets on the SSD containing Ubuntu, you can just overwrite it with a new file system (format it).

If you need to wipe the drive to remove any trace of private data, you can use hdparm or DBAN according to this thread[URL="http://ubuntuforums.org/showthread.php?t=2124829"]

best way to wipe a drive[/URL]

---

### Post by edd13 on 2013-09-13
Hi

the thing is both of my OS W8 and ubuntu have problems. at the present moment I can only access ubuntu via live usb and can`t access windows 8. I have another thread opened to try to resolve this other issue but it seems that nobody knows how.

Anyway how can I format the unbunt ssd if my OS state is not working? Does it work through live usb? Any other tool?

Thanks

---

### Post by sudodus on 2013-09-13
Yes, it is a good idea to boot from a live USB drive and use ***gparted*** to manage the partition table and file systems.

Have you got a Windows install disk, or only a preinstalled system with UEFI? Is there a recovery partition or disk for Windows? If not, you need to make Windows available again, and it should be possible after installing Ubuntu and tweaking the boot system (grub) with [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair").

---

### Post by edd13 on 2013-09-13
I have used gparted already and I probablt messed up even more as I don`t really understand linux

I have a w8 install disk and already tried to repair windows but I only get a black screen message saying MISSING OPERATING SYSTEM...don`t understand why

I also have the windows recovery usb stick to recover partitions and boot issues but I still did not figure out how to use and fix all boot issues....would you know?

[COLOR=#000000]This is the BOOT INFO SUMMARY that i have from the live ubuntu usb > [/COLOR][http://paste.ubuntu.com/6102442](http://paste.ubuntu.com/6102442)

I am not sure where the problem is but I am desperate for help...please keep me informed

---

### Post by sudodus on 2013-09-14
This info shows what kind of partition tables you have
```

=================== parted -l:

Model: ATA OCZ-SOLID3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
1      1049kB  4024MB  4023MB  linux-swap(v1)
2      4024MB  46.5GB  42.5GB  ext4
3      46.5GB  119GB   72.5GB  ext4
4      119GB   120GB   1049MB  ext4


Model: ATA OCZ-VERTEX3 MI (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  106MB  105MB  primary  ntfs         boot
2      107MB   120GB  120GB  primary  ntfs


Model: ATA ST1500DL003-9VT1 (scsi)
Disk /dev/sdc: 1500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  106MB   105MB   primary  ntfs         boot
2      106MB   1500GB  1500GB  primary  ntfs


Model: Verbatim STORE N GO (scsi)
Disk /dev/sdd: 7744MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      4129kB  7744MB  7740MB  primary  fat32        boot, lba

```
It seems you have installed Windows 8 to ***/dev/sdb1 ***and*** /dev/sdc1***
```

=================== os-prober:
/dev/sdb1:Windows 8 (loader):Windows:chain
/dev/sdc1:Windows 8 (loader):Windows1:chain

```

but those drives
```

Model: ATA OCZ-VERTEX3 MI (scsi)
Disk /dev/sdb: 120GB

Model: ATA ST1500DL003-9VT1 (scsi)
Disk /dev/sdc: 1500GB

```
have ***MSDOS*** partition tables, which I think is wrong. You need to install Windows 8 to a drive with a ***GPT*** partition table. Only ***/dev/sda*** has GPT.

```
Model: ATA OCZ-SOLID3 (scsi)
Disk /dev/sda: 120GB
```

But this information from ***df*** shows

```
=================== df -Th:
Filesystem     Type       Size  Used Avail Use% Mounted on
...
/dev/sda2      ext4        39G  176M   37G   1% /mnt/boot-sav/sda2
/dev/sda3      ext4        67G  180M   63G   1% /mnt/boot-sav/sda3
/dev/sda4      ext4       985M   18M  918M   2% /mnt/boot-sav/sda4
/dev/sdb1      fuseblk    100M   32M   69M  32% /mnt/boot-sav/sdb1
/dev/sdb2      fuseblk    112G  108M  112G   1% /mnt/boot-sav/sdb2
/dev/sdc1      fuseblk    100M   28M   73M  28% /mnt/boot-sav/sdc1
/dev/sdc2      fuseblk    1.4T  626G  772G  45% /mnt/boot-sav/sdc2

```

and there is very little space used in all mountable partitions except in the last one, ***/dev/sdc2***, so that is the only place there can be an installed operating system. Have you installed Windows 8 to that partition? And have you wiped Windows 8 from ***/dev/sdb***?

So I suggest

1. Save whatever personal files you have in the partition ***/dev/sdc2***, if you intend to use it for an operating system. There are 626G of data. Otherwise (if you want to keep it as a data partition, it would be safer if you unplug that drive from the computer while you install operating systems to the other drives. (Unplug Model: ATA ST1500DL003-9VT1 (scsi), Disk /dev/sdc: 1500GB)

2. Make a GUID partition table and give it a UEFI partition and another small Windows partition at the head of the drive. Try if the Windows 8 install drive will do all this for you. I suppose you want to use ***/dev/sdb*** for this purpose (Model: ATA OCZ-VERTEX3 MI (scsi), Disk /dev/sdb: 120GB).

3. Install Ubuntu into /dev/sda2 (39 GB) or /dev/sda3 (67 GB) or use both, /dev/sda2 for root and /dev/sda3 for home, (Model: ATA OCZ-SOLID3 (scsi), Disk /dev/sda: 120GB).

4. And finally, you might need Boot Repair to fix the booting afterwards. See this link

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Good luck :-)

---

### Post by edd13 on 2013-09-14
Hi Sudodus

It looks like you have been the only one to get all this stuff accurate.
Let me answer and explain your information above:
I have no deleted my w8 nor my ubuntu and I don`t understand why there`s very little space on both ssds. Does it mean they`ve gone and I can`t recover them?
Secondly /dev/sdc2 is my data hd drive where I kept most of my stuff
You are right when saying that I want w8 on the vertex ssd and ubuntu on the other ssd
What do you really mean by creating a GUIG partition and give it a UEFI partition and another small windows partition at the head of the drive? How can I do this? Through gparted or any other partition tool? I have mini partition tool if helps
Will this recover my windows? What about my usb recovery stick that I created prior this problem...can it be used to recover windows?

Please let me know

---

### Post by sudodus on 2013-09-14
> **edd13 said:**
> Hi Sudodus

It looks like you have been the only one to get all this stuff accurate.
Let me answer and explain your information above:
I have no deleted my w8 nor my ubuntu and I don`t understand why there`s very little space on both ssds. Does it mean they`ve gone and I can`t recover them?
I think the installed systems are gone (or were never really installed there), but the SSDs are probably OK. There is little ***used*** space. Most of it is there, waiting to be used :-)
> 
Secondly /dev/sdc2 is my data hd drive where I kept most of my stuff
You are right when saying that I want w8 on the vertex ssd and ubuntu on the other ssd
What do you really mean by creating a GUIG partition and give it a UEFI partition and another small windows partition at the head of the drive? How can I do this? Through gparted or any other partition tool? I have mini partition tool if helps
Will this recover my windows? What about my usb recovery stick that I created prior this problem...can it be used to recover windows?

Please let me know

Since you  have a w8 install disk, I recommend that you use it and let it do all the partitioning and formatting. I think it can, if you allow it to manage the whole drive (let it wipe everything and start from the beginning).

Edit: Disconnect the data drive before the installation.

---

### Post by edd13 on 2013-09-20
Hi

Took a different approach and installed w8 on the ssd where ubuntu was installed. Lost all my files though....at least my pc is running

Thanks

---

