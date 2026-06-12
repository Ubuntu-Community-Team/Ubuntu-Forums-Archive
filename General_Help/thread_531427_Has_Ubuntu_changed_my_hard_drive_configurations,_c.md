---
title: "Has Ubuntu changed my hard drive configurations, can i change them back?"
date: 2007-08-21
forum: General Help
---

### Post by bigr00 on 2007-08-21
I've had my laptop for some time now, I've installed xp trillions of times without no problems on it previously. A couple of days ago i accidentally installed ubuntu (now thats another story)  overwriting my previous OS. Well, these kind of things happen, i opened up the support forums and found out that if i want to get rid of ubuntu, i'd might just use my xp cd and everything would be ok. 

But no, things are not so simple. as they could be. After inserting my xp cd and waited for it to boot, it loads itself to the menu, where i have to choose either to install or to repair windows, it doesn't matter what i choose, the next error is, that **THERE IS NO HARD DRIVE FOUND ON YOUR COMPUTER.**
My hard drive works just fine (the BIOS hard drive test says that its 100% working) and i can use ubuntu and do various actions, which cannot be done without a hard drive (obviously).

Now since i was able to install windows perfectly, without NO problems at all before, it must have been ubuntu, that changed some configurations. I'm worried now, not that ubuntu is bad or something (its great, in fact) but i need to use windows for some homework projects (that ubuntu doesn't support).

Help a desperate student to solve this ridiculous problem.
Thanks for hearing me out.

bigr

---

### Post by jnorthr on 2007-08-21
When you reboot your machine do you see any menus or GUI presented by either xp or ubuntu ? Yes, in order for ubuntu (or any other o/s) to be used on a machine along with windows, a special utility called a super grub ( grand unified uinversal booter?) is written to the first sector of your first hard disk. Grub is given control first when your machine is booted. It should examine the various partitions on your machine and present you with a list of which o/s partitions you can boot from. Do do see anything like this ?

---

### Post by vinogans on 2007-08-21
well  I am new to linux but here go nothing ubuntu changed ur drive ext instead of ntfs or fat32 it changed it to ext2 or ext3 as u choose on setup u can re format your hard from live cd as in the setup progress format it to fat32 or ntfs , then use command fixmbr in dos or repair consule in windows cd

---

### Post by ddrichardson on 2007-08-21
First things first. Are you saying the Windows CD doesn't boot?

---

### Post by bigr00 on 2007-08-21
> **jnorthr said:**
> When you reboot your machine do you see any menus or GUI presented by either xp or ubuntu ? Yes, in order for ubuntu (or any other o/s) to be used on a machine along with windows, a special utility called a super grub ( grand unified uinversal booter?) is written to the first sector of your first hard disk. Grub is given control first when your machine is booted. It should examine the various partitions on your machine and present you with a list of which o/s partitions you can boot from. Do do see anything like this ?
Since there is no more xp on my computer, after rebooting, i see only grub counting some numbers before starting ubuntu (i find its normal).  Thats all (there cant be anything else)

> **vinogans said:**
> well  I am new to linux but here go nothing ubuntu changed ur drive ext instead of ntfs or fat32 it changed it to ext2 or ext3 as u choose on setup u can re format your hard from live cd as in the setup progress format it to fat32 or ntfs , then use command fixmbr in dos or repair consule in windows cd
Tried that one, used Gnome Partition Editor to format the drive and tried two ways:
1) one fat32 partition (using the whole disc)
2) two partitions, one fat32 and the other ext3 (where the fat32 one was chosen as primary one)

After those actions i tried to install windows again, but got the same error as before.

> **ddrichardson said:**
> First things first. Are you saying the Windows CD doesn't boot?
It does boot and starts the installation, but on the part where i should choose to install or repair windows, it cans me with that error above.
Btw, the cd is fine aswell, used my pc to check it (it worked perfectly there)

---

### Post by ddrichardson on 2007-08-21
What happens if you leave some unpartitoned space?

---

### Post by bigr00 on 2007-08-21
> **ddrichardson said:**
> What happens if you leave some unpartitoned space?
Good one

I left the partition blank, didn't define it but still got THE error

---

### Post by ddrichardson on 2007-08-21
Boot from the live cd and post the output of fdisk -l

---

### Post by jnorthr on 2007-08-21
see, there is still an outside possibility that the windows partition is still there but not reachable. That's what we need to establish. If it's really not there you may as well toast the whole drive and rebuild it.

---

### Post by bigr00 on 2007-08-21
> **ddrichardson said:**
> Boot from the live cd and post the output of fdisk -l

[[IMG]http://img75.imageshack.us/img75/9022/screenshotuv1.th.png[/IMG]](http://img75.imageshack.us/my.php?image=screenshotuv1.png)

---

### Post by bigr00 on 2007-08-21
> **jnorthr said:**
> see, there is still an outside possibility that the windows partition is still there but not reachable. That's what we need to establish. If it's really not there you may as well toast the whole drive and rebuild it.
oh my...
I might as well give up then and persuade the professor to give me homework with programs that ubuntu supports :p

but still... I'm stubborn enough to dig deeper :D

---

### Post by ddrichardson on 2007-08-21
OK, sorry I should have been more specific - you also need to specify the drive:

fdisk -l /dev/hda for example. It needs doing as sudo too.

---

### Post by bigr00 on 2007-08-21
> **ddrichardson said:**
> OK, sorry I should have been more specific - you also need to specify the drive:

fdisk -l /dev/hda for example. It needs doing as sudo too.
Am i doing something wrong?

[[img]http://img3.freeimagehosting.net/uploads/th.b0abb2e6e9.png[/img]](http://img3.freeimagehosting.net/image.php?b0abb2e6e9.png)

---

### Post by ddrichardson on 2007-08-21
No you just have no partiton table, hence why Windows won't install.

fdisk the hard drive and create a single fat32 partition from there.

---

### Post by bigr00 on 2007-08-21
> **ddrichardson said:**
> No you just have no partiton table, hence why Windows won't install.

fdisk the hard drive and create a single fat32 partition from there.

fdisk the drive? Sorry, i'm kinda new to ubuntu and dont know how to do that, I'd need a little push here :)

---

### Post by ddrichardson on 2007-08-21
Assuming the drive is the first ide master:

```
sudo fdisk /dev/hda
```

Follow the options, its fairly straight forward. Delete any partitions (there doesn't appear to be any) create a partition, select primary and use the default values suggested to use all the drive.

Change the filesystem type to fat32, hit w to commit changes and you should have your partition table back,

---

### Post by maybeway36 on 2007-08-21
I dont think you have windows on your computer anymore. You just said you overwrote your previous OS, right?

---

### Post by bigr00 on 2007-08-21
> **ddrichardson said:**
> Assuming the drive is the first ide master:

```
sudo fdisk /dev/hda
```

Follow the options, its fairly straight forward. Delete any partitions (there doesn't appear to be any) create a partition, select primary and use the default values suggested to use all the drive.

Change the filesystem type to fat32, hit w to commit changes and you should have your partition table back,
it gets weirder 
[A PIC]("http://xs218.xs.to/xs218/07342/Screenshot-2.png")



> **maybeway36 said:**
> I dont think you have windows on your computer anymore. You just said you overwrote your previous OS, right?

Thats correct, no windows, just ubuntu

---

### Post by ddrichardson on 2007-08-21
Look in /dev for sd* and hd* devices.

---

### Post by bigr00 on 2007-08-22
> bigr@vehmer:~$ sudo fdisk /dev
Password:
You will not be able to write the partition table.

Unable to read /dev
bigr@vehmer:~$ 

this is what i get

---

### Post by ddrichardson on 2007-08-22
You can't fdisk /dev

You need to:
```
ls /etc/sd*
ls /etc/hd*
```

From the live cd to see what devices are available.

---

### Post by bigr00 on 2007-08-22
> **ddrichardson said:**
> You can't fdisk /dev
.

my bad :(

ok, here's the result:

> bigr@vehmer:~$ ls /etc/hd*
/etc/hdparm.conf
bigr@vehmer:~$ 

---

### Post by ddrichardson on 2007-08-22
OK - third time lucky```
ls /dev/hd*
```
I typed etc by mistake.

---

### Post by bigr00 on 2007-08-22
> bigr@vehmer:~$ ls /dev/hd*
ls: /dev/hd*: No such file or directory

third time lucky indeed...

---

### Post by ddrichardson on 2007-08-22
what about /dev/sd*

---

### Post by bigr00 on 2007-08-22
now we're getting somewhere

> bigr@vehmer:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5
bigr@vehmer:~$

and after that i fdisked it

> bigr@vehmer:~$ sudo fdisk /dev/sda
Password:

The number of cylinders for this disk is set to 14593.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): m
:hint: notice number 2
thats the problem i'm having

how can i get rid of that? :)

---

### Post by ddrichardson on 2007-08-22
The 1024 limitation hasn't been a problem for Linux for years, but still is for Windows.

If you intend to install windows and don't mind starting all over again then delete all the partitions and leave it unallocated. Fat32 has problems with very large drives that NTFS doesn't.

---

### Post by bigr00 on 2007-08-22
> **ddrichardson said:**
> The 1024 limitation hasn't been a problem for Linux for years, but still is for Windows.

If you intend to install windows and don't mind starting all over again then delete all the partitions and leave it unallocated. Fat32 has problems with very large drives that NTFS doesn't.

If i delete the partitions and leave it unallocated then the default number of cylinders automatically goes to 1024 ? or undefined?

Ok, i'll try it out now
wish me luck

---

### Post by ddrichardson on 2007-08-22
Its not the number of cylinders its that bootloaders don't always work installed beyond the 1024th cylinder.

---

### Post by bigr00 on 2007-08-23
An update then...
 
I deleted the partition(s) in live cd mode and made a new partition renaming the cylinders starting from 1 to 1024 (second try was 1 - 1023)

But still got pwnd by windows installer, wishing me good luck finding my hard drive.

So the problem is still up!


It seems even after I define the cylinder range, something changes is right back (if i reboot the live cd and take a peek after defining it) to 14593.](*,)

---

### Post by regomodo on 2007-08-23
> **bigr00 said:**
> After inserting my xp cd and waited for it to boot, it loads itself to the menu, where i have to choose either to install or to repair windows, it doesn't matter what i choose, the next error is, that **THERE IS NO HARD DRIVE FOUND ON YOUR COMPUTER.**


bigr

A very normal thing. Ubuntu, by default, uses the ext3 Filesystem. Windows being windows cannot see that and will just say that error you are getting. The XP installer cannot even delete that partition, i believe. I may be wrong so try to delete the Ubuntu partition there 1st. If you can't read on.

What you need to do is use your Ubuntu Live cd and use the gparted application to delete the partitons. You don't need to create a NTFS partition, just delete the partitions ubuntu made. Most likely the OS and swap partition.

Now, when you startup the xp cd again the installer will now tell you that you have a hdd/partiton that you can install xp to.

Hope that helps.

[edit] just read more of this thread. seems you are having more issues.

About this fdisk issue i see you're having i cannot understand why you are being told to do a sudo fdisk -l /dev/.......
All you need is a sudo fdisk -l   It should list all the partions on the devices it can see.

---

### Post by bigr00 on 2007-08-23
> **regomodo said:**
> A very normal thing. Ubuntu, by default, uses the ext3 Filesystem. Windows being windows cannot see that and will just say that error you are getting. The XP installer cannot even delete that partition, i believe. I may be wrong so try to delete the Ubuntu partition there 1st. If you can't read on.

What you need to do is use your Ubuntu Live cd and use the gparted application to delete the partitons. You don't need to create a NTFS partition, just delete the partitions ubuntu made. Most likely the OS and swap partition.

Now, when you startup the xp cd again the installer will now tell you that you have a hdd/partiton that you can install xp to.

Hope that helps.

I've tried that one and leaving the partition undefined, it still gets hammered by something and changes the cylinders to a number that windows has no clue what to do with

Even if i make a new fat32 partition, i get the wonderful "find your hard drive" error

---

### Post by tone39 on 2007-08-23
Hi 
I have had this problem in the past and you will need to use a little aplication called "killdisk"
I think it is still available as a download free for one pass that usually does the trick
[www.killdisk.com](www.killdisk.com)
Good luck workd for me
tone39

---

### Post by luvr on 2007-08-23
You seem to be going round and round in circles, and I'm pretty confused about what you did or did not do so far, so, if you don't mind, could you post the output of the following command here:
```
sudo fdisk -l
```
(the option being *"minus lowercase ell*'). That should give a clear idea of the current state of your harddisk(s). I'm hesitant to suggest any further actions until I understand the current situation.

Just to be clear: You did say that the Windows XP installation CD boots OK, but then it tells you that it cannot find any harddisks, didn't you?

---

### Post by ddrichardson on 2007-08-23
Why are you defining the cylinder range? You need only have the bootloader (Windows) before the 1024th cylinder. If fdisk cannot create a single unpartioned space then you need to get hold of another disk and confirm that the controller is serviceable.

If it is there is something wrong physically with the hard drive. SMART detection will not be very helpful with an unpartioned disk - try testing it with the manufacturers tools.

---

### Post by regomodo on 2007-08-23
> **ddrichardson said:**
> 

If it is there is something wrong physically with the hard drive. SMART detection will not be very helpful with an unpartioned disk - try testing it with the manufacturers tools.

What he said. When i messed with osx86 i totally borked a drive. Gparted, fdisk, cfdisk, qtparted etc did not work. I had to get a manufacturer tool and set the drive to zeroes.

[http://forum.insanelymac.com/index.php?showtopic=47671&hl=](http://forum.insanelymac.com/index.php?showtopic=47671&hl=)

---

### Post by bigr00 on 2007-08-23
> **tone39 said:**
> Hi 
I have had this problem in the past and you will need to use a little aplication called "killdisk"
I think it is still available as a download free for one pass that usually does the trick
[www.killdisk.com](www.killdisk.com)
Good luck workd for me
tone39
Ok, tried that one, didnt work, STILL getting the error (waited 3 hours for killdisk to delete everything)

> **luvr said:**
> You seem to be going round and round in circles, and I'm pretty confused about what you did or did not do so far, so, if you don't mind, could you post the output of the following command here:
```
sudo fdisk -l
```
(the option being *"minus lowercase ell*'). That should give a clear idea of the current state of your harddisk(s). I'm hesitant to suggest any further actions until I understand the current situation.

Just to be clear: You did say that the Windows XP installation CD boots OK, but then it tells you that it cannot find any harddisks, didn't you?
there ya go
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$ 
Yes, i said the XP installation disk boots just fine and after the routine part where i choose either to install or repair windows i get the error that i dont have any hard drives in my computer.

> **regomodo said:**
> What he said. When i messed with osx86 i totally borked a drive. Gparted, fdisk, cfdisk, qtparted etc did not work. I had to get a manufacturer tool and set the drive to zeroes.

[http://forum.insanelymac.com/index.php?showtopic=47671&hl=](http://forum.insanelymac.com/index.php?showtopic=47671&hl=)
Now thats good... i'll get right on it

---

### Post by bigr00 on 2007-08-23
Anyone has a good tip how to identify whats the manufacturer of my hard drive?

edit:
I'd need a bit help, really, i'm new to ubuntu and don't even know the basics yet.

So is there an Everest type of program for ubuntu aswell? Where i can see who manufactured my hard drive

---

### Post by bigr00 on 2007-08-23
i'm not joking :confused:

---

### Post by luvr on 2007-08-23
> **bigr00 said:**
> Anyone has a good tip how to identify whats the manufacturer of my hard drive?
Try
```
sudo lshw
```
(*"LiSt HardWare"*). That will produce a list of all *(identifiable)* hardware in your machine, and identify the vendors.

> **bigr00 said:**
> there ya go
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
ubuntu@ubuntu:~$
Good--That tells me that there's one 120-GB harddisk in your system, and Ubuntu refers to it as **/dev/sda.**

Now, since Windows XP seems to be confused about it, I would zap it--i.e., wipe out the Master Boot Record (including the partition table)--a bit like **regomodo** suggested when he said:
> **regomodo said:**
> I had to get a manufacturer tool and set the drive to zeroes.
You don't need to wipe the whole harddisk surface, though (that will take quite a long time); just the Master Boot Record will do--i.e., the first 512 bytes of the disk. It won't hurt, however, to zap a few extra sectors; personally, whenever I need to do these types of things, I zap at least the first track (which, as the fdisk output shows, is 63 sectors).

You don't need any extra software to do this--Linux includes the **dd** utility (*"dump data"* or some such; some prefer to call it *"destroy disk,"* because it lets you lose all data on a disk in just a few seconds...:wink:).

Now, to zap the first few (say, 63) sectors (where one sector is 512 bytes), you can simply run the following command:
```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=63
```
(where *"if"* stands for *input file,* *"/dev/zero"* is a device that produces as many null bytes as you request, *"of"* stands for *output file,* *"/dev/sda"* is your harddisk, *"bs"* means *block size,* and *"count"* specifies the number of blocks).

Next, try and boot the Windows XP installation CD, and see if it can figure out your harddisk now--it most likely will, and if it does, everything is fine.

If Windows still doesn't see your disk, then you can try and rerun the **dd** command, followed by
```
sudo fdisk /dev/sda
```
You will receive a warning that the partition table (or the Master Boot Record--I don't remember exactly) is invalid, and will be recreated when you perform a write. Thus, execute the **w** (*"write"*) command from within *fdisk,* followed by **q** (*"quit"*). *(In my opinion, though, if it didn't work **without** the extra "fdisk" step, it most likely won't work **with** it either; I would suggest that you try first **without** it.)*

---

### Post by bigr00 on 2007-08-23
> **luvr said:**
> Try
```
sudo lshw
```
[QUOTE]st
             configuration: driver=ahci latency=0
             resources: ioport:13f0-13f7 ioport:15f4-15f7 ioport:1370-1377 ioport:1574-1577 ioport:40d0-40df iomemory:f4585000-f45853ff irq:17
           *-disk
                description: SCSI Disk
                product: TOSHIBA MK1234GS
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: AH00
                serial: 478YFQO5S
                size: 111GB
                configuration: ansiversion=5

Got it...


```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=63
```
Didn't work :(


```
sudo fdisk /dev/sda
```
didn't work either

Thanks for bothering tho :(

I think its better if I post a picture of the error
[[IMG]http://aycu30.webshots.com/image/24269/2000514006940210884_th.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2000514006940210884)

---

### Post by ddrichardson on 2007-08-23
If that hasn't worked then you need to test the drive in another machine, it looks like it may have gone to silicon heaven.

---

### Post by bigr00 on 2007-08-23
> **ddrichardson said:**
> If that hasn't worked then you need to test the drive in another machine, it looks like it may have gone to silicon heaven.

I can install ubuntu perfectly, download files, run games just fine, the drive is ok.

Like i said, the BIOS drive test says its 100% working

---

### Post by bigr00 on 2007-08-23
I read the first line of my error and got me thinking, its referring to some kind of hard drive drivers

Worth a shot...

---

### Post by ddrichardson on 2007-08-23
Are you saying that its only windows that wont recognise the disk?

---

### Post by bigr00 on 2007-08-23
> **ddrichardson said:**
> Are you saying that its only windows that wont recognise the disk?
The only problem i'm facing is, that windows installation buggs me, everything else is super-duper

Thats what i tried to say in the beginning aswell ....

---

### Post by ddrichardson on 2007-08-23
If it is only windows then there is the possibility of sata being disabled in bios (unlikely) something lurking on the drive - possible and rectifiable by overwriting the entire disk with zeros.

There is also the possibility of a problem in bios - easy to check, reset the cmos by setting the cmos reset jumper and powering on, waiting around 10-15 secs and turning off then replacing the jumper. People will tell you to remove the battery, it does the same thing.

There is at least one virus that can reside in CMOS, but its really rare.

This machine doesn't have some kind of raid controller does it? Lastly is this a plain vanilla windows disk or one of those retore cds?

---

### Post by bigr00 on 2007-08-23
> **ddrichardson said:**
> 
There is also the possibility of a problem in bios - easy to check, reset the cmos by setting the cmos reset jumper and powering on, waiting around 10-15 secs and turning off then replacing the jumper. People will tell you to remove the battery, it does the same thing.

There is at least one virus that can reside in CMOS, but its really rare.

This machine doesn't have some kind of raid controller does it? Lastly is this a plain vanilla windows disk or one of those retore cds?
resetted cmos all the same

i'm not familiar with the term raid controller, how can i check for it?

it used to be one of those restore one, before ubuntu overwrote everything

---

### Post by ddrichardson on 2007-08-23
Hallelujah - if the cd is a restore disk - it usually requires a restore partition. Which is not there.

---

### Post by bigr00 on 2007-08-23
> **ddrichardson said:**
> Hallelujah - if the cd is a restore disk - it usually requires a restore partition. Which is not there.
oh you meant the cd... its plain installation cd 

i thought... never mind, too much beer makes wonders

---

### Post by luvr on 2007-08-24
> **bigr00 said:**
> [QUOTE=luvr;3240884]```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=63
```
Didn't work :([/QUOTE]
*"Didn't work"* as in *"The **dd** command gave me an error"* (and, if so, what exactly was the error?°), or *"Didn't work"* as in *"The **dd** command seems to have done OK, but the Windows XP installation still fails to recognise the disk"*?

Anyway, it looks to me like the disk is a SATA drive, which Windows XP most likely won't see without some extra help. During its startup phase, the Windows XP installation process displays a text that you may press a key (I think it's **F6,** but I'm not entirely sure) if you need to load extra drivers. That's most likely what you will have t do (but, obviously, you wll have to obtain the appropriate drivers first).

Otherwise, it may be a question of reconfiguring your IDE and SATA settings in BIOS; there may be a *"legacy"* setting or some such in there somewhere that you may want to experiment with.

---

### Post by regomodo on 2007-08-24
> **luvr said:**
> *"Didn't work"* as in *"The **dd** command gave me an error"* (and, if so, what exactly was the error?°), or *"Didn't work"* as in *"The **dd** command seems to have done OK, but the Windows XP installation still fails to recognise the disk"*?

Anyway, it looks to me like the disk is a SATA drive, which Windows XP most likely won't see with some extra help. During its startup phase, the Windows XP installation process displays a text that you may press a key (I think it's **F6,** but I'm not entirely sure) if you need to load extra drivers. That's most likely what you will have t do (but, obviously, you wll have to obtain the appropriate drivers first).

Otherwise, it may be a question of reconfiguring your IDE and SATA settings in BIOS; there may be a *"legacy"* setting or some such in there somewhere that you may want to experiment with.

i believe you have to set the mode of sata drives to ide in BIOS. If you can't do that then you need to get sata drivers for your mobo and load them (via floppy) when the xp cd says to do so.

---

### Post by bigr00 on 2007-08-24
Guys, first of all, I'd like to say thanks you all for trying to help me out, but the solution to the problem was not logical and suprising.

I had to disable SATA from BIOS and everything cleared out (weird)

problem solved, i hope it helps someone out in the future

---

### Post by luvr on 2007-08-24
> **bigr00 said:**
> I had to disable SATA from BIOS and everything cleared out (weird)
Yes, those BIOS settings are often awfully confusing, aren't they?

My guess is that *"disabling SATA"* really makes the SATA interface emulate traditional IDE. Most likely, one of the two IDE interfaces (if your computer has two of these) will be disabled, so SATA can take its place.

---

### Post by ddrichardson on 2007-08-24
Glad it's all working. You could mark this thread as solved to help anyone with a similar problem.

---

