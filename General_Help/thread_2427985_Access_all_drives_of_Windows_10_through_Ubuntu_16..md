---
title: "Access all drives of Windows 10 through Ubuntu 16.04"
date: 2019-09-28
forum: General Help
---

### Post by GirishSharma on 2019-09-28
Hello,

I have one PC in my office.  It came with pre-installed Windows 10 with one HDD.  To install Ubuntu, I made a partition and installed Ubuntu 16.04 on it.  All works fine.

Now, I want to access Windows 10 drives C: and D: in Ubuntu.  At this moment, I don't have access to the PC so, I can't give you outputs of :

sudo blkid
sudo fdsik -l

but, when I says :

sudo mount /dev/sda6 /media/win

It works fine (earlier, I shudtown /s in windows for avoid hibernation issue), but It just shows me two folders :

1.Recovery
2.System Volume Information

in /media/win mount point.  I don't know, how do I access complete C: and D: in ubuntu.

Kindly help me.

PS : Due to security reasons, I don't have internet access on the office PC so, I can't apt-get install on it.

---

### Post by The Cog on 2019-09-28
You really need to identify the right partitions to mount.
There's no lsblkid command - try this instead - should help:
```
lsblk -o name,size,type,fstype,mountpoint
```

---

### Post by yancek on 2019-09-28
The use of "C:\" on windows usually refers to the drive/partition on which the OS is installed.  With the microsoft naming conventions on windows, D on the other hand, can be another partition on the same drive, another partition on a separate drive or a CD/DVD drive.  If you have two windows partitions you will need to mount both partitions.  The command you posted mounts one.  Have you tried creating mount point for both and mounting both?  Have you looked under /media/username for a UUID for the windows partitons?

> t works fine (earlier, I shudtown /s in windows for avoid hibernation issue), but It just shows me two folders :


I'm not sure what your point is here.  Did it show the expected files as you seem to indicate earlier or was this with some other attempt?

---

### Post by GirishSharma on 2019-09-28
I am thankful to both of you. As I requested above, I don't have access to my office PC right now, so I think its better to post the output of above two commands i.e. blkid and fdisk, then only we can come to solution.

I don't know which /dev/sda[N] have windows installation, but when I says mount /dev/sda6, it mounts but just opens Recovery and System Volume Information in the mount location.

---

### Post by GirishSharma on 2019-09-28
These are required outputs :

```

girish@girish-OptiPlex-3050:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial


girish@girish-OptiPlex-3050:~$ lsblk -o name,size,type,fstype,mountpoint
NAME     SIZE TYPE FSTYPE MOUNTPOINT
sdb      7.6G disk        
&#9492;&#9472;sdb1   7.6G part vfat   /media/girish/Girish
sr0     1024M rom         
sda    931.5G disk        
&#9500;&#9472;sda4   2.9G part swap   [SWAP]
&#9500;&#9472;sda2   128M part        
&#9500;&#9472;sda5   7.1G part ext4   /
&#9500;&#9472;sda3 919.8G part        
&#9500;&#9472;sda1   650M part vfat   /boot/efi
&#9492;&#9472;sda6   990M part ntfs   


girish@girish-OptiPlex-3050:~$ sudo blkid
/dev/sda1: LABEL="ESP" UUID="BAE9-4ADF" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="0ab58319-d42a-4a79-8852-3ee99179129b"
/dev/sda2: PARTLABEL="Microsoft reserved partition" PARTUUID="1d1844e9-56d3-4873-b7d4-b0a6f17cf0a8"
/dev/sda3: PARTLABEL="Basic data partition" PARTUUID="b6e4a31c-a1ad-47cd-a786-2062db9b2eb7"
/dev/sda4: UUID="ebf5074c-d7d9-4bc9-8ab7-d4e0eda4c2bb" TYPE="swap" PARTUUID="b9aca77d-e580-487c-8167-707f3f8c4875"
/dev/sda5: UUID="aa1787c1-0544-4957-8055-08a746f5bf8a" TYPE="ext4" PARTUUID="d1e8acb0-43a5-40e5-99aa-d5fa8b91062d"
/dev/sda6: LABEL="WINRETOOLS" UUID="9CA08935A0891744" TYPE="ntfs" PARTUUID="ae60c659-3fb0-46dd-96a5-aa6953b29589"


girish@girish-OptiPlex-3050:~$ sudo fdisk -l
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: E1D206C6-CD80-4796-8691-87310D959375


Device          Start        End    Sectors   Size Type
/dev/sda1        2048    1333247    1331200   650M EFI System
/dev/sda2     1333248    1595391     262144   128M Microsoft reserved
/dev/sda3     1595392 1930500095 1928904704 919.8G Microsoft basic data
/dev/sda4  1930500096 1936500735    6000640   2.9G Linux swap
/dev/sda5  1936500736 1951471615   14970880   7.1G Linux filesystem
/dev/sda6  1951471616 1953499135    2027520   990M Windows recovery environment


girish@girish-OptiPlex-3050:~$ sudo mount /dev/sda6 /media/win
girish@girish-OptiPlex-3050:~$ ls /media/win
recovery  System Volume Information
girish@girish-OptiPlex-3050:~$ 

```

---

### Post by TheFu on 2019-09-28
Assuming /media/win isn't mounted, it looks like you really want:
**sudo mount /dev/sda3 /media/win**

Hibernation is just 1 of the issues with Windows10 and partitions. Fastboot must also be disabled. Sometimes it is called "Fast Startup." Disabling those happens inside Windows.

The Cog, I'm going to make that my default ```
alias  lsblk='lsblk -o name,size,type,fstype,mountpoint'
```
Just too useful NOT to have it.

---

### Post by GirishSharma on 2019-09-28
> **TheFu said:**
> Assuming /media/win isn't mounted, it looks like you really want:
**sudo mount /dev/sda3 /media/win**

Hibernation is just 1 of the issues with Windows10 and partitions. Fastboot must also be disabled. Sometimes it is called "Fast Startup." Disabling those happens inside Windows.

The Cog, I'm going to make that my default ```
alias  lsblk='lsblk -o name,size,type,fstype,mountpoint'
```
Just too useful NOT to have it.

Thanks for your reply. Do you mean I need to mount /dev/sda3 ?  Actually, its too late, my peers in office have left the office, so I will test the command tomorrow.

For hibernation, last time I said shutdown /s when I was switching off the windows, so I think windows have shutdown not hibernated.

---

### Post by Autodave on 2019-09-28
*Fastboot* is normally turned off in the BIOS.  Access the BIOS and untick it.

---

### Post by TheFu on 2019-09-28
> **Autodave said:**
> *Fastboot* is normally turned off in the BIOS.  Access the BIOS and untick it.

[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup) is what I attempted to say. It is settings controlled by Windows that leaves the file systems open between reboots.  It isn't the power-standby or hibernation. On a computer with windows only, it will make booting faster, since it skips any file system checks for consistency.  Whether that is ever actually a good idea is something MSFT can debate.

---

### Post by yancek on 2019-09-28
> Thanks for your reply. Do you mean I need to mount /dev/sda3 ? 

That would make sense as that windows partition takes up almost the entire drive (almost 920 of 931GB)  and the other partitions are Recovery and reserved and there is really no reason for you to access them.
Also, your Ubuntu is not going to work 'fine' for very long as you have it on a very small partition (7.1GB) and it will soon fill up and become unbootable.

---

### Post by TheFu on 2019-09-28
Of course, if you want it to be available always, at boot, inside Linux, then using the fstab to configure that would make sense. I don't dual boot, so I would never use the fstab for NTFS partitions, but many people do.  

There are some specific mount options to make NTFS access a little safer and faster.  They can be used in a mount command, the fstab or if you use autofs.  Basically, any real mount that doesn't use a GUI.

---

### Post by GirishSharma on 2019-10-02
> **TheFu said:**
> Assuming /media/win isn't mounted, it looks like you really want:
**sudo mount /dev/sda3 /media/win**

Hibernation is just 1 of the issues with Windows10 and partitions. Fastboot must also be disabled. Sometimes it is called "Fast Startup." Disabling those happens inside Windows.

The Cog, I'm going to make that my default ```
alias  lsblk='lsblk -o name,size,type,fstype,mountpoint'
```
Just too useful NOT to have it.

I am sorry for late reply.

When I says sudo mount /deve/sda3 /media/win i gets :

```

girish@girish-OptiPlex-3050:~$ sudo mount /dev/sda3 /media/win
[sudo] password for girish: 
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.
girish@girish-OptiPlex-3050:~$ 

```

In windows I have C:\ and D:\ drives. I don't know what I am missing.

---

### Post by TheFu on 2019-10-02
Windows calls things "drives" that aren't really "drives", they are partitions.
```
Device          Start        End    Sectors   Size Type
/dev/sda1        2048    1333247    1331200   650M EFI System
/dev/sda2     1333248    1595391     262144   128M Microsoft reserved
/dev/sda3     1595392 1930500095 1928904704 **919.8G** Microsoft basic data
/dev/sda4  1930500096 1936500735    6000640   2.9G Linux swap
/dev/sda5  1936500736 1951471615   14970880   7.1G Linux filesystem
/dev/sda6  1951471616 1953499135    2027520   990M Windows recovery environment

$ lsblk -o name,size,type,fstype,mountpoint
NAME     SIZE TYPE FSTYPE MOUNTPOINT
sdb      7.6G disk        
&#9492;&#9472;sdb1   7.6G part vfat   /media/girish/Girish
sr0     1024M rom         
sda    931.5G disk        
&#9500;&#9472;sda4   2.9G part swap   [SWAP]
&#9500;&#9472;sda2   128M part        
&#9500;&#9472;sda5   7.1G part ext4   /
&#9500;&#9472;sda3 919.8G part        
&#9500;&#9472;sda1   650M part vfat   /boot/efi
&#9492;&#9472;sda6   990M part ntfs
```
Shows us the 2 disks in the system.
sdb is probably an 8GB flash drive.
sda is a 1tb spinning disk with a number of partitions.  sda6 is less than 1G in size.  sda3 is over 900G in size, but somehow it doesn't have a file system found on it.  I don't know how that might have happened.  The drive is GPT, so there won't be any extended partitions, which simplifies things.

So, assuming sda3 really is NTFS, the fdisk output implies that, then that file system just needs to be fixed from a Windows machine. Until that is handled, I don't think Linux will be able to access it.  It could be hibernation. It could be fast startup or it could be data corruption.  Linux cannot fix any of those for NTFS. Sorry.

---

### Post by GirishSharma on 2019-10-02
Thank you once again for your quick reply.  I ran below commands, kindly look on them :

```

girish@girish-OptiPlex-3050:~$ sudo mount -t ntfs /dev/sda3 /media/win
[sudo] password for girish: 
NTFS signature is missing.
Failed to mount '/dev/sda3': Invalid argument
The device '/dev/sda3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
girish@girish-OptiPlex-3050:~$ 




girish@girish-OptiPlex-3050:~$ sudo file -s /dev/sda3
/dev/sda3: DOS/MBR boot sector, code offset 0x58+2, OEM-ID "-FVE-FS-", sectors/cluster 8, reserved sectors 0, Media descriptor 0xf8, sectors/track 63, heads 255, hidden sectors 1595392, FAT (32 bit), sectors/FAT 8160, serial number 0x0, unlabeled; NTFS, sectors/track 63, physical drive 0x1fe0, $MFT start cluster 393217, serial number 02020454d414e204f, checksum 0x41462020
girish@girish-OptiPlex-3050:~$ 


girish@girish-OptiPlex-3050:~$ sudo ntfsfix /dev/sda3
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.
girish@girish-OptiPlex-3050:~$ 

```

I have done chkdsk /f but still not able to mount the /dev/sda3. When I ran chkdsk c: it said me it is having NTFS File System. For hibernation issue, I said shutdown /s when I was switching off the windows.

---

### Post by TheFu on 2019-10-02
Here's what I wrote yesterday:
> **TheFu said:**
>  
So, assuming sda3 really is NTFS, the fdisk output implies that, then that file system just **needs to be fixed from a Windows machine**. Until that is handled, I don't think Linux will be able to access it.  It could be hibernation. It could be **fast startup** or it could be **data corruption**.  Linux cannot fix any of those for NTFS. Sorry.

I have no idea what shutdown /s does.   Did you fix any fast startup issues?
I have no other suggestions. Sorry.

---

### Post by cmcanulty on 2019-10-02
One thing that cause this: if you restart windows and go to ubuntu windows drive won't mount. If you do a shutdown and then boot to ubuntu the drive will mount (usually anyway)

---

### Post by GirishSharma on 2019-10-03
Problem Solved...!!

I just disabled Bitlocker in windows and all went fine.  I started with googling mount Windows Basic Data partition in ubuntu and found a link which suggested to disable the bitlocker and this solved my issue.

I am thankful to you for your continue support and helpful replies.

---

### Post by dragonfly41 on 2019-10-03
Now go to Thread Tools at top of this page and mark the issue as "solved".

---

### Post by GirishSharma on 2019-10-03
Already Done..!!

---

