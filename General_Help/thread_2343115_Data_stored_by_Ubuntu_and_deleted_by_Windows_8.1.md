---
title: "Data stored by Ubuntu and deleted by Windows 8.1?"
date: 2016-11-13
forum: General Help
---

### Post by cpighin on 2016-11-13
Hello, 
I am Italian and since October I have a **new notebook**:
**ASUS-S551LN** (label S551LN-CJ526H) with **Windows 8.1** and an optical **HD** with **1TB** capacity
on which I installed **Ubuntu 16.04.1** in a **dual boot** configuration.

I encountered a [B]serious problem: if Ubuntu is used to save files or folders in the DATA partition (formatted NTFS from Windows), the data remains in the partition until Windows is started. Since then files/folders no longer appear in the partition!
[/B]
I initially thought that Windows 8.1 was the cause of the problem, but it seems unlikely to be true. If that were so, I would find many articles/posts on the Web, but I found only a few cases of users who complain about the same problem.

Consider that in the DATA partition I had copied thousands of personal files that were deleted, and this caused me serious damage!

Of course I asked the ASUS Support for an explanation of the incident and finally I got the following answer (translated from Italian):

> The machine's original operating system is Windows. Therefore we can not officially provide support for unsupported operating systems.

However, we have deepened the problem and is quite known in Unix. Windows 8 and 8.1 have difficulty in managing files created by other operating systems (more precisely cancel changes, therefore if the file is created in Ubuntu will be deleted).

You could use a file system natively shared by both systems, the FAT. The FAT is little usable because of limitations in the size of files that can be saved in the partition (the single file can not exceed 4GB).

As an alternative to FAT32, you could try to format the data partition in ExFAT (FAT64), but it is not a native Linux format (exactly as NTFS) therefore you should install some additional packages, hereinafter a guide:

[http://www.lffl.org/2012/06/exfat-fat64-levoluzione-di-fat32-su.html]("http://www.lffl.org/2012/06/exfat-fat64-levoluzione-di-fat32-su.html")

These Workaround are not intended as a solution but as a possible alternative, and they could not solve the problem that is structural in Windows.

I can hardly believe that information received are true, because if that were confirmed, [B]it would mean that ALL Windows 8.1 machines cannot use a Linux operating system to store data, even if the OS is mounted on a USB stick and, frankly speaking, this sounds as incredible to me!
[/B]
And **if this was true only for ASUS computers**, then this information should be communicated to customers who want to use a Linux OS, so that they may turn to another producer!

Regarding the question on the type of formatting: if the ASUS expert recommended to format the DATA partition to FAT or FAT32, it means that he believes that the problem happens **only with NTFS partitions and even this does not convince me**.

[B]What do you think about this issue?

Am I one of few people who complain about deletion of Ubuntu data with Windows 8.1 or many other users have the same problem?

How can I solve the problem?
[/B]
Claudio :)

---

### Post by oldfred on 2016-11-13
Do you have Windows hibernation or fast start up on?
That leaves the NTFS mounted and restores it to as it was when you re-boot back into Windows. 

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by cpighin on 2016-11-13
> **oldfred said:**
> Do you have Windows hibernation or fast start up on?
That leaves the NTFS mounted and restores it to as it was when you re-boot back into Windows. 


I am confident to have set Windows hibernation and fast start up OFF before installing Ubuntu, but I'm ready to follow your instruction to check my system!

Claudio :)

---

### Post by oldfred on 2016-11-13
Almost all those that have had issues were related to fast start up or hibernation.
       More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by cpighin on 2016-11-13
> **oldfred said:**
> Almost all those that have had issues were related to fast start up or hibernation.
       More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

I have read what reported on the link above and I think that my pc issue is different!

Have you notice of people with same problem?

Claudio :)

---

### Post by yancek on 2016-11-13
> I can hardly believe that information received are true, because if that were confirmed, **it  would mean that ALL Windows 8.1 machines cannot use a Linux operating  system to store data, even if the OS is mounted on a USB stick and,  frankly speaking, this sounds as incredible to me!**

That a windows operating systems cannot use a Linux operating system is absolutely and unequivacally true and it doesn't matter which release of windows you are using, even the latest windows 10.  This is a decision made by microsoft and there is nothing anyone outside microsof can do about it.  But this isn't your problem since you indicate that your data partition is formatted with a proprietary windows filesystem.   I don't use hibernation but that seems like a logical source of the problem.  Millions of people use Ubuntu and other Linux systems and share data on FAT32 and ntfs formatted filesystems without problems.

---

### Post by cpighin on 2016-11-14
> **yancek said:**
> That a windows operating systems cannot use a Linux operating system is absolutely and unequivacally true and it doesn't matter which release of windows you are using, even the latest windows 10.  This is a decision made by microsoft and there is nothing anyone outside microsof can do about it.  But this isn't your problem since you indicate that your data partition is formatted with a proprietary windows filesystem.   I don't use hibernation but that seems like a logical source of the problem.  Millions of people use Ubuntu and other Linux systems and share data on FAT32 and ntfs formatted filesystems without problems.
Thanks **yancek**

I have 2 older PC with dual boot systems (WindowsXP/Ubuntu12.04 and Windows7/Ubuntu14.04) and I had no problem on storing data on a common partition. This is the first time I'm experimenting such an issue:( Can you explain why with the new machine?

Regarding the hibernation, do you think that de-activating it in Windows I will solve the problem?

Have you notice of people with dual boot machines and data cancelled ?

Claudio :)

---

### Post by yancek on 2016-11-14
Windows 8 and 10 use hibernation by default which your older windows systems did/do not.  I personally have never used hibernation on any system and although I have windows systems on my Desktop, I basically haven't used windows on a regular basis since windows 2000 and doubt I'll be much help with this problem.  You might check into the various ways of turning off hibernation/fastboot and whatever other options you might have as some of this is done in the BIOS and as I undeerstand, there are some options within windows itself.

Good luck.

---

### Post by oldfred on 2016-11-14
Even if you originally turned off fast start up and hibernation, Windows on major updates (or even minor updates) may turn it back on.
Best to regularly check after Windows updates.

---

### Post by cpighin on 2016-11-14
[B]I switched Off the Hibernation mode and tested once more if a file saved by Ubuntu in DATA partition were again there after running Windows and ... it has been cancelled! So, as I can understand, it is not matter of Hibernation!
Am I right?
[/B]
Here under you can check steps done for this test and, at the bottom, a prooff that the Hibernation was Off (0 value)

a) I Set the Hibernation mode to Off
```
Microsoft Windows [Versione 6.3.9600]
(c) 2013 Microsoft Corporation. Tutti i diritti riservati.

C:\Windows\system32>runas /user:Claudio cmd
Immettere la password per Claudio:
Tentativo di avvio di cmd come utente "ASUS-S551LN\Claudio" ...

C:\Windows\system32>powercfg.exe /hibernate off

C:\Windows\system32>Exit
```
b) I turned to Ubuntu and saved file "ProvaDaUbuntu" into partition DATA anc checked few times that it was there

c) I turned to Windows again to check if file "ProvaDaUbuntu" were still there ... but it was NOT: it was cancelled! 

d) I tested in Regedit that Hibernation parameter were set to OFF (parameter "0") and it was confirmed
[IMG]https://s5.postimg.org/6goz3lmbr/Cattura20161114.png[/IMG]

Claudio :)

---

### Post by yancek on 2016-11-14
> c) I turned to Windows again to check if file "ProvaDaUbuntu" were still there ... but it was NOT: it was cancelled! 

What does "turned to Windows" mean?  After copying the file created in Ubuntu and from Ubuntu copying it to your ntfs data partition, did you then boot windows and fail to find the file?  Something is missing here as that is bizarre.  I don't use windows regularly but have often copied files from Linux to a windows ntfs partition and never had any problems.  The files are always where I copied them on the windows partition.

If you don't see the file when you boot into windows, is it still seen when you boot back to Ubuntu and view it on the ntfs data partition?

---

### Post by cpighin on 2016-11-15
> **yancek said:**
> What does "turned to Windows" mean?  After copying the file created in Ubuntu and from Ubuntu copying it to your ntfs data partition, did you then boot windows and fail to find the file?  Something is missing here as that is bizarre.  I don't use windows regularly but have often copied files from Linux to a windows ntfs partition and never had any problems.  The files are always where I copied them on the windows partition.

If you don't see the file when you boot into windows, is it still seen when you boot back to Ubuntu and view it on the ntfs data partition?

Yes, 

after saving the file created in Ubuntu into the ntfs DATA partition, then I boot windows and the file was not there anymore! After running Windows files saved by Ubuntu are not shown into the Partition DATA even under Ubuntu!

Consider that a Windows expert started giving assistance on the issue few days ago but now he is not answering to my posts!

It is very surprising for me that no other users have posted something to inform that I am not the only one experiencing such an issue!

At this point, after having unsuccessfully tried several ways to recover personal files saved in the DATA partition and cancelled (by Windows?), I'm thinking to try creating an L-DATA (Linux DATA) partition formatted ext4 to verify if saved files will remain there!

What do you think?

---

### Post by yancek on 2016-11-15
> After running Windows files saved by Ubuntu are not shown into the Partition DATA even under Ubuntu!


I've never experienced anything like that and have no explanation.  Almost any major Linux distribution will be able to read and write to an ntfs partition if the ntfs-3g software is installed on Linux.  What makes your situation really bizarre is not being able to see the files you copied to an ntfs partition when you re-boot into Ubuntu.  That should not happen.

Creating a data partition with a Linux filesystem should work but you should know that you will not be able to access that data from windows as I pointed out in an earlier post.  You may be able to install some third party software on windows to enable this which may or may not work.

If you are trying to save data you had on the ntfs partition, you might try the 'testdisk' software which you can get from the link below.  Make sure you read the Step by Step instructions before beginning.  

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by cpighin on 2016-11-15
> **yancek said:**
> ...That should not happen.
Yes, but **it DOES HAPPEN !!!**

Remember that an ASUS expert (post [#1]("https://ubuntuforums.org/showthread.php?t=2343115&p=13569404#post13569404"))  wrote > The machine's original operating system is Windows. Therefore we can not officially provide support for unsupported operating systems.

However, we have deepened the problem and is quite known in Unix. Windows 8 and 8.1 have difficulty in managing files created by other operating systems (more precisely cancel changes, therefore if the file is created in Ubuntu will be deleted).


I have to insist: [B]am I the only one user of a double boot system experiencing this issue?
[/B]
Regarding my attempts to restore data I tried also the 'testdisk' software and I opened topic [Help needed to recover files by TestDisk]("https://forum.cgsecurity.org/phpBB3/viewtopic.php?f=5&t=6636&sid=f8309a90be7c4d4e4b7bb67e4ac0350e") with no results :(

Have you good experience on restoring data using TestDisk?

Claudio :)

---

### Post by oldfred on 2016-11-15
Few vendors support anything other than Windows. And their help desk does not know enough to help and often gives out incorrect info.
To the extent that users do have issues, that is true, but everyone we have seen come back with a response was that turning off fast start up or hibernation solved issue.

Are you using pci=nomsi boot parameter. 
Many Asus systems have need that to solve various issues.

       Asus M32CD desktop - Skylake several boot parameters  pci=nomsi  i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[URL="http://ubuntuforums.org/showthread.php?t=2307273"]http://ubuntuforums.org/showthread.php?t=2307273
[/URL]
 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)
[http://ubuntuforums.org/showthread.php?t=2327570](http://ubuntuforums.org/showthread.php?t=2327570) 

[URL="http://ubuntuforums.org/showthread.php?t=2307273"]
[/URL]

---

### Post by yancek on 2016-11-15
> Windows 8 and 8.1 have difficulty in managing files created by  other operating systems (more precisely cancel changes

Which  makes it a windows problem and again, I don't see how anyone at a  Linux/Ubuntu forum is going to be able to make changes to the  proprietary/commercial windows system.  
And no, in the 12 years I've  been using Linux, I have never had a problem like this or known of  anyone else who did.  I'd agree based on my experience with the post by  oldfred about vendors.  Most don't pre-install Linux and don't know  anything about it so give out no information or bad information.  I  expect you would get a similar answer from HP, Toshiba or other  manufacturer.  They are a poor source of accurate info on Linux. 

The hibernation/fastboot options seem to be the culprit in most cases as pointed out above.  Good luck.

---

### Post by cpighin on 2016-11-15
**Oldfred** and **Jangek**,

thank you for your recent posts. I don't know why, but my feeling is that the solution of my problem is elsewhere than "pci=nomsi boot parameter" or "hibernation/fastboot options" since I installed Ubuntu 16,04.1 without relevant problems and my pc has Hibernation and fastboot options Off.

I agree not to expect good software support from vendors, and for this I'm trying to get it by forums.

Now **I have a news**, I don't know if it is good or not: I was preparing the system to create a new little partion named L-DATA (Linux DATA NTFS) just to check if data saved by Ubuntu in a different partition than DATA were cancelled as well. If YES I would have tried to format L-DATA in ext4 to see what were happened.

To do that, I run Windows and tried to reduce the DATA partition using the Disk Manager tool and I did not success because the tool got stuck. So I thought it were appropriate to run "**CHKDSK D: /F /R**" and suddenly the system began to write a long list of data that could possibly help to recover lost files! Now four hours have passed and the system is still running ... I will leave it working without interference!

I'm hoping that by this action it might arise some element useful to take a step towards the solution of the mystery!

I will report in any case ;)

Claudio :)

---

### Post by oldfred on 2016-11-15
With chkdsk you need to run  & rerun until no errors. It does not always fix everything with one pass.

The one Windows 10 system I have just to watch Comcast videos remotely also has 16.04.
So I booted into Windows & turned off fast start up. Booted into Ubuntu and saved a file to a shared NTFS partition.
Rebooted back into Windows and file was there and worked.

---

### Post by cpighin on 2016-11-16
**I HAVE GOOD NEWS** :D 

Command "CHKDSK D: /F /R" did a "miracle": after several hours of running it returned my disk with alla data I lost, even files created and saved by Ubuntu!

This is code returned by Windows
```
  71871538 cluster liberi elaborati.

Verifica dello spazio disponibile completata.
Correzione errori nella mappa di bit del volume.

Correzioni apportate al file system.
Non sono necessarie ulteriori azioni.

 693545983 KB di spazio totale su disco.
 405871876 KB in 72926 file.
          23176 KB in 3809 indici.
                    0 KB in settori danneggiati.
        164779 KB in uso dal sistema.
          65536 KB occupati dal file registro.
 287486152 KB disponibili su disco.

            4096 byte in ogni unità di allocazione.
173386495 unità totali di allocazione su disco.
  71871538 unità di allocazione disponibili su disco.

D:\>
```
Now I'm saving data into an external HD and than I will try to start Ubuntu to do some testing in order to verify if something happens with an ulterior starting of Windows.

**Have any idea on the issue**?

Claudio :)****

---

### Post by oldfred on 2016-11-16
Windows requires chkdsk after any partition resize.

Both Windows (chkdsk) & Linux(fsck) often need repairs if partition abnormally shutdown, or not correctly unmounted. If system crashes or power failure can cause those issues. And sometimes it just needs a file repair.

Linux has a parameter to automatically run fsck based on settings in fstab. It used to be every 40 or 60 reboots.

---

### Post by cpighin on 2016-11-16
**Few news**

in a Topic in Italian it has been requested to run command sudo fdisk -l aqnd to check how many disks are seen by Gparted, avoiding to connect any other device). Here are results:
a) **execution of command sudo fdisk -l**
```
claudio@ASUS-S551LN:~$ sudo fdisk -l
[sudo] password di claudio: 
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 2491E444-004B-48CE-B660-2901E0996F08

Dispositivo      Start       Fine    Settori   Size Tipo
/dev/sda1         2048     206847     204800   100M EFI System
/dev/sda2       206848    2050047    1843200   900M Windows recovery environment
/dev/sda3      2050048    2312191     262144   128M Microsoft reserved
/dev/sda4      2312192  427431935  425119744 202,7G Microsoft basic data
/dev/sda5    427431936  452007935   24576000  11,7G Microsoft basic data
/dev/sda6    452007936  534947389   82939454  39,6G Microsoft basic data
/dev/sda7    534951936 1922043903 1387091968 661,4G Microsoft basic data
/dev/sda8   1922045952 1953523711   31477760    15G Windows recovery environment




Disk /dev/sdb: 22,4 GiB, 24015495168 bytes, 46905264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 18741CF1-E5C0-47D9-93BD-C1014545924A

Dispositivo Start     Fine  Settori  Size Tipo
/dev/sdb1    2048 46903295 46901248 22,4G sconosciuto
claudio@ASUS-S551LN:~$ 

```
b) **devices seen by GParted**
- dev/sda (931,51 GiB)
- dev/sdb (22,37 GiB)

**Hereafter  a new test:**

 c) **content of DATA partition as seen by Windows and Ubuntu**
[img]https://s5.postimg.org/z5g5vf9l3/Cattura_Windows201611161538.png[/img]
[img]https://s5.postimg.org/88w6n3qrr/Cattura_Ubuntu20161116_160337.png[/img]

d) **I have cancelled file ProvaDaUbuntu and created file ProvaDaUbuntu20161116 by Ubuntu** and verifyed its presence into the DATA partiotion, than I closed Ubuntu e run Windows. This is what I saw:
[img]https://s5.postimg.org/f0mlpyfrb/Cattura_Windows201611161626.png[/img]
**Attention, there are 2 significant elements**:
1) file ProvaDaUbuntu20161116 does not exist, but there is the old one ProvaDaUbuntu (for me is a proof that Windows cancel a file if is not created inside itself),
2) I noticed that **the Windows clock is back by one hour**. I noticed this in the past, but I have not considered it important,

e) I have run Ubuntu and verified that new file ProvaDaUbuntu20161116 was not there e the previous ProvaDaUbuntu was not there also, as you see
[img]https://s5.postimg.org/izjt8s4ef/Cattura_Ubuntu201611161642.png[/img]

It is difficult for me to avoid thinking that Windows is not the cause of the problem!

Claudio :)

---

### Post by Impavidus on 2016-11-16
> **cpighin said:**
> 
2) I noticed that **the Windows clock is back by one hour**. I noticed this in the past, but I have not considered it important,

That happens because Ubuntu sets the clock on the motherboard to UTC, but Windows expects the clock to be set to local time. Dual booting is easiest if all systems set the clock to UTC, but it may be a bit tricky to tell Windows to do so. So it's recommended to instruct Ubuntu to set the clock to local time. See this thread: [https://ubuntuforums.org/showthread.php?t=2321876](https://ubuntuforums.org/showthread.php?t=2321876) (post #2)

Normally when installing as dual boot with Windows, Ubuntu is configured automatically to set the mobo clock to local time, but this may not happen when Windows isn't correctly detected during install.

As for your main problem: I've got no experience with any Windows past XP, but it seems that Windows doesn't properly unmount its file system on shutdown and properly mount it on boot. That is, it seems fastboot is still on, although you switched it off, you say. Indeed, it seems Windows causes the problem. But it makes me wonder why Ubuntu is willing to mount the partition in read-write mode. It shouldn't do so when Windows hasn't properly unmounted it.

---

### Post by cpighin on 2016-11-17
> **Impavidus said:**
> That happens because Ubuntu sets the clock on the motherboard to UTC, but Windows expects the clock to be set to local time. Dual booting is easiest if all systems set the clock to UTC, but it may be a bit tricky to tell Windows to do so. So it's recommended to instruct Ubuntu to set the clock to local time. See this thread: [https://ubuntuforums.org/showthread.php?t=2321876](https://ubuntuforums.org/showthread.php?t=2321876) (post #2)

If I remember correctly, the Windows clock came back to local time after the execution of command "CHKDSK D: / F / R". If so, the cause of discrepancies with Ubuntu should be other.

> As for your main problem: I've got no experience with any Windows past XP, but it seems that Windows doesn't properly unmount its file system on shutdown and properly mount it on boot. That is, it seems fastboot is still on, although you switched it off, you say. Indeed, it seems Windows causes the problem. But it makes me wonder why Ubuntu is willing to mount the partition in read-write mode. It shouldn't do so when Windows hasn't properly unmounted it.

In the Italian Ubuntu forum I got a suggestion that "my pc would use the Intel Smart Response Technology (it uses a small SSD as a cache to speed up a PC). Obviously running Windows, it would cause conflict with the dual boot Ubuntu, and this would explain the missing files".

This may be the case. As a matter of fact, running Windows Disk Manager I got following image, just few days after the purchase!
[img]https://s5.postimg.org/7b9325g07/20161008Prima.png[/img]
You can see a "Disco 1" that may be the SSD mentioned above!

I will try to disable the Intel Smart Response application and we'll see the result!

Claudio :)

---

### Post by oldfred on 2016-11-17
If Intel SRT drive may also have RAID meta-data which you have to remove to get grub to install. It used to be Ubuntu installer would not see drive at all, but now it seems to install correctly except for grub.
The Intel SRT is just a cache so Windows can boot faster. Part of requirement by Microsoft to make it seem like Windows is not so slow booting. But not used for anything else. And cache is just size of RAM, but SSD is usually larger. Some just delete SRT & RAID meta-data and install Ubuntu / (root) to SSD to make Ubuntu fast. But have /home on HDD. Some with even larger SSD, keep SRT and still have room for / in unused space.

 Intel Smart Response Technology
[http://mjg59.dreamwidth.org/26022.html](http://mjg59.dreamwidth.org/26022.html) 
      
 Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
HP Envy  Windows 7 with MBR & SRT
[URL="http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx"]http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx
[/URL]
 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491) 

[URL="http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx"]
[/URL]

---

### Post by cpighin on 2016-11-18
Intel Smart Response **(Intel® SRT)** seems not to be installed on my PC. As a matter of fact I was not able to find it into the system.
Here under is the list of Intel Srevices running on my PC:
> Intel Bluetooth Service
Intel(R) Capability Licensing Service TCP IP Interface
Intel(R) Content Protection HECI Service
Intel(R) Dynamic Application Loader Host Interface Service
Intel(R) Dynamic Platform and Thermal Framework Config TDP Service Application
Intel(R) Dynamic Platform and Thermal Framework Critical Service Application
Intel(R) Dynamic Platform and Thermal Framework Low Power Mode Service Application
Intel(R) Dynamic Platform and Thermal Framework Processor Participant Service Application
Intel(R) HD Graphics Control Panel Service
Intel(R) Management and Security Application Local Management Service
Intel(R) ME Service
Intel(R) PROSet/Wireless Event Log
Intel(R) PROSet/Wireless Registry Service
Intel(R) PROSet/Wireless Zero Configuration Service
Intel(R) Smart Connect Technology Agent

I have not found anything attributable to the two technologies mentioned above except, perhaps:

**Intel(R) Management and Security Application Local Management Service**
**Intel(R) ME Service**

although, reading few articles on the net, I am led to believe that even they are not involved in the problem.

Am I wrong?

Claudio :)

---

### Post by oldfred on 2016-11-18
It seems you do not have Intel SRT.
But the configuration with a small SSD, is typical of Windows hibernation configuration.
Vendors were required by Microsoft to add hardware or change system so it made it seem that Windows booted faster, since it does not boot faster.

---

### Post by cpighin on 2016-11-18
> **oldfred said:**
> It seems you do not have Intel SRT.
But the configuration with a small SSD, is typical of Windows hibernation configuration.
Vendors were required by Microsoft to add hardware or change system so it made it seem that Windows booted faster, since it does not boot faster.

As you may check in my [post #10]("https://ubuntuforums.org/showthread.php?t=2343115&p=13569910#post13569910") I should have set Hibernation to OFF, but I have not seen significative change in the Windows booting speed, so i cannot exclude that hibernation is still active.

Do you know how to exclude securely the hibernation function?

Claudio :)

---

### Post by oldfred on 2016-11-18
Beyond the instructions posted in Windows forums, I do not know anything about Windows hibernation.

As posted before my one primarily Windows 10 system with hibernation off as per Windows forums instructions, does let me use a shared NTFS partition for files.

---

### Post by cpighin on 2016-11-18
> **oldfred said:**
> ...As posted before my one primarily Windows 10 system with hibernation off as per Windows forums instructions, does let me use a shared NTFS partition for files.

Unfortunately, I cannot do the same. Consider that this aftenoon I spent time to check if my system has hibernation set to off and that seems to be true!

I continue to ask: am I the only one in this forum soffering for data deleted by Windows 8.1 if saved by Ubuntu?

Claudio :)

---

### Post by cpighin on 2016-11-21
**I stopped to look for a proper solution, and I opted for a temporary one**!

By Windows, I reformatted the DATA partition (NTFS), then I reduced it to 157.64 GB to leave a free volume of about 500 GB where then I created the Linux-DATA ext4 partition to prevent its use by Windows.

[img]https://s5.postimg.org/v59xlxgzr/Schermata_del_2016_11_20_17_12_27.png[/img]

Since the partition was created by GParted as administrator, I could not copying my files there. Then I opened Nautilus as administrator and I modified the partition permissions so that now I can read, write, delete files and folders.

Then I filled the Linux-DATA partition with my file and I run a test: I created file ProvaDaUbuntuInExt4.txt in Linux-DATA partition and then I booted Windows and verified that it was anable to "see" the new partition, I started again Ubuntu and verified that the test file was still present! Very well: windows did not cancel the test file!

I also verified that a file created by Ubuntu in the DATA partition (NTFS), disappeared with the running of Windows, as always, on my PC :(

[b]Now I can finally work in peace with the PC saving files in Linux-DATA partition (ext4), without fearing that data be deleted by Windows or other software installed on the machine.

I am willing to do some additional testing to solve the mystery, reserving the DATA partition (NTFS) for Windows and for testing.
[/b]
Claudio :)

---

