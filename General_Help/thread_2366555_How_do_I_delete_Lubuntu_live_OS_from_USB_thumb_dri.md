---
title: "How do I delete Lubuntu live OS from USB thumb drive?"
date: 2017-07-19
forum: General Help
---

### Post by AbleTassie on 2017-07-19
All,

I finally figured out that I can boot off the USB of my PC which is 9 years old. I have two thumb drives, 8GB and 16 GB. So I made two USB thumb drives with a copy of Lubuntu on each of them using the** startup disk creator** to allow a live boot off a USB port. Both thumb drives worked great as live boots. 

I want to now **(1)** delete the Lubuntu OS off of the drives and return them to use as regular thumb drives, OR **(2)** alternatively I want to allow a live boot USB with persistence & that also has the capability to be used for storage of files as a regular thumb drive.

Naiively I tried to delete Lubuntu from the 8GB drive while in PCManFM. It tried, but gave me error messages. Even though the files on the 8GB drive may have changed some, I can still live boot my PC off the 8GB drive.

I gather that I have to use GParted (or similar more advanced software) to do what I want, but I get some error messages (see attached screen shots). It appears, for example, that there is a difference in physical block size in terms of bytes in the 8GB drive as assessed by Linux or the "driver descriptor." I know you have to be careful with GParted or you can mess things up badly.

QUESTION: Can anybody tell me how to accomplish what I want to do?

Thanks,

A.

[ATTACH=CONFIG]276046[/ATTACH][ATTACH=CONFIG]276047[/ATTACH]
[ATTACH=CONFIG]276043[/ATTACH][ATTACH=CONFIG]276044[/ATTACH][ATTACH=CONFIG]276045[/ATTACH]

---

### Post by warmango on 2017-07-19
plug it into the PC, open your native file manager, and right click the USB drive,and format like you would on windows

---

### Post by vasa1 on 2017-07-19
I use [mkusb]("https://help.ubuntu.com/community/mkusb") for dealing with pen drives. Its developer is [sudodus]("https://ubuntuforums.org/member.php?u=1499021") who's readily available to answer any difficulties you may encounter.

---

### Post by sudodus on 2017-07-19
> **vasa1 said:**
> I use [mkusb]("https://help.ubuntu.com/community/mkusb") for dealing with pen drives. Its developer is [sudodus]("https://ubuntuforums.org/member.php?u=1499021") who's readily available to answer any difficulties you may encounter.

Yes, if you need help to use mkusb, I'm here.

It should work well along both routes,

(1) delete the Lubuntu OS off of the drives and return them to use as regular thumb drives, OR

(2) alternatively I want to allow a live boot USB with persistence & that also has the capability to be used for storage of files as a regular thumb drive.

---

### Post by yancek on 2017-07-19
You can easily us GParted to simply Create New Partition Table on the usb.  That option is under the Device tab on GParted.  If you have multiple hard drives/usb's attached, make sure you have the correct one selected from the drop down arrow in the upper right of the GParted window.  You would need to not be using the usb you are trying to create the new partition table on and the same is you are going to format it.

---

### Post by mastablasta on 2017-07-19
obviously you can't tdelete it if it is in use (e.g. you ran the live OS form it and now you would like to delete it in same session). well actually maybe you could but it needs some command line magic (like unmounting and possibly turning the deksotp off).

---

### Post by AbleTassie on 2017-07-19
Thanks for your suggestions everybody. If I need to reformat the drives to FAT32 as they were before making them into live bootable USBs,  can I do this with GParted or mkusb or both? 

Warmango, what is the "native file manager"? If it is PCManFM that is in Lubuntu, I tried what you suggested and it did not work as far as I can tell.

Thanks again,

A.

---

### Post by monkeybrain20122 on 2017-07-19
> **AbleTassie said:**
> Thanks for your suggestions everybody. If I need to reformat the drives to FAT32 as they were before making them into live bootable USBs,  can I do this with GParted or mkusb or both? 

Warmango, what is the "native file manager"? If it is PCManFM that is in Lubuntu, I tried what you suggested and it did not work as far as I can tell.

Thanks again,

A.

I don't know about Lubuntu, but in Ubuntu there is a disk utility, just open it, it will detect your usb drive and choose reformat in the menu. You can always use gparted, but it is not installed by default so you need to install it. Start gparted, click "device" to locate your usb drive (it has to be plugged in of course) and then  right click >  "format to". Just make sure you have the correct drive, refromating will wipe everything.

---

### Post by sudodus on 2017-07-19
> **AbleTassie said:**
> Thanks for your suggestions everybody. If I need to reformat the drives to FAT32 as they were before making them into live bootable USBs,  can I do this with GParted or mkusb or both? 

Warmango, what is the "native file manager"? If it is PCManFM that is in Lubuntu, I tried what you suggested and it did not work as far as I can tell.

Thanks again,

A.

You can do it with mkusb. And in many cases (but not always) you can do it with gparted and Disks alias gnome-disks.

If mkusb fails, I am afraid, that the USB pendrive is damaged. See this link, [Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

### Post by AbleTassie on 2017-07-19
I am in kind of a hurry right now and will experiment with GParted and  mkusb soon -- thanks to everybody for the info about them. But I would like to use one USB drive as soon as possible  (ASAP). I did what MonkeyBrain suggested using the default disk utility in Lubunut, see screen shot that shows the formatting commands I asked for. But after formatting the USB drive is not sensed or mounted by the PCManFM for  some reason. The USB drive is still sensed by the PC however (again see  screen shot after formatting). 

QUESTION: What more must I do for the thumbdrive to  be sensed by PCManFM so that I can copy and paste to (and from) it.

Thanks, 

A.

[ATTACH=CONFIG]276057[/ATTACH]

---

### Post by AbleTassie on 2017-07-19
I am in kind of a hurry right now and will experiment with GParted and  mkusb soon -- thanks to everybody for the info about them. But I would like to use one USB drive as soon as possible  (ASAP). I did what MonkeyBrain suggested using the default disk utility in Lubunut, see screen shot that shows the formatting commands I asked for. But after formatting the USB drive is not sensed or mounted by the PCManFM for  some reason. The USB drive is still sensed by the PC however (again see  screen shot after formatting). 

QUESTION: What more must I do for the thumbdrive to  be sensed by PCManFM so that I can copy and paste to (and from) it.

Thanks, 

A.

[ATTACH=CONFIG]276058[/ATTACH]

---

### Post by sudodus on 2017-07-19
You need not only the basic partition table, but also a partition and a file system in the partition.

mkusb makes it straightforward to restore the USB pendrive to a standard storage device with an MSDOS partition table and a FAT32 partition (a partition with a FAT32 file system). But it is possible with another tool too, unless there is some data, that is confusing that tool. The crucial thing done by mkusb is to wipe the first megabyte (overwrite with zeros), which removes data that might confuse various tools, but mkusb can run the whole process.

---

### Post by lammert-nijhof on 2017-07-19
Use the standard disk utility that comes with any Ubuntu flavor. Don't try to delete the partition, that will be rejected. 
1. First format the complete disk in MBR/DOS format using the menu sign in the top right corner of the disk utility window. 
2. Create a partition in the free space, use the + sign under the large free space bar. Ignore a possible crash, just restart the Disk Utility. 
3. Format the partition by selecting it from the gears symbol below the large free space bar.

You should select "Don't overwrite existing data", unless you have a enough free time to wait for the system to write zeroes to the whole USB Stick.

---

### Post by AbleTassie on 2017-07-19
OK thanks everybody. Because of limited time, I did the procedure Lammert described and that took care of it. 

A.

---

### Post by AbleTassie on 2017-07-20
I have two USB thumb drives (8GB and16 GB) and I am interested in having two usb drives that can live boot Lubuntu and also have persistence as well as have some space for storage of data just like a normal USB thumb drive. It looks like there are various tools that can accomplish this: GParted, mkusb/guidus, UNetbootin, perhaps Disks and Startup Disk Creator. 

I would like to just read as much as I need to about the various tools above and try experimenting with them to get a feel for them to get to my goal. I know that I can lose data on the thumbdrives (which is backed up and can always be recovered and reused), but I just do not want to damage the thumb drives (or any other drive) in the process of experimenting. In some of my reading Sudodus suggested not wiping a drive clean too often due to shortening the life of the thumb (pen) drive.

QUESTION: Is there anything I should not do that would really cause damage to the thumb drives (or any drive)?

Any other comments or cautions would be welcomed.

Thanks,

A.

---

### Post by sudodus on 2017-07-20
As you mentioned, do not wipe the whole drive clean too often. For example, you can do it when the write speed is reduced to half of the original speed.

If you use the drive as a persistent live drive, it should work for a long time. Problems are usually caused by damages of the file system of the 'casper-rw' partition or file for persistence, and the USB drive or memory card itself is still healthy.

If you *install* an operating system in a pendrive (installed like into an internal drive, but into a USB pendrive or memory card), you must take special care to avoid excessive wear. There are details at this link, [help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks). Typical operating systems for Raspberry Pi are installed like this, and there are several reports of memory cards that are damaged beyond repair (gridlocked or completely dead).

Electric shock (for example static electricity) can kill any electronic device, also USB pendrives and memory cards.

---

### Post by AbleTassie on 2017-07-20
> **sudodus said:**
> As you mentioned, do not wipe the whole drive clean too often. For example, you can do it when the write speed is reduced to half of the original speed.

If you use the drive as a persistent live drive, it should work for a long time. Problems are usually caused by damages of the file system of the 'casper-rw' partition or file for persistence, and the USB drive or memory card itself is still healthy.



Thanks Sudodus,

I have some questions for you or anybody else who wants to weigh in. In reading about the casper-rw partition, I came across the description below:
(at [https://stackoverflow.com/questions/2566121/what-is-casper-rw-loop-file-and-why-do-i-need-it-to-make-saving-persistant-on-us):](https://stackoverflow.com/questions/2566121/what-is-casper-rw-loop-file-and-why-do-i-need-it-to-make-saving-persistant-on-us):) 

"You may think, "well why not just do it as a directory on the stick?"   The reason for this is that a FAT32 filesystem doesn't have all the  metadata that a Unix environment needs.  You need to use something like  ext2.

  [B]So what is a casper file?  It's a file that has been treated like  it's a hard drive partition.  That's it.  Instead of pointing mkfs.ext2  or mount at /dev/sda3 (a partition), you've pointed it at  /mnt/sda3/casper-rw (a file)."

[/B]QUESTION(S): If the above is true, then does that mean I only need one partition on the thumb drive (the casper-rw partition) for both **(1)** persistence during a live boot and **(2)** regular use to store data when booting off the hard drive? That is, one partition (the casper-rw partition) in addition to the partition the Lubuntu live boot OS is on in the thumb drive?

Or do I need three partitions on the thumb drive: one for the Lubuntu live boot OS, one for persistence (casper-rw) and one for storing data during a regular boot off the hard drive?

Thanks,

A.

---

### Post by sudodus on 2017-07-20
> **AbleTassie said:**
> ...

QUESTION(S):

If the above is true, then does that mean I only need one partition on the thumb drive (the casper-rw partition) for both **(1)** persistence during a live boot and **(2)** regular use to store data when booting off the hard drive? That is, one partition (the casper-rw partition) in addition to the partition the Lubuntu live boot OS is on in the thumb drive?

When there is only one FAT32 partition that is filling the whole USB pendrive, the available method to create persistence is to make a file with a file system inside, a 'casper-rw' file. But there are disadvantages, for example that the size is limited to 4 GB (the maximum file size in FAT32). You may think that it is an alternative to have a FAT32 partition for the file system and an ext partition with a 'casper-rw' label for persistence, but it does not work (at least not with Ubuntu and the Ubuntu family flavours), when you use the standard boot system (booting via syslinux in BIOS mode).
> 
Or do I need three partitions on the thumb drive: one for the Lubuntu live boot OS, one for persistence (casper-rw) and one for storing data during a regular boot off the hard drive?

If you create a USB pendrive, that boots via grub (both in BIOS mode and in UEFI mode), it is possible to use a partition for persistence.

It might be possible to do this with 3 partitions,

[LIST]
[*]a boot partition, which is also an EFI partition, 
[*]a partition for the system (basically a copy of the content of the iso file)
[*]a partition with a 'casper-rw' label for persistence
[/LIST]

But I extended the partition table to 5 partitions in the persistent live systems made with mkusb:

[LIST]
[*]partition #1 (located at the tail end of the drive) with the NTFS file system is intended for storage and transfer of data. You can read and write files to this partition both both linux and Windows. There is no size limit for the files.
[*]partition #2 either a bios_grub partition (in GPT), or an extended partition (in an MSDOS partition table)
[*]partition #3, a boot and efi partition
[*]partition #4, with a cloned image of the iso file (containing the system)
[*]partition #5, with a 'casper-rw' label for persistence
[*]
[/LIST]

---

### Post by AbleTassie on 2017-07-20
> **sudodus said:**
> When there is only one FAT32 partition that is filling the whole USB pendrive, the available method to create persistence is to make a file with a file system inside, a 'casper-rw' file. But there are disadvantages, for example that the size is limited to 4 GB (the maximum file size in FAT32). You may think that it is an alternative to have a FAT32 partition for the file system and an ext partition with a 'casper-rw' label for persistence, but it does not work (at least not with Ubuntu and the Ubuntu family flavours), when you use the standard boot system (booting via syslinux in BIOS mode).

If you create a USB pendrive, that boots via grub (both in BIOS mode and in UEFI mode), it is possible to use a partition for persistence.

It might be possible to do this with 3 partitions,

[LIST]
[*]a boot partition, which is also an EFI partition, 
[*]a partition for the system (basically a copy of the content of the iso file) 
[*]a partition with a 'casper-rw' label for persistence 
[/LIST]

But I extended the partition table to 5 partitions in the persistent live systems made with mkusb:

[LIST]
[*]partition #1 (located at the tail end of the drive) with the NTFS file system is intended for storage and transfer of data. You can read and write files to this partition both both linux and Windows. There is no size limit for the files. 
[*]partition #2 either a bios_grub partition (in GPT), or an extended partition (in an MSDOS partition table) 
[*]partition #3, a boot and efi partition 
[*]partition #4, with a cloned image of the iso file (containing the system) 
[*]partition #5, with a 'casper-rw' label for persistence 
[/LIST]



Thanks Sudodus,

I've been doing more reading. I think my computer (circa 2008) does not use EFI/UEFI. When I run the terminal command "dmesg | grep "EFI v"" I get nothing.

In  the three partition solution you give, can the casper-rw partition be  used for regular storage of data (in both linux and windows)?

 In  your 5 partition solution with mkusb your partition #5 for persistence  is a different partition than  #1 for storage of regular files. What is  the advantage of using 5 partitions like this instead of fewer  partitions?

One of the reasons I am interested in persistence is  so that I can use the latest version of a web browser (e.g,, Firefox) to  browse the internet during a live session -- better security I'm told.  The downloaded version of Lubuntu 16.04.2 LTS does not contain the  latest version of Firefox. If the latest version of Firefox were in the  persistent partition, I assume it would still have to be reinstalled for  each USB boot live session after the system boots up. Is this correct?   

Similarly if Libre Office Writer were stored in persistence, it  too would have to be reinstalled for each USB boot live session after  the system boots up. Is this correct? 

Thanks,

A.

---

### Post by sudodus on 2017-07-21
> **AbleTassie said:**
> Thanks Sudodus,

I've been doing more reading. I think my computer (circa 2008) does not use EFI/UEFI. When I run the terminal command "dmesg | grep "EFI v"" I get nothing.

You are right. A computer from 2008 is booting in the old BIOS mode.
> 
In  the three partition solution you give, can the casper-rw partition be  used for regular storage of data (in both linux and windows)?

No, the casper-rw partition has a linux file system that Windows cannot read. It might be possible to use a FAT32 partition to store files in a way, that it will be available for both linux and Windows.
> 
In  your 5 partition solution with mkusb your partition #5 for persistence  is a different partition than  #1 for storage of regular files. What is  the advantage of using 5 partitions like this instead of fewer  partitions?

Partition #1 is made for storage and transfer of data for and between linux and Windows. The whole layout is made to work in many computers running in both BIOS and UEFI mode. And it is set up automatically with only a few options for you (the end user) to set, so it is easy to make something that works.

But if you want to do it yourself from scratch, and tweak the system for your particular situation, you are welcome to borrow ideas and tips.
> 
One of the reasons I am interested in persistence is  so that I can use the latest version of a web browser (e.g,, Firefox) to  browse the internet during a live session -- better security I'm told.  The downloaded version of Lubuntu 16.04.2 LTS does not contain the  latest version of Firefox. If the latest version of Firefox were in the  persistent partition, I assume it would still have to be reinstalled for  each USB boot live session after the system boots up. Is this correct?   

What do you mean by each USB boot live session?

In a persistent live system you can install (and upgrade) application programs, for example Firefox, and the installed and/or upgraded version will persist, in other words, it will be there after reboot or shutdown and cold boot.

But it is very important that you allow the system to reboot and shutdown completely, give it time to flush the buffers in other words write the data to the 'casper-rw' partition completely. If you unplug the USB pendrive too early, the system will be damaged.

In general, persistent live systems are sensitive, and you should take frequent backups. See this link,

[Backup and restore of persistent overlay data](https://help.ubuntu.com/community/mkusb/persistent#Backup_and_restore_of_persistent_overlay_data)
> 
Similarly if Libre Office Writer were stored in persistence, it  too would have to be reinstalled for each USB boot live session after  the system boots up. Is this correct? 

Libre Office can also be upgraded and stored so that it persists after reboot or shutdown and cold boot.

But it is not possible to use an upgraded linux kernel, because the kernel is started before the overlay is activated. In general, you should *not* update & upgrade a persistent live system completely like you do with an installed system. It is likely to result in a corrupted system. Instead you should only install individual program packages and upgrade individual program packages. And you can tweak the system plus save various data files. For example:

```
sudo apt-get update
sudo apt-get install firefox
sudo apt-get install libre-office
```

will keep Firefox and Libre Office up to date.

---

### Post by AbleTassie on 2017-07-21
> **sudodus said:**
> 

Partition #1 is made for storage and transfer of data for and between linux and Windows. The whole layout is made to work in many computers running in both BIOS and UEFI mode. And it is set up automatically with only a few options for you (the end user) to set, so it is easy to make something that works. 

Thank you Sudodus,

**I want to make a USB thumb drive with live boot capability, persistence and data storage/transfer between computers in as simple a way as possible. Can you briefly tell me what to do in mkusb?**

**I want to do this so that I can sign onto public wifi with my laptop in as secure a way as possible, but also use the thumb drive for standard storage and transfer of files, perhaps to a library PC as well.** I may also want to use a VPN, the "Firejail" sandboxing application and a service like OpenDNS for interacting with the internet when on public wifi.
I have two thumb drives, and 8GB and a 16 GB, but could buy larger ones, e.g., 32GB.** Is there a preferred size?**

  
> **sudodus said:**
>  What do you mean by each USB boot live session? In a persistent live system you can install (and upgrade) application programs, for example Firefox, and the installed and/or upgraded version will persist, in other words, it will be there after reboot or shutdown and cold boot.

But it is very important that you allow the system to reboot and shutdown completely, give it time to flush the buffers in other words write the data to the 'casper-rw' partition completely. If you unplug the USB pendrive too early, the system will be damaged. 

OK, I will be careful. In a straight live boot without persistence, nothing can be written to the thumb drive, so I assume there is some increased risk of errant code, viruses, malware being written to the thumb drive when it is set up for persistence. **Is this correct? ** 

> **sudodus said:**
>  But it is not possible to use an upgraded linux kernel, because the kernel is started before the overlay is activated. In general, you should *not* update & upgrade a persistent live system completely like you do with an installed system.  

OK thanks for the instruction. I will only update manually a few apps, like Firefox and Libre Office and infrequently. I can see now that it is the kernel that is unchanged on the thumb drive, even if it is set up for persistence. Only the data in a partition for persistence can be changed. (And, of course, data in a partition that is set up for regular data storage and transfer, e.g in both Linux and Windows) can be also changed.) 

Thanks again,

A.

---

### Post by vasa1 on 2017-07-21
While it maybe convenient for a poster to have just one thread for topics that could very well deserve a new thread of their own, the topics in the thread *that aren't reflected in the thread's title* may be missed by others who feel that the thread's title doesn't reflect their interest.

For this reason, I suggest that each topic, even if somewhat related, has its own thread and that each thread be given a nice descriptive title :)

---

### Post by AbleTassie on 2017-07-21
[SIZE=2]Thanks Vasa,

[/SIZE]I will mark this thread as SOLVED.

A.

---

### Post by sudodus on 2017-07-22
> **AbleTassie said:**
> Thank you Sudodus,

**I want to make a USB thumb drive with live boot capability, persistence and data storage/transfer between computers in as simple a way as possible. Can you briefly tell me what to do in mkusb?**

I wrote the [mkusb quick start manual](https://help.ubuntu.com/community/mkusb?action=AttachFile&do=view&target=mkUSB-quick-start-manual-12.pdf) for this purpose, see particularly the pages 23-25.

You find the "full description" at the following links,

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

Please ask specific questions, if you need more help.
> 
**I want to do this so that I can sign onto public wifi with my laptop in as secure a way as possible, but also use the thumb drive for standard storage and transfer of files, perhaps to a library PC as well.** I may also want to use a VPN, the "Firejail" sandboxing application and a service like OpenDNS for interacting with the internet when on public wifi.
I have two thumb drives, and 8GB and a 16 GB, but could buy larger ones, e.g., 32GB.** Is there a preferred size?**

As you have already agreed with @vasa, it is better to discuss these items in a separate thread.
> 
OK, I will be careful. In a straight live boot without persistence, nothing can be written to the thumb drive, so I assume there is some increased risk of errant code, viruses, malware being written to the thumb drive when it is set up for persistence. **Is this correct? ** 

Yes

---

