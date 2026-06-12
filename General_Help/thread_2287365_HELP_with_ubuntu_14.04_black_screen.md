---
title: "HELP with ubuntu 14.04 black screen"
date: 2015-07-18
forum: General Help
---

### Post by chfakht on 2015-07-18
Hi all ,
i have installed ubuntu 14.04 after installing windows 7 (dual boot) a years ago and i have been working on both OS without problems
now when i boot to ubuntu i choose from the menu memtest x86 (i have just choose this option for the first time and i have no idea about it) , so i get a blue screen running memtest but the screeen take a lot of time and freezes so i have reboot my laptop and chhoose to boot from ubuntu 14.04 after a while i get the ubuntu logo and it disappear and i get after  that a black screen .
i have rebooot the laptop a lot of time but i get always the black screen .
i don"t know if tthis problem is due to trunning memtest , just to add i have noticed that i'm having 0 free space in  / folder and it could be the source of the problem 

here is q summary from repair-boot that i have installed by booting with a ubuntu from usb drive
before repairing the boot . [http://paste.ubuntu.com/11902035/](http://paste.ubuntu.com/11902035/)  ==> after [http://paste.ubuntu.com/11902038/](http://paste.ubuntu.com/11902038/)
please help me , i have found a lot of manipulations concerning this but i'm afraid to broke the systeme because i'm not an experienced linux user
thanks a lot

---

### Post by grahammechanical on 2015-07-19
Memtest will take a long time to run. The more memory we have the longer the test will take. I do not know if rebooting while the test is running will break the loading of the operating system, or not. I think that the Memtest is run under Linux and so rebooting before the test has finished could cause this problem. Does Windows 7 load correctly? You do not say.

 Boot Repair cannot fix this problem because there is no problem with the boot of Ubuntu from the boot menu. The problem comes after the boot menu has activated the Linux kernel and during the loading of Ubuntu/Linux. And Boot Repair is not designed to fix those kind of problems.

At the boot menu we can select Advanced options for Ubuntu and then select Recovery Mode. At the Recovery menu we will get options. If you think the problem is caused by a lack of free space then select

clean - try to make free space.

When back at the recovery menu you can select 

fsck - check all file systems.

Allow time for the utility to do its work. Memtest tests memory RAM. fsck checks the hard disc (file systems). 

Resume- resume normal boot

may get you to a working login screen and desktop.

Regards.

---

### Post by PaulW2U on 2015-07-19
*Thread moved to **General Help**.*

---

### Post by chfakht on 2015-07-19
thanks for replay @[[COLOR=#000000]grahammechanical[/COLOR]]("http://ubuntuforums.org/member.php?u=1087323")[COLOR=#000000] [/COLOR] ,
i have 2 memory slots 4GB in each one ... yes WINDOWS 7 does load correctly , and with also recovery mode i get the black screen , i have checked for file system error and i get that there is 2 errors but without showing what the source of those errors !!! i have free (make more free space) 2 gb of the drive but the problem persist :p
so what can i do now !!! please repond :) thanks you

---

### Post by oldfred on 2015-07-19
I see two issues, gpt and full partition.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

/dev/sda7      ext4              42G   40G     0 100% /mnt/boot-sav/sda7

Ubuntu does not normally install if you have gpt backup partition table.
Windows ignores backup gpt table, so it will work.

FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

But you still have issue of full drive. You need to do some major housecleaning or expanding of partition. Make sure you have good backups of both Windows & Ubuntu before making any changes.

You also have NTFS partitions at 91%. Windows NTFS really needs 30% free space to work well on the way it writes to partitions. System starts to get very slow at 10% free and it may take forever to do a defrag.

---

### Post by chfakht on 2015-07-19
thanks a lot @[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711") ,
yes i have forgot to tell that in the past i have re-partionned the Hard Drive 2 times to manage space between linux and windows using gparted ....
for this phrase of you , #Ubuntu does not normally install if you have gpt backup partition table.# can you explain for me that plzz because i m just a newbie ...
i notice that this was just a warning and before running memtest by curiosity* i have not got any problem 
--> so i ll began solving this first problem . 
but when i try to install fixparts i get an error 
Unpacking fixparts (0.8.8-1) ... 
dpkg: error processing archive /home/ubuntu/Downloads/fixparts_0.8.8-1_amd64.deb (--install): 
 trying to overwrite '/usr/share/man/man8/fixparts.8.gz', which is also in package gdisk 0.8.8-1build1 
Processing triggers for man-db (2.6.7.1-1ubuntu1) ... 
Errors were encountered while processing: 

thanks for your help and i it would be very helpfull for me if you give me the right commads to test 
i am wondering why linux does not use setup system to install , remove or repair anything , it was so easy to do with windows p.

---

### Post by oldfred on 2015-07-19
There is the very old MBR(msdos) partitioning table. Windows only boots in BIOS mode from MBR.
And there is the newer gpt partitioning table. Required for UEFI boot of Windows or any drive over 2TiB.
Ubuntu will actually boot from gpt with either BIOS or UEFI, but if dual booting with Windows partitioning type is set by Windows.
       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Fixparts is from same author as gdisk. And now gdisk is included in the newer Ubuntu as many installs need it. Maybe fixparts is already installed? 
Or you can use gdisk, just not quite as easy.


 sudo gdisk /dev/sda
Command (? for help): 

You have to go to advanced mode, and want just MBR(msdos) not gpt(GUID). It may try to convert to gpt. List partitions, confirm correct, and w to write updates, if not sure q to quit and no changes will be written.


 gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

### Post by chfakht on 2015-07-21
i think that [COLOR=#000000]partitioning type is set by Windows. because i get the grub in the first time not windows (i used to have windows first but i have changed that)
i don't want to do advanced command like you just telling me i'm afraid to loose all my data
i will try to repair ubuntu without removing packages + /home folder 
thanks[/COLOR]

---

### Post by oldfred on 2015-07-21
If data is at all valuable you have have good backups. And even hard drives will (when not if) fail. Sometimes catastrophically. I have had a drive fail within one year, although that is not normal. 

         The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

