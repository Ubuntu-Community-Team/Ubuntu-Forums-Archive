---
title: "How safe is it to write to NTFS under Ubuntu?"
date: 2013-02-16
forum: General Help
---

### Post by MrsUser on 2013-02-16
I ordered a new external hard disk drive. And I will copy a lot of data to it, almost 3TB.

So far, I didn't experience any problems with writing to NTFS under Ubuntu, except for  the fact that I have to keep track of keeping file names Windows compatible (it'd be nice if Ubuntu would give me a warning about Windows-incompatible file names when  writing to NTFS -- by the way, I wonder if there is a Linux tool  that can recursively batch rename all files of a partition to Windows  compatible file names).

As for NTFS the advantage is that I can access the files on the hdd from both Ubuntu and Windows. Even though I basically never use Windows, I thought it's perhaps still better to format to NTFS, just in case I have a situation where I need access from a Windows OS.

Ubuntu can read and write NTFS, of course. But I wonder how safe is it for my data? How 'clean' is Ubuntu's implementation to write NTFS? Are there any drawbacks, e.g. that it could corrupt the files or the file system? Because it's a lot of data, so I want to make sure the file system will not get corrupted due to possible incompatibilities.

-------------------
EDIT:
I have just found the answer here:
[http://ubuntuforums.org/showthread.php?t=1154652](http://ubuntuforums.org/showthread.php?t=1154652)

and here:
[http://askubuntu.com/questions/32292/is-ntfs-3g-safe-for-writing](http://askubuntu.com/questions/32292/is-ntfs-3g-safe-for-writing)

---

### Post by DeMus on 2013-02-16
What you could also do is make the disc ext4 and use this file system while using a Linux distro.
Should you ever have to use Windows again, boot that computer with a live-cd, copy the file(s) to the hard drive in that computer and re-boot into Windows.
That way, you can use Linux all the way and, as you also mentioned you will almost never have to use Windows again, you use the full capacity of the Linux system

---

### Post by carl4926 on 2013-02-16
> And I will copy a lot of data to it, almost 3TB.I know of no real issues
Such a drive will need to be GPT

---

### Post by sgage on 2013-02-16
I've been using an ntfs-formatted external HD for backup from both Linux and Windows for years, and have never had a problem, other than the Windows filename situation that you are already aware of.

---

### Post by Sef on 2013-02-16
No problem should pop up. Have used NTFS and everything works.

---

### Post by Bufeu on 2013-02-16
[http://superuser.com/questions/32838/is-ntfs-on-ubuntu-stable](http://superuser.com/questions/32838/is-ntfs-on-ubuntu-stable)
[http://forums.freebsd.org/showthread.php?p=153546#post153546](http://forums.freebsd.org/showthread.php?p=153546#post153546)

NTFS is a  a proprietary file system. There are no open specifications of it.  Everything that ntfs-3g can do was achieved by reverse engineering. Today, the NTFS support in Linux should be stable. But one of the down sides of NTFS is that it doesn't support Linux file permissions, so this must be set when mounting the partition: [http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by kurt18947 on 2013-02-16
If you use Windows *very* occasionally,  there are a few Windows add-ons that enable Windows to read ext2/3/4.  I've not tried them, been okay with NTFS but from what I've read, the Windows add-ons are safe and work well to READ ext formatted disks.  Writing to ext* in Windows can lead to corruption.  Here is one:

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

Here is another.  Note that this supports both reading and writing.  I'm not sure how safe that is:

[http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html](http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html)

A google search turns up more options.  I haven't used any of them but the two above would probably top my list if I needed the capability.  If you're skeptical of NTFS and only need occasional Windows access, you could read the file in Windows then save in Windows.

---

### Post by Bufeu on 2013-02-16
> **kurt18947 said:**
> If you use Windows *very* occasionally,  there are a few Windows add-ons that enable Windows to read ext2/3/4.  I've not tried them, been okay with NTFS but from what I've read, the Windows add-ons are safe and work well to READ ext formatted disks.  Writing to ext* in Windows can lead to corruption.  Here is one:

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

Here is another.  Note that this supports both reading and writing.  I'm not sure how safe that is:

[http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html](http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html)

A google search turns up more options.  I haven't used any of them but the two above would probably top my list if I needed the capability.  If you're skeptical of NTFS and only need occasional Windows access, you could read the file in Windows then save in Windows.[http://www.linuxjournal.com/article/9449](http://www.linuxjournal.com/article/9449)

---

### Post by oldfred on 2013-02-16
Unless you are copying video or other large files I would hesitate to make any one 3TB partition. Just because new drives are very large does not mean partitions should be.

If NTFS chkdsk will take forever, and you should have a Windows install to periodically run chkdsk. That can only be done from Windows. Windows does not automatically do that like LInux does.

Even with ext4 fsck will take longer. And Linux normally schedules fsck every 40 or 60 reboots.

You will have to use gpt partitioning as MBR has a max of 2.2TB or 2TiB. MBR was designed in middle '80s with first hard drive for PC. It has reached its design limit.

Use gparted or gdisk to create gpt partitions.
       GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

    
       I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

---

### Post by MrsUser on 2013-02-17
Thank you all for the great hints.
As for automatically only allow Windows filenames when writing to NTFS under Linux, I googled around a bit more and found out that it is actually already built-in into ntfs-3g, it just has to be activated:

> As Windows uses more restrictive naming rules, you can prevent ntfs-3g  from creating new files which do not meet Windows file naming rules by  using the option **windows_names**.
[http://www.tuxera.com/community/ntfs-3g-faq/](http://www.tuxera.com/community/ntfs-3g-faq/)Obviously, the option windows_names has to be used when mounting the drive, I assume I have to put it in fstab then?! I'm looking for examples how to do it.

 Anyway, I'll also tinker around a bit with the option to install ext4 supoort  in Windows (I only need to read from the hdd when under Windows,  so this should be alright). So I guess the "Linux Reader for Windows" from Sysinternals is just what I need, in case I decide to go for ext4:

> [...] the program provides for read-only access and does not allow you to make  records in file system partitions. This guarantees that the  interference in an alterative file system will not affect the work of  Linux later. [...]
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)As for the file permissions of ext4, I don't really need to keep them on the external hdd. All the data is just static data that is not really sensitive or private, videos, photos and there is no need for any access restrictions in my home. Actually, it's just the contrary: I want to be able to access the data from any computer I plug the hdd into. So I wonder what happens then? Am I getting locked out of from my own hdd when using ext4 and plugging it into another Linux machine? Or how do I access the drive then?

However, in case a hdd with sensitive data gets stolen (which probably won't happen to me as I rarely take the hdd somewhere else than the next room), just out of interest: How does it work to encrypt the whole hdd with Linux tools? And is there any way to read that encrypted hdd when under Windows? I heard of TrueCrypt, but I'm not sure if this is a good solution, because it's third-party.

> **oldfred said:**
> I have created my gpt partitions with gparted.  Under device, create partition table, advanced, choose gpt not the  default msdos (MBR) partitioning.

Very useful, thanks! But in case I format to NTFS. Should I do the paritioning and formatting under Windows (maybe to make sure it's best compatible to Windows)?!

---

### Post by jmore9 on 2013-02-17
I use 500 gig and 1 tb NTFS formated drives inter changeably on windows
XP and 7 and Ubuntu 12.10 and Pclinusos and have not had any problems.  The only problem i have had with Ubuntu and NTFS was with an old 6.4gig hard drive i wanted to see if it still worked so used Ubuntu to check it.  It is really old so had a little bit of a time getting access to it.  Also a cannon ( i think its a cannon ) 2 drives connected together to make one from long ago casued some problems.  But you should not have any problems with modern drives.

---

### Post by Rebelli0us on 2013-02-17
> **MrsUser said:**
> I ordered a new external hard disk drive. And I will copy a lot of data to it, almost 3TB.

So far, I didn't experience any problems with writing to NTFS under Ubuntu, except for  the fact that I have to keep track of keeping file names Windows compatible (it'd be nice if Ubuntu would give me a warning about Windows-incompatible file names when  writing to NTFS -- by the way, I wonder if there is a Linux tool  that can recursively batch rename all files of a partition to Windows  compatible file names).

As for NTFS the advantage is that I can access the files on the hdd from both Ubuntu and Windows. **Even though I basically never use Windows**, I thought it's perhaps still better to format to NTFS, just in case I have a situation where I need access from a Windows OS.

Ubuntu can read and write NTFS, of course. But I wonder how safe is it for my data? How 'clean' is Ubuntu's implementation to write NTFS? Are there any drawbacks, e.g. that it could corrupt the files or the file system? Because it's a lot of data, so I want to make sure the file system will not get corrupted due to possible incompatibilities.

-------------------
EDIT:
I have just found the answer here:
[http://ubuntuforums.org/showthread.php?t=1154652](http://ubuntuforums.org/showthread.php?t=1154652)

and here:
[http://askubuntu.com/questions/32292/is-ntfs-3g-safe-for-writing](http://askubuntu.com/questions/32292/is-ntfs-3g-safe-for-writing)

If you use NTFS you MUST boot Windows and run chkdsk occasionally because Linux cannot do it.

If you "never use Windows" or rarely, then consider using ext4 and running Windows as a Guest OS in a Virtual Machine.

---

### Post by Bufeu on 2013-02-17
> **Rebelli0us said:**
> If you use NTFS you MUST boot Windows and run chkdsk occasionally because Linux cannot do it.

If you "never use Windows" or rarely, then consider using ext4 and running Windows as a Guest OS in a Virtual Machine.Or...

> **Bufeu said:**
> [http://www.linuxjournal.com/article/9449](http://www.linuxjournal.com/article/9449)

---

### Post by oldfred on 2013-02-17
from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by MrsUser on 2013-02-18
> **oldfred said:**
> from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

Thank you so much! The trash problem was indeed annoying. Didn't know there's a fix for it :) But still, maybe I'll format to ext4. I use Windows very rarely.

---

### Post by MrsUser on 2013-02-20
I decided to format in NTFS. Thing is today I received the new external hdd. Then I wanted to convert it to GPT. I did that in Windows (I used Windows to use Seagate's Dashboard software to set the power savings time of the hdd). But accidentally I chose the wrong hdd. I had my other external hdd still plugged in and did everything too quick -- and then the damage was done. I had deleted the partition (needed before being able to convert it to GPT) and then set it to GPT. A few seconds after I realized I had chosen the wrong hdd and was of course terribly worried. Because I temporarily had a big portion of my data only on this hdd, trusting I'll do everything right until I create my new backup. Really, a newbie mistake :-/

However, I am currently in the processing of recovering all the data successfully. First I tried TestDisk to recover the lost partition, but I had overwritten it already, so no chance there. But then I used 'Power Recovery' from MiniTool and chose the option for 'Damaged Partition Recovery'. Even though I can't recover the partition itself, this nifty tool was able to list all the files and folders that are on it, even the deleted stuff. And so I was able to select all those files and copy them to the other hdd.

So then I decided to have the new external hdd in NTFS. Simply because in this case I was happy to have Windows on my machine to run that recovery software which makes data recovery a piece of cake. Also, if the new external hdd would have been in ext4, I wouldn't have had any other medium to write the recovered data to. Therefore I think it's best to have it in NTFS, as it is the most accessible regardless of the OS I'm running. Such situation as today could happen anytime or maybe at some point I really need to access it from Windows for some other reason.

And I'll keep the dual boot, of course. One never knows when Windows is absolutely needed, even if using Ubuntu all the time. And vice versa it's the same. Windows users sometimes could really need a Linux to do stuff they can't achieve with Windows. I guess it's best to have the best from both sides when it comes to tricky situations as the one I had today.

Anyway, I'll purchase another hdd of the same size to have a backup of the first hdd. And the other hdd I will format in ext4. Then I have one in NTFS and one in ext4. A good balance I guess :)

However, I'm not sure yet if I should keep the default kind of formatting of the new hdd. It's a 4TB hdd, but uses MBR (which works -- it seems to emulate another kind of sectors to the OS). On the other hand, the drive simply works as is. So why touch it? Or do you guys think it's still better to switch to GPT? Are there any disadvantages of the pseudo-MBR? Also, I heard of LVM partitioning and how easy it is to change partition sizes. Is this something I could apply to the external hdd? And if so, how do I do it?

---

### Post by oldfred on 2013-02-20
If you are using MBR on a 4TB drive you only have 2.2GB of data as that is the max that MBR can possibly do.

Only gpt can handle that larger drives. And we have seen some issues with Windows and those very large gpt drives. Best to use gdisk which is the fdisk for gpt drives or gparted to create gpt partitioning.

Lots of Info on gpt:

       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
Windows does not follow UEFI spec on size of protective MBR
[http://thestarman.pcministry.com/asm/mbr/GPT.htm](http://thestarman.pcministry.com/asm/mbr/GPT.htm)

       GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

    GPT Advantages (older but still valid)  srs5694 post #@:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by sleash78 on 2013-02-20
yes

---

### Post by MrsUser on 2013-02-20
> **oldfred said:**
> If you are using MBR on a 4TB drive you only have 2.2GB of data as that is the max that MBR can possibly do.
Actually, I have the full 4TB despite MBR. Obviously the hdd emulates different block sizes. I read somewhere an article about it. I suppose this is some kind of 'hack' that some manufacturers use in order to make it readable for older operating systems (Windows XP for instance) too, although those OS types have the 2,2TB limit then. However, to be on the safe side I'll switch to GPT. Although I'm not sure if there is any drawback to this as for the hdd software tools that came shipped with it. It's a Seagate Backup Plus 4TB.

---

### Post by oldfred on 2013-02-20
You must have the new Advanced format or 4K drive. New partition tools align those correctly. 

       How to install a WD Advanced Format Drive on a non-Windows Operating System
the following distributions will default to good alignment for Advanced Format disk drives: Ubuntu 10.04, Fedora 13, Redhat 6 and derived products. 
[http://wdc.custhelp.com/app/answers/detail/a_id/5655](http://wdc.custhelp.com/app/answers/detail/a_id/5655)
How it works around 2TiB limit. 
[https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues](https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues)

---

### Post by MrsUser on 2013-02-21
I used Windows to convert the drive to GPT. But now I see it created a "Microsoft Reserved" partition of 128MB at the beginning which seems totally useless as this drive is an external drive and won't be used for anything else than simple data storage.

The reason why I used Windows to do it was that I thought if it's done in Windows then I won't have any possible compatibility issues for Windows. However, I want to format it as GPT without that Microsoft Reserved partition -- in other words: I want it 'clean'.

What is the most elegant way to do it (newbie-proof)? Are there any GUI based tools for Linux or do I have to do it via command line?

I have already copied about 700GB on it. Can I somehow kill the Microsoft Reserved partition and add it to the existing main partition? Or is it better to do a fresh formatting? I can backup the data, but copying again 700GB via USB 2.0 is a pain, especially because I'd have to do this twice -- creating the backup and then write the data back after the formatting.
---------
EDIT:
**Microsoft Reserved Partition (MSR) is actually required for GPT by Windows?**
> Every GPT disk must contain an MSR.[COLOR=Navy]Windows and GPT FAQ: [http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

[COLOR=Black]Not sure what happens when creating a GPT without MSR, if this will be a problem for Windows or not.

Oh, and I just saw that GParted can create and handle GPT. That's nice. But is an MSR partition compulsary or not?
[/COLOR] [/COLOR]

---

### Post by oldfred on 2013-02-21
It was my understanding that the MSR is required just before the main Windows partition. With gpt there is no more drive area after the MBR and before the first partition. There used to be issues with grub & windows writing info into that area just after the MBR. So I think the MSR is just space for Windows to write the serial numbers, DRM registration info, hidden data from virus software and just hidden data from other software. It is unformatted so it must just be a scratch pad.

If booting with UEFI you may want an efi partition at the beginning of the drive. I like to have an operating system on every drive. 

       I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

I follow this logic but use Ubuntu instead.
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by MrsUser on 2013-02-21
In other words: If I don't boot from that drive, I don't need the MSR (at least as long as Microsoft doesn't make it mandatory in the future). So I could delete it. On the other hand, there's no negative side keeping it, I suppose -- except for 128MB less, which is ok considering the drive is 4TB 8-)

----------------

Update:
I sent the hdd back. It's quite noisy and gets very hot even in idle (more than 50° Celsius). Not very safe for my data. However, I've formatted my other external hdd to ext4 now and I probably will format another drive I want to purchase also to ext4. I just don't like the Windows stuff. And I tried the ext4 Linux reader software for Windows which does a good job. So no problem to access the data when in Windows. Although I want to wipe Windows from my hdd and have a pure Ubuntu computer again. :)

---

