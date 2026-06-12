---
title: "Problem with ntfs partition (14.04)"
date: 2018-01-20
forum: General Help
---

### Post by Robbyx on 2018-01-20
Fstab has an entry in it:
...
# /dev/sda6:ntfs partition 
UUID=66F914EF0613BAF3 /media/data ntfs defaults 0 2 

When the computer is rebooted the error message is:
[I]Error occurred while mounting /media/data
press F to skip
Press N for manual recovery
[/I]
Having skipped, I run in terminal 
Sudo ntfsfix  /dev/sda6
This shows no error messages but reports mounting has succeeded..
Sudo ntfsfix -b -d  /dev/sda6 
Reports no errors

Running:
Sudo ntfsfix -b -d   /media/data
Error message:
[I]Mounting volume ... error opening "/media/data": is a directory. Failed attempting to correct error
...
Volume is corrupt. Run chkdsk
[/I]
This makes me assume that the partition has not been mounted into /media/data. 

I do not know what I should do next. 

Could I please have some guidance?

---

### Post by oldfred on 2018-01-20
Umm, run chkdsk?
But you can only do that from Windows or a Windows repair disk.
Actually ntfsfix turns on the chkdsk needed flag, so Windows will run chkdsk on reboot. But then you cannot mount from Linux as it will not mount damaged (chkdsk needed) NTFS partitions.
If also running Windows 8 or 10 make sure fast start up/hibernation is off. Windows updates will turn that back on, so even if you turned it off before, it may be back on.

---

### Post by Robbyx on 2018-01-20
> **oldfred said:**
> Umm, run chkdsk?
But you can only do that from Windows or a Windows repair disk.
Actually ntfsfix turns on the chkdsk needed flag, so Windows will run chkdsk on reboot. But then you cannot mount from Linux as it will not mount damaged (chkdsk needed) NTFS partitions.
If also running Windows 8 or 10 make sure fast start up/hibernation is off. Windows updates will turn that back on, so even if you turned it off before, it may be back on.
Windows is not available on the machine and is not being run there. 
The chkdsk message was in an error message generated when ubuntu was running.
The ntfs partition is required to be used by Ubuntu not Windows.
The problems I described related to Ubuntu not loading the ntfs partition. Windows only comes into the message by way of the error message you picked up.
I would have expected the partition to load if ntfsfix passed it as ok.
What have I wrongly set up?

---

### Post by yancek on 2018-01-20
If you don't have/use windows, why have a proprietary windows filesystem on the partition?
ntfsfix can repair minor problems (sometimes) on ntfs filesystems but if there is a problem more serious, it won't be able to repair it an you will need to run chkdsk which is only available in windows.

> The ntfs partition is required to be used by Ubuntu not Windows.

You might need to explain that.  No Linux system 'requires' any windows filesystem.

---

### Post by Robbyx on 2018-01-20
I require it because it has information on it that is needed.
Could you please look over my settings in the first post and see if you can spot a cause that is leading to the failure to load?

---

### Post by Yellow Pasque on 2018-01-20
First, make sure you have the correct UUID:
```
sudo blkid
```

> **Robbyx said:**
> 
Running:
Sudo ntfsfix -b -d   /media/data
Error message:
[I]Mounting volume ... error opening "/media/data": is a directory. Failed attempting to correct error
...
Volume is corrupt. Run chkdsk
[/I]
This makes me assume that the partition has not been mounted into /media/data. 

You're not using the command correctly there, so ignore that error (garbage in, garbage out). Your first example (using /dev/sda6) was correct. If ntfsfix reports the volume mounted, you should check mount:
```
sudo mount
```
If not mounted, what happens when you try and mount it manually?
```
sudo mount -v /dev/sda6
```

---

### Post by oldfred on 2018-01-20
If you have another Windows machine, make a Windows repair/recovery disk.
Then use that to run chkdsk on your partition.
You often have to run chkdsk multiple times to clear all issues. Usually 3 times.

---

### Post by Robbyx on 2018-01-21
Posted in error see subsequent

---

### Post by Robbyx on 2018-01-21
See comments at *** below
> **Temüjin said:**
> First, make sure you have the correct UUID:
```
sudo blkid
```
[SIZE=5][FONT=Franklin Gothic Medium][/FONT][/SIZE]
***The uuid in fstab is correct
[FONT=Arial][/FONT]
 If ntfsfix reports the volume mounted, you should check mount:
*** ntfsfix /dev/sda6 
*** mounted Vol  ok, (all checks ok)
```
sudo mount
```
If not mounted, what happens when you try and mount it manually?
```
sudo mount -v /dev/sda6
```
*** ntfs_attr_pread_i: ntfs_pread failed
     i/o error failed to read ntfs$bitmap
     ntfs is either inconsistent or there is a hardward fault

As I do not have access to a windows machine to create a bootdisk with chkdsk. do  you agree that I could try TestDisk next see [https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)
I found out about it at [https://linuxacademy.com/blog/linux/ntfs-partition-repair-and-recovery-in-linux/](https://linuxacademy.com/blog/linux/ntfs-partition-repair-and-recovery-in-linux/)
> Deeper Dive
Unfortunately, not everything can be fixed quickly. In fact, there are a very large number of very expensive disk recovery software (often under the category of &#8220;disk forensics&#8221; since they are employed by investigators when sifting through damaged drives) for fixing drives that power up but won&#8217;t boot or provide file system access.

There is a fantastic, and free, utility (and fully bootable rescue CD if it is inside your local computer) for recovering your Windows NTFS partition (and it can do EXT2/3/4, FAT/FAT32/exFAT, HFS and SunFS filesystems too). This utility is called TestDisk and is available in Debian 

---

### Post by Yellow Pasque on 2018-01-21
I don't think testdisk is a full substitute for chkdsk. testdisk will fix problems with the partition table.

Isn't it possible to put windows 10 install media on a USB and run chkdsk from there?

---

### Post by Holger_Gehrke on 2018-01-21
Testdisk is probably not useful in this situation. It can reconstruct broken partition tables or boot sectors but broken logical NTFS structures are simply not it's job. Photorec might be able to copy the files you need off the disk (or it might not; Photorec tries to find files without depending on the logical structures of the file systems; a file that is fragmented will probably not be recoverable with photorec), but the right tools for working with a filesystem created by Microsoft for Microsoft's Operating Systems run on Windows. NTFS is very much a second class citizen in the Linux world, you can create, read and write it but there are no tools to check or repair NTFS. 

Holger

---

### Post by Robbyx on 2018-01-21
> **Temüjin said:**
> I don't think testdisk is a full substitute for chkdsk. testdisk will fix problems with the partition table.

Isn't it possible to put windows 10 install media on a USB and run chkdsk from there?

My sister has a window 8 machine so I realise I could use  her computer. In view of the last two comments I will not use testdisk but will proceed with chkdsk.

I thank all of you who tried to help me.

---

### Post by Robbyx on 2018-01-21
This link talks about making a recover disk/ drive:
[https://www.howtogeek.com/131907/how-to-create-and-use-a-recovery-drive-or-system-repair-disc-in-windows-8/](https://www.howtogeek.com/131907/how-to-create-and-use-a-recovery-drive-or-system-repair-disc-in-windows-8/)
It seems to me for my purposes it does not matter if I create a dvd or usb recovery drive/ disc:
>   If your PC cannot boot from USB, you’ll need the CD/DVD-based system repair disc.
    The USB-based recovery drive is tied to the PC that you used to create it. Having a system repair disc around will let you troubleshoot startup problems on different PCs running the same version of Windows.

Like we said, though, both tools will let you access the advanced boot options and other recovery tools if you can’t access them any other way

In post Win 7 versions can I asume that I do not need to worry if the donor machine is 64bit and the receiver 32bit?

---

### Post by Robbyx on 2018-01-25
I have a windows 7 repair disk. I have got to the Command prompt option within the repair disk. I guess the partition that needs to be repaired is logical  Partition 4 (how do I check if it is the ntfs partition: from within the repair disk)

I would like to run chkdsk on partition 4. Do you know the correct syntax?

I have tried to follow the advice on: [http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html](http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html)
I selected partition 4 (via Select partition 4) and then typed "Active" and it reported "virtual disk service error: the certified partition type is invalid for this operation"

---

### Post by oldfred on 2018-01-25
Available parameters depend on version of Windows.

 Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r     # for NTFS only use /f for FAT32
[https://technet.microsoft.com/en-us/library/cc730714.aspx](https://technet.microsoft.com/en-us/library/cc730714.aspx)
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)
Windows 10 chkdsk
[https://www.tenforums.com/tutorials/40734-drive-error-checking-windows-10-a.html](https://www.tenforums.com/tutorials/40734-drive-error-checking-windows-10-a.html)

---

### Post by Robbyx on 2018-01-25
> **oldfred said:**
> Available parameters depend on version of Windows.

 Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r     # for NTFS only use /f for FAT32
[https://technet.microsoft.com/en-us/library/cc730714.aspx](https://technet.microsoft.com/en-us/library/cc730714.aspx)
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)
Windows 10 chkdsk
[https://www.tenforums.com/tutorials/40734-drive-error-checking-windows-10-a.html](https://www.tenforums.com/tutorials/40734-drive-error-checking-windows-10-a.html)

Thank you for your response. 

The internal HD has the first 3 partitions for Ubuntu. The 4th is the NTFS partition. How do I find what letter has been allocated by the Win 7 repair disk to the NTFS partition? At present i only know that  it is partition 4. Can I assume that each partition is given a different letter by the disk?

---

### Post by Yellow Pasque on 2018-01-25
> I selected partition 4 (via Select partition 4) and then typed "Active" and it reported "virtual disk service error: the certified partition type is invalid for this operation" 

It sounds like you were trying to make a logical partition active? If so, why? You don't need to do that to run chkdsk on it.

EDIT: Maybe you were trying to SELECT a disk in diskpart?

---

### Post by Yellow Pasque on 2018-01-25
> **Robbyx said:**
> Thank you for your response. 

The internal HD has the first 3 partitions for Ubuntu. The 4th is the NTFS partition. How do I find what letter has been allocated by the Win 7 repair disk to the NTFS partition? At present i only know that  it is partition 4. Can I assume that each partition is given a different letter by the disk?

This is more of a question for a Windows forum, no?
Anyway, this should give you the drive letter:
```

diskpart
list volume
exit
```

---

### Post by Robbyx on 2018-01-25
> **Temüjin said:**
> It sounds like you were trying to make a logical partition active? If so, why? You don't need to do that to run chkdsk on it.

EDIT: Maybe you were trying to SELECT a disk in diskpart?

No I am just struggling to run chkdsk from the win7 repair disk on only the NTFS partition.

I do not know the drive letter allocated to the NTFS partition by the repair disk I only know the partition number.

I assume I run chkdsk:

chkdsk <drive letter for ntfs>  /b

Is it possible to put in the partiton number instead of the drive letter?

---

### Post by Yellow Pasque on 2018-01-25
I'm not sure if you saw my previous post (you probably posted yours at about the same time), but list volume should give you the letter. Or if pictures help, see #3 here for example of list volume output:
[https://helpdeskgeek.com/how-to/diskpart-windows-how-to-use/](https://helpdeskgeek.com/how-to/diskpart-windows-how-to-use/)

---

### Post by Robbyx on 2018-01-28
Thank you for going the extra mile to help me. The outcome has been satisfactory in that the drive is now accessible.

---

