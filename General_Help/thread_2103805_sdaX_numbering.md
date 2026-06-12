---
title: "sdaX numbering"
date: 2013-01-11
forum: General Help
---

### Post by geohei on 2013-01-11
Hi.

Let's assume a HDD with GPT (as opposed to MBR).

I have the following partitions (fs doesn't matter).
sda1, sda2, sda3, sda4

Now I delete sda1 with a Live CD.
For some reason, sda2 is all of a sudden called sda1, while sda3 and sda4 keep their name.

I noticed all this when performing an image backup of sda1 with subsequent restore of sda1 (restoring first deletes the partition). sda1 is/was the EFI partition on my HDD (100 MB). The image backup was done with Acronis True Image 2013.

Question: Where are the sdaX numbers stored? In the GPT? They must be saved somewhere OS independant since UEFI needs to know the sdaX number for UEFI boot managing.

Thanks,

---

### Post by dino99 on 2013-01-11
sorry i cant directly answer to your question: it might be better to ask devs on askubuntu.

its quite disturbing to see some partition number scaled while some others are not; i've always seen that issue and it can be called a bug.

---

### Post by geohei on 2013-01-13
Further tests revealed the following (all on above mentioned GPT HDD):

```
sda1 fat32 efi
sda2       msftres (Windows MSR partition)
sda3 ntfs  Windows 7
sda4 ext4  Ubuntu 12.10
sda5 swap
```

sda1,2,3 are for Windows 7
sda1,4,5 are for Ubuntu 12.10

I'm looking for an image backup solution and (initially) elected Acronis True Image Home 2013 (ATIH 2013), whic is supposed to handle GPT HDDs and ext4. So all should (!) be fine.

The backup works fine for sda1,3,4,5 (ATIH dopesn't see sda2. sda5 is not necessary to backup, but I did it just for testing purpose).

Restore of sda3,4 works fine. sdaX as mentioned above numering is respected.

However when I restore sda1, I get the following:
```

sda2 fat32 efi
sda1       msftres (Windows MSR partition)
sda3 ntfs  Windows 7
sda4 ext4  Ubuntu 12.10
sda5 swap
```

sda1,2 are swapped.

Until today, I thought that the numbering is always according to the physical position on the HDD, but this seems to be wrong. The numbering must be stored somewhere. I need to know where and correct the swap of sda1,2 before proceeding. It messes up my UEFI NVRAM Boot Manager settings.

So ... where are the partition numbers stored?

Thanks,

---

### Post by bab1 on 2013-01-13
> **geohei said:**
> Until today, I thought that the numbering is always according to the physical position on the HDD, but this seems to be wrong. The numbering must be stored somewhere. I need to know where and correct the swap of sda1,2 before proceeding. It messes up my UEFI NVRAM Boot Manager settings.

So ... where are the partition numbers stored?

Thanks,
The device numbers are determined at boot time (as they are enumerated (they are stored as udev rules).  They will always change based on what is on the bus at the time of boot (as you found out).  You should use the UUID as that is unique to the partition or a LABEL that you give the partition.  See the header of the /etc/fstab below```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; **[COLOR="Red"]this may be used with UUID= as a more robust way to name[/color]**
# [COLOR="Red"]**devices that works even if disks are added and removed**[/COLOR]. See fstab(5).#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
**[COLOR="Red"]UUID=fb80eecb-e0cf-49a2-9936-6e219d09a7e1[/COLOR]** /   ext3    errors=remount-ro 0       1

```

---

### Post by geohei on 2013-01-13
> **bab1 said:**
> The device numbers are determined at boot time (as they are enumerated (they are stored as udev rules).  They will always change based on what is on the bus at the time of boot (as you found out).
You talk about device numbers.
I was asking about partition numbers.
These don't seem to be allocated at boot time, do they?

Thanks,

---

### Post by bab1 on 2013-01-13
> **geohei said:**
> You talk about device numbers.
I was asking about partition numbers.
These don't seem to be allocated at boot time, do they?

Thanks,
The device is sda the partition is sda1.  Yes the sda1 is allocated (enumerated) at boot time.  If the device sda becames sdb the first partition on sda (sda1) becomes sdb2.

---

### Post by geohei on 2013-01-13
> **bab1 said:**
> The device is sda the partition is sda1.  Yes the sda1 is allocated (enumerated) at boot time.  If the device sda becames sdb the first partition on sda (sda1) becomes sdb2.
I only have one disk inside this (test) machine, so no sdbX, only sdaX

If I got it right, then sdaX should be sequenced for 1 to 5 (in my example) at boot time. I thought the same until now, but ...

... how do you then explain that the order of the second code block in article #3 above is sda2,1,3,4,5?

Could it be that the boot time assignments of partition numbers only applies to MBR (wild guess from my side)?

---

### Post by bab1 on 2013-01-13
```

```> **geohei said:**
> I only have one disk inside this (test) machine, so no sdbX, only sdaX

If I got it right, then sdaX should be sequenced for 1 to 5 (in my example) at boot time. I thought the same until now, but ...

... how do you then explain that the order of the second code block in article #3 above is sda2,1,3,4,5?

Could it be that the boot time assignments of partition numbers only applies to MBR (wild guess from my side)?

It may be the MBR issue, but then again it may not.  I do know that the way to correct the problem is to follow the advice provided in the /etc/fstab file.  Anything else is just "navel gazing"; providing a lot of lint but nothing of any substance.  ;-)

[COLOR="Blue"]Edit:  The partition UUID numbers are part of the partition meta data.  You can see them with this command[/COLOR]```
sudo blkid -c /dev/null -o list
```

---

### Post by geohei on 2013-01-13
> **bab1 said:**
> 
It may be the MBR issue, but then again it may not.  I do know that the way to correct the problem is to follow the advice provided in the /etc/fstab file.  Anything else is just "navel gazing"; providing a lot of lint but nothing of any substance.  ;-)
If you suggest to edit /etc/fstab, this assumes that an OS runs from the HDD (in my case sda4, Ubuntu 12.10). Changing /etc/fstab of a Live CD would only be temporary.

I believe that the partition numbering is stored somewhere outside the OS, because ...

1. An Ubuntu Live CD (GParted) initially showed sda1,2,3,4,5, which was right after the installation. After the restore of sda1 (see above), sda1,2 were swapped. This was confirmed by the Live CD.
2. UEFI Boot Manager relies on EFI partition being sda1. After sda1 went sda2, I couldn't boot anything anymore, which is logical!

So ... editing /etc/fstab in Ubuntu 12.10 (the one installed on /etc/fstab) doesn't change anything to the partition numbering stored outside the OS (Windows, Ubuntu, ... any OS).

UEFI uses the /dev/sdaX scheme to address the partitions (also UUID, but first I'd like to know where the sdaX numbers are stored).

... later ...

I found a solution now ...

gdisk, p, s, p, w
This sorts the partitions and reassigns sdaX numbers.

```
ubuntu@ubuntu:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 51A46A20-01F1-47E2-BAD7-AC8272BEC91D
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 991786349 sectors (472.9 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1          206848          468991   128.0 MiB   0700  
   2            2048          206847   100.0 MiB   EF00  
   3          468992       210184191   100.0 GiB   0700  
   4       210184192       315041791   50.0 GiB    0700  
   5       315041792       359020543   21.0 GiB    8200  
   6      1350803456      1656948735   146.0 GiB   0700  
   7      1656948736      1953523711   141.4 GiB   0700  

Command (? for help): s
You may need to edit /etc/fstab and/or your boot loader configuration!

Command (? for help): p
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 51A46A20-01F1-47E2-BAD7-AC8272BEC91D
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 991786349 sectors (472.9 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  
   2          206848          468991   128.0 MiB   0700  
   3          468992       210184191   100.0 GiB   0700  
   4       210184192       315041791   50.0 GiB    0700  
   5       315041792       359020543   21.0 GiB    8200  
   6      1350803456      1656948735   146.0 GiB   0700  
   7      1656948736      1953523711   141.4 GiB   0700  

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sda.
Warning: The kernel is still using the old partition table.
The new table will be used at the next reboot.
The operation has completed successfully.
```

That's it!

Now ... it would be useful to have a tool to backup and restore the GPT! ?!

Thanks,

---

### Post by oldfred on 2013-01-13
Systems do not necessarily see partitions like the MSR, swap or bios_grub. These are unformatted and used more a scratch pads for software just to directly write into. But systems will require these partitions.

gpt has more internal structures. The efi partition is really ef00 in gpt or a long GUID.

       Windows 8 UEFI requirements:
If Windows RE is on the system partition, the size is 350 MB. If it's not the system partition, then
it's 300 MB. This is assuming MBR layout. (For GPT, Windows RE is always separate from the
ESP, hence 300 MB.)
            Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Has info on GUIDs
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by geohei on 2013-01-13
Thanks, but the ?s remain.

1. Where are the partition numbers stored? GPT?
2. Can I change them as I wish (like gdisk can sort them)? If yes, how?
3. Can I backup/restore the GPT (i.e. HDD structure)?

---

### Post by Yellow Pasque on 2013-01-13
> **geohei said:**
> 1. Where are the partition numbers stored? GPT?
They're (assuming you mean /dev/sda#) not stored. udev decides them at boot and how it does so is not always consistent to us humanoids, which is why you use UUID's as suggested.
> 2. Can I change them as I wish (like gdisk can sort them)? If yes, how?
You can dive into the murky waters of writing udev rules (have fun with that..).

---

### Post by geohei on 2013-01-14
> **Temüjin said:**
> They're (assuming you mean /dev/sda#) ...
Yes, I meant /dev/sda#.

> **Temüjin said:**
> ... not stored. udev decides them at boot and how it does so is not always consistent to us humanoids, which is why you use UUID's as suggested.
Are you sure about that?
The reason I have my doubts is, that EFI knows already about the number (see previous articles in this thread). This would mean they are stored outside an OS. udev would mean that Ubuntu starts to assign them while booting, right?

However ... after sda1/2 was swapped (see above), EFI, Live CD Ubuntu and installed Ubuntu recognized the partitions as sda2 for the first partition (efi) and sda1 as second partition (msftres). How do you explain this?

Could it be that udev only applies for != GPT HDDs (= MBR HDDs)?

Would you like to see a screenshot of the sda1/2 swap (GParted from Live CD)?

---

### Post by geohei on 2013-01-25
To complete/finish this thread ...

1. The sda# numbers are in fact not stored. The partition data is stored in the GPT. Every partition has a fix position. The GPT can hold up to 128 positions (expandable). The number sda# is derived from the number of the position inside the GPT. Let's say, if position 4 is the Ubuntu 12.10 ext4 partition, this will be then sda4, _independently whether partitions in positions 1, 2 or 3 exist_. This explains the gaps which sometimes occur in the sda# numbering, id est why you can delete e.g. sda3 and sda4 will still be called sda4 later on. This behavior seems to be fundamentally different as for the MBR.

2. The previously mentioned sda1/2 swap was created by Acronis True Image Home 2013. For some reason, this software rearranges the positions inside the GPT. I don't see any logical reason for this. It created quite a mess. Therefore I will not use this software anymore but Macrium Reflect 5.1 buld 5529 instead (Boot CD), which, until now, seems to work reliably.

A good link can be found here (german):
[HDD GPT Daten]("http://forum.chip.de/linux/hdd-gpt-daten-1703601.html")

Thanks for all the help.

---

