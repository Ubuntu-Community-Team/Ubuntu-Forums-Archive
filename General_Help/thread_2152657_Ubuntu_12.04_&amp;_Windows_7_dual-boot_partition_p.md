---
title: "Ubuntu 12.04 &amp; Windows 7 dual-boot partition problem"
date: 2013-06-08
forum: General Help
---

### Post by boxcorner on 2013-06-08
Hello

I had configured my Lenovo Z570 laptop, which had Windows 7 pre-installed, to dual-boot Ubuntu 12.04 and that worked fine.
Unfortunately the backup software for my Nokia phone only supported Windows.
After backing up my phone, Windows 7 reported C: drive nearly full.
However, the D: drive, which contained drivers, had plenty of free space.
So (stupidly, in retrospect) I used Windows 7 partition manager to reduce D: and increase C: by the corresponding amount.
Now my laptop reports the following when started:[INDENT]error: no such partition
grub rescue>_[/INDENT]
Is there any way to recover Windows 7 and/or Ubuntu 12.04 ?

Thanks in advance for any help

---

### Post by ahallubuntu on 2013-06-08
I wonder if you actually blew away your Ubuntu partitions?

Boot up your 12.04 live USB or live CD, then type this command:

sudo parted -l

and give the output here.

---

### Post by boxcorner on 2013-06-08
Many thanks for your prompt reply:

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD7500BPVT-2 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system  Flags
 1      1049kB  211MB   210MB   primary   ntfs         boot
 2      211MB   57.9GB  57.7GB  primary   ntfs
 3      57.9GB  734GB   676GB   extended               lba
 5      703GB   706GB   3274MB  logical   ntfs
 6      706GB   734GB   27.9GB  logical   ntfs
 4      734GB   750GB   15.8GB  primary   ntfs         diag




Model: Generic Flash Disk (scsi)
Disk /dev/sdb: 2136MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      32.8kB  2136MB  2136MB  primary  fat16        boot




ubuntu@ubuntu:~$

---

### Post by ahallubuntu on 2013-06-08
Sorry, I don't see any Linux partitions there. I assume that means you accidentally deleted them during the resize. Windows 7 should detect Linux partitions as "unknown format" or something like that and may even offer to format them (you should say "no").

(I'm assuming you have only the 750GB hard drive and not a second drive.)

So - what now? If you want to get Windows to boot again, dig up a Windows 7 install disc. If you don't have a Windows disc, you can download/burn a free one legally from Softpedia. Google for "windows 7 softpedia."

Boot the Windows disc and try boot repair. You can also dump into a Command Prompt and type:

```
bootrec.exe /fixmbr
```

Not that I'm discouraging you from re-installing Ubuntu, but that means resizing partitions all over again. FYI, if you wish to do that, you don't need a whole lot of space for a working Ubuntu installation. 20GB is probably more than enough if you store most of your files in your Windows partitions. I have Ubuntu 12.04 running on my netbook in a 6GB partition (almost full though - but it works fine).

---

### Post by boxcorner on 2013-06-09
I downloaded Windows 7 Home ISO x86, burned to CD.
Laptop booted, but when I ran repair it reported wrong version of Windows.
I am now downloading Home Premium x64 (will try Pro if Premium is wrong version).
Is there an easier way to determine version?
Sparse setup info supplied by Lenovo doesn't mention OS.
All docs supplied on HD ... frustrating.
Please explain what you mean by "dump into a Command Prompt"
```
grub rescue> bootrec.exe /fixmbr
Unknown command 'bootrec.exe.'
grub rescue> ls
(hd0) (hd0,msdos6) (hd,msdos5) (hd0, msdos4) hd0, msdos3) (hd0, msdos2) (hd0, msdos1)
```

I selected:[INDENT]"Use recovery tools that can help fix problems starting Windows. [/INDENT]
```
[INDENT]Select an operating system for repair."[/INDENT]
The OS is listed as:[INDENT]"Windows 7"[/INDENT]
```
When I select that recovery option a pop-up is displayed:[INDENT]"System Recovery Options
This version of System Recovery Options is not compatible with the version of Windows you are trying to repair. 
Try using recovery disc that is compatible with this version of Windows."[/INDENT]
Not very helpful. It would be more helpful if it determined which version of Windows 7 it is!

Booting Ubuntu from USB key, devices listed are:
```
210 MB Filesystem ... boot stuff
58 GB Filesystem ... Documents and Settings, Program Files, etc.
3.3 GB Filesystem ... Drivers, Lenovo stuff
New Volume
```

I found this [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) very helpful.
Downloaded Boot-Repair-Disk-64bit.iso from [http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/) & burned disk.
Repaired successfully, so now able to boot Windows.
Will try to get Ubuntu running again dual-boot as before, so I can restore from backup.

Installed Ubuntu 12.04 LTS from USB key.
Dual-boot Windows/Ubuntu works fine.
Update Manager downloading 566 updates.
Re-installed Gnome 3.

Restored humongous amount of data from Déjà backups.
Recovered all except my pride, thanks to Boot-Repair-Disk & Déjà Dup Backup Tool.
All's well that ends well (Heywood, Shakespeare, et alia)

---

