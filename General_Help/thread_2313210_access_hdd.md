---
title: "access hdd"
date: 2016-02-10
forum: General Help
---

### Post by kwstas3 on 2016-02-10
Hello everyone. I'm not expert so I'm sorry for any mistakes in advance.
So, i had a laptop (Toshiba satellite a300) and after some time the battery stopped working. after a black out, while the laptop was plugged in but switched off, it wasn't booting up. 
So, i press the button and the laptop starts normally, but after a few seconds shuts down immediately before the end of the whole process.
I gave the laptop to a person to take a look at it and he told me that the graphic card was burnt and because it is embedded with the motherboard it will be expensive to fix. i was wondering if this is valid because the screen showed some things normally. Anyway i told him if he can recover my files and he said yes, but he didn't give me all of my files because he said that i had put a password or something and it wasn't possible with other computer. lately i wanted to try it for myself and search some specific folders but with no luck. he said me that he managed to get the files through linux, so i made a usb with ubuntu, but i didn't manage to access the hdd. The laptop had pre-installed windows vista and later windows 7. Ubuntu shows the hdd as fat16 but the guy told me that this file system is very old, before xp and to try with scientific linux which is the OS that he was using. I found the scientific linux too complicated.
Now the good part. Today, i tried to open the laptop in order to see what was the problem. The laptop starts but shows that there isn't any bootable device, so i connect the usb that i have the ubuntu and boom. The laptop works perfectly. Is it possible the laptop to work fine and to have its graphic card burnt??????????????
I'm annoyed because he told me so but i'm happy because the laptop is working.
Unfortunately i still cannot access my hdd. What i need is to access the hdd to recover some specific files and after that if it is possible to work fine or to format and install OS again.

---

### Post by newbie-user on 2016-02-10
Graphics card works, apparently. There may be a bad capacitor on the motherboard somewhere that is causing intermittent issues. Anyway, you may have to mount your hdd manually. Open a terminal and run: 
```
sudo fdisk -l
```
This will show you what hard drives are available. Then you can manually mount the hdd as shown here: [https://help.ubuntu.com/community/Mount/USB]("https://help.ubuntu.com/community/Mount/USB")

---

### Post by kwstas3 on 2016-02-10
Thanks for the reply. Before today that i discovered that the laptop works i tried many things to access the hdd as an external hdd attached to my pc, but nothing. Now that i put the hdd where it belongs i have the same problem. when trying to mount the hdd manually i see the same error: wrong fs type, bad option, bad.....

---

### Post by yancek on 2016-02-10
How exactly are you trying to mount it, what specific command?  If you are getting the wrong filesystem type error, you can determine the filesystem with the command:  sudo parted -l (Lower Case Letter L in the command).

---

### Post by kwstas3 on 2016-02-11
sudo mount /dev/sd?? /media/(mount point i have made)
sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=1000,utf8,dmask=027,fmask=137 and something like this but a little differnet at the endplus some other thing similar to those but i cannot remember because i found them on the internet.

with sudo parted -l i get no file system and a flag hidden. if you want i can paste the results
also, as i said in the first post with [COLOR=#111111][FONT=Consolas]sudo fdisk -l[/FONT][/COLOR] i get as filesystem hidden fat16

---

### Post by oldfred on 2016-02-11
If the Windows partition is showing as FAT16 that has to be wrong. 
Window 7 is only NTFS.

It could be that you just need to change back to NTFS, NOT REFORMAT.
You can use Disks and just change type to 07 or NTFS, be sure not to choose format.

Not sure what versions of Ubuntu have Disks, or what equivalent is in other flavors.
You can install it in any version from Ubuntu repository.
And click on change partition, one of tiny icons.

You can also use command line if MBR(msdos)
Check partitions:
sudo fdisk -lu

 change sda1 to type 07, if not sda1 change to correct number.
sudo sfdisk --change-id /dev/sda 1 07
Note space between sda & partition 1 and 07 is NTFS type.

---

### Post by kwstas3 on 2016-02-11
ok. so, i go to disks
choose the specific hdd
go to settings where are 5 options available from 9
choose edit partition
and change from Hidden FAT16 (0x16) to HPFS/NTFS (0X07).
Should i check the box bootable? and also, this will certainly not wipe my data out?

---

### Post by oldfred on 2016-02-11
Windows has to have boot flag on the Primary NTFS partition that has its boot files and more boot code in the PBR or partition boot sector that tells Windows to boot from bootmgr (or with XP ntldr).

That will not reformat drive, And you want boot flag if that is your Windows boot partition.
You may still need chkdsk from Windows repair console.

Hidden may be assigned to vendor recovery partitions which may also have bootmgr. Not sure otherwise, how you got FAT16?

---

### Post by kwstas3 on 2016-02-11
i changed it but with no luck.
ubuntu said that there isn't ntfs signature when i tried to mount it and windows said that the type of file system is RAW. chkdsk is not available for RAW drive.

---

### Post by oldfred on 2016-02-11
See if backup NTFS signature is valid, testdisk calls it BS or boot sector. Testdisk can restore it, or can create a new default NTFS signature. But that is (I think) still the old XP type and you have to then run chkdsk to convert to newer bootmgr version.

This was more for those who wrote grub into Partition boot sector and need to restore backup.
 You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by kwstas3 on 2016-02-11
> **oldfred said:**
> See if backup NTFS signature is valid, testdisk calls it BS or boot sector. Testdisk can restore it, or can create a new default NTFS signature. But that is (I think) still the old XP type and you have to then run chkdsk to convert to newer bootmgr version.

This was more for those who wrote grub into Partition boot sector and need to restore backup.
 You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

how can i check if backup ntfs signaturre is valid?

let me tell you that i use ubuntu 15.10 and the hdd seems to have two partition: one that is used and one unallocated space

---

### Post by oldfred on 2016-02-11
Did you looks at testdisk screen shots. It tells you if backup is a valid BS, but even if valid it is not always correct, as grub can be considered valid, but is never correct for NTFS.

May be best to see more details.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by kwstas3 on 2016-02-11
i cannot install teskdisk

---

### Post by oldfred on 2016-02-11
Are you using live installer?
It should be just 
sudo apt-get install testdisk

---

### Post by kwstas3 on 2016-02-12
i get the following error:
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  testdisk
0 upgraded, 1 newly installed, 0 to remove and 150 not upgraded.
Need to get 0 B/315 kB of archives.
After this operation, 1,238 kB of additional disk space will be used.
dpkg: unrecoverable fatal error, aborting:
 unknown group 'lp' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

here: [https://apps.ubuntu.com/cat/applications/testdisk/](https://apps.ubuntu.com/cat/applications/testdisk/) i see that available versions are up to 13.10 and i use 15.10.

ok.. i installed testdiskin windows. when i get the screen that you said before i see the status of both boot sector and backup bootsector as bad.
so backup bs button is not available. what happens if i press rebuild bs?




eventually i managed to run testdisk from ubuntu and the hdd is in the laptop (where it belongs) but nothing changed.

---

### Post by oldfred on 2016-02-12
As posted above, the rebuild BS creates a new one. But it may be Windows XP compatible. But running chkdsk from Windows should update it.

How are you booting Windows if it is broken. And your Linux update issue is another whole thread.

Post the link to the summary report from Boot-Repair. I now am concerned we may be trying to repair the wrong partition or creating more issues. Need to see details.

---

### Post by kwstas3 on 2016-02-12
every action that i do from windows, i do it from my desktop pc. the hdd with the problem is the main drive of my laptop. if you want tell me what details i should provide. thank you very much for the help. i really appreciate it.

---

### Post by oldfred on 2016-02-12
So you have laptop hard drive plugged into Desktop PC?
That is a way to run Windows fixes.

Many create a Windows repairCD or flash drive so they do not have to remove drive. And keep the Ubuntu installer flash drive to use for emergency boot or repairs.

       Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

   [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)

---

### Post by kwstas3 on 2016-02-12
yes. i've tried with repair disk but nothing happened.
what i told with the read error is not right.
i thought that it got stucked, so i stopped it. but i downloaded a programm called hd tune and run a quick error scan. only one square (152 MB) is damaged and i think that this is the point of read error. now the testdisk is searching the drive but i have to wait. when i stopped the searching from testdisk i managed to see some files but not all of them. i suppose that if the scaning finish i will see my files.

---

### Post by oldfred on 2016-02-12
If you can see files with testdisk and do not have backups, make backups immediately.

Testdisk also has photorec which just scans drive for files, but does not recover file names, just extensions. It can take a long time to figure out which file is which.

---

### Post by kwstas3 on 2016-02-13
hello again. when the guy told me that my laptop is dead i told him to save my files. and he saved only some files. eventually my laptop works and i want to save some specific files that he didn't save. now that the scannning is finished i get these results(after deep search):[ATTACH=CONFIG]267272[/ATTACH]  the thing is that i cannot find in any of this partitions the files i want. i find some files that are fewer than the backup that gave me the guy. how can i understand which of these is the boot sector?

there are only two disks now on my pc: the disk of my pc and the disk of my laptop (400GB):[ATTACH=CONFIG]267273[/ATTACH] i chose the physical drive and not the F:, is that right?

---

### Post by oldfred on 2016-02-13
I do not know Windows version, but f: looks correct.

Testdisk finds all versions or previous configurations of your system. All the old partition configurations will be d. If trying to recovery deleted partitions best to know in detail partition structure you want to recover. But it will not let you choose a combination of old partitions that overlap or are inconsistent.
If just recovering data, do the deeper search.

---

### Post by kwstas3 on 2016-02-13
I think it is the same because eventually I managed to run test disk from Ubuntu too. Anyway the files that I found was from the physical drive. Do you think that if I search the f I'll  find the other files?

---

### Post by oldfred on 2016-02-13
It should not hurt to try to see what it finds. Testdisk normally is just scanning drive, it only is when/if you tell it to write a new partition table that changes will be made to drive.

---

### Post by kwstas3 on 2016-02-15
hello again. i put the hdd back to the laptop so as to have the external drive to move files from laptop. there was only one available option fro hdd so i serched it and showed two partitions. one with * and one with P. the one wth p had some files in it. with deeper search it found some partitions (shown on the previous screenshot) with D and some of them had the same files in it. the files are fewer than the files that the guy managed to recover. i cannot understand this. does it mean that he have deleted them?

---

### Post by oldfred on 2016-02-15
If testdisk is not seeing them, either another partition or files were deleted.
You then can try photorec. It looks for anything on the drive that looks like a file, by type. But cannot recover full filename.
It took me weeks to sort thru files and find file names. It also found every deleted version of some files, so I had many copies that were slightly different versions.
If photos, they have internal data you can use to recover a file name/date.

---

### Post by kwstas3 on 2016-02-17
Is there a way to manually set the file type or I have to choose from the list? I ask because I cannot find some file types in the list and if I choose them all it will take weeks to recover the files.

---

### Post by oldfred on 2016-02-17
How large is drive and how fast is system.
When I ran it, it took overnight.
Not sure how to set a file type not in list, as it seemed like it had everything. 
If not a standard file type it then may not even be searching for that?

---

