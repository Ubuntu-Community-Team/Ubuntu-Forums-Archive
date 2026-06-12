---
title: "Windows or Ubuntu partitions?"
date: 2015-08-24
forum: General Help
---

### Post by darrenrmoss on 2015-08-24
Hi. Can anyone tell me which on this list are ubuntu partitions? I'm using windows 8.1 - accidentally formatted ubuntu partition from windows explorer - Im dont want to fix this, just want rid of the ubuntu partitions. Will reinstall ubuntu after upgrade to windows 10. Cheers!

Sorry - abandoning post - pasted screendump never shows up in post.

---

### Post by Bashing-om on 2015-08-24
darrenrmoss; Hello;

Your screenshot did not take.
However, the information you seek will be provided by the terminal command:
```

sudo parted -l

```
IF there are ubuntu partitions, they will be marked as 'ext4' - on a default ubuntu install - under the "file system" heading.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by darrenrmoss on 2015-08-24
Hi. Thanks for fast reply. I will try running ubuntu from usb and then try your suggestion. ANy idea how to do the equivelent from windows? Thanks.

---

### Post by Bashing-om on 2015-08-24
darrenrmoss; Hey;

Nope, I am Windows illiterate; cannot help you there.

What is the problem you are addressing, perhaps we can help resolve it ? A booting issue ? 

[INDENT][INDENT]we do try and help
[/INDENT][/INDENT]

---

### Post by v3.xx on 2015-08-24
> **darrenrmoss said:**
> ANy idea how to do the equivelent from windows? Thanks.

Your windows partition manager should do the same

---

### Post by yancek on 2015-08-24
> I will try running ubuntu from usb and then try your suggestion. ANy idea how to do the equivelent from windows? Thanks. 				

The command suggested won't "do" anything other than output information on drives/partitions.  You should be able to use Disk Management in windows to delete partitions or format them for use with windows.  You can't format them for any Linux filesystem from windows as a default windows system won't recognize/read or write to a Linux partition.

---

### Post by ajgreeny on 2015-08-24
The problem with Disk-management in Windows is that it will report Linux partitions (usually) as healthy partitions but give you no more information than that as Windows is unable to read or do anything except see that they are present on disk.  There may be third-party partition managers that can tell you everything needed, but I am another Windows illiterate Ubuntu user so I do not know what they might be.

---

### Post by darrenrmoss on 2015-08-26
Hi all! Thanks for your help. How do I insert a screen dump image? I cant get it to work!

---

### Post by darrenrmoss on 2015-08-26
Okay, I'll type it in..   AOMEI Partition Assistant shows:

Partition           File system   Capacity      Used space    Free space   Flag           Status
*: SYSTEM       FAT32          300.00MB    57.26MB        242.74MB     GPT,EFI     System
*: Recovery     NTFS            600.00MB    327.88MB      272.12MB     GPT,WRE   None
*:                   Other            128.00MB   0.00KB           128.00MB     GPT,MSR   None
C: OS              NTFS            137.13GB    75.30GB        61.84GB       GPT           Boot
*:                   NTFS            350.00MB    284.48MB      65.52MB       GPT,WRE    None
F:                   NTFS             48.83GB     93.30MB        48.74GB       GPT           None
D: Data           NTFS            258.44GB    171.47GB       86.9GB        GPT           None
*: Restore       NTFS            20.01GB      10.12GB        9.89GB         GPT,WRE    None

Obviously C, D and F are windows. Which out of "Recovery" and "Restore" are windows? And the 2 unlabelled ones?

THanks!

---

### Post by ajgreeny on 2015-08-26
> **darrenrmoss said:**
> Okay, I'll type it in..   AOMEI Partition Assistant shows:

Partition           File system   Capacity      Used space    Free space   Flag           Status
*: SYSTEM       FAT32          300.00MB    57.26MB        242.74MB     GPT,EFI     System
*: Recovery     NTFS            600.00MB    327.88MB      272.12MB     GPT,WRE   None
*:                   Other            128.00MB   0.00KB           128.00MB     GPT,MSR   None
C: OS              NTFS            137.13GB    75.30GB        61.84GB       GPT           Boot
*:                   NTFS            350.00MB    284.48MB      65.52MB       GPT,WRE    None
F:                   NTFS             48.83GB     93.30MB        48.74GB       GPT           None
D: Data           NTFS            258.44GB    171.47GB       86.9GB        GPT           None
*: Restore       NTFS            20.01GB      10.12GB        9.89GB         GPT,WRE    None

Obviously C, D and F are windows. Which out of "Recovery" and "Restore" are windows? And the 2 unlabelled ones?

THanks!
Sorry, but I and many other users will probably not be able to help with much explanation of that output in a Windows utility.

It would be much more helpful to boot to a live Ubuntu system and post back here, in code tags, the output of ```
sudo parted -l
```
There is, however, only one very small (128MB) partition, the third in the list, which is not NTFS or FAT32 so that is one which could be the Linux partition, even though it is too small to be very useful, but I would suggest you do more investigating before you do anything more to it, just in case I am wrong about this and it is a needed Windows partition.

---

### Post by darrenrmoss on 2015-08-26
Okay. Will do. Thanks.

---

### Post by darrenrmoss on 2015-08-26
I can't get sudo parted - l to work - it says Error could not stat device - - no such file or directory. Am I missing something?

Gparted shows:

Partition file system mount point label size used unused flags
/dev/sda1 fat32 [blank] 300.00MiB 57.26MiB 272.74MiB boot
/dev/sda2 ntfs [blank] recovery 600.00MiB 327.89MiB 272.11MiB hidden, diag
/dev/sda3 ! unknown [blank] [blank] 128.00MiB - - msftres
/dev/sda4 ntfs /media/ubuntu/OS OS 137.13GiB 75.47GiB 61.66GiB msftdata
/dev/sda5 ntfs [blank] [blank] 350MiB 284.48MiB 65.52MiB hidden, diag
/dev/sda6 ntfs /media/ubuntu/F4E48D1AE48CE06A [blank] 48.83GiB 93.31MiB 48.74GiB msftdata
unallocated unallocated [blank] [blank] 1.00MiB -  -  [blank]
/dev/sda7 ntfs /media/ubuntu/Data Data 258.44GiB 171.47GiB 96.97GiB msftdata
/dev/sda8 ntfs [blank] Restore 20.01GiB 10.12GiB 9.89GiB hidden,diag

---

### Post by oldfred on 2015-08-26
Both Windows & Vendor may call partitions recovery. One was the Windows repair console and the other was the vendor image of the drive as new. Both Windows & vendor recovery disks or flash drives should be created as if hard drive fails how are you going to recover to a new drive?

The 128MB msftres is required by Windows. It is unformatted, so partition tools may complain as they cannot see the format.
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

The 1MB partition may be a bios_grub partition? It also must be unformatted.
That is for installing grub to the gpt partitioned drive's protective MBR for BIOS booting. 
But you should be installing Ubuntu in UEFI boot mode and then would not have a bios_grub.


 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

---

