---
title: "Checking RAM using Live Pendrive UBUNTU 12.04.2"
date: 2014-07-23
forum: General Help
---

### Post by anon_private on 2014-07-23
Is there a way for run a system file check for Vista using Ubuntu. Is so, please advise

Thanks

---

### Post by TheFu on 2014-07-23
Well, sorta ...

You can run an fsck.ntfs from Linux, but you shouldn't. Use the tools from the OS file system (vista) if you care about avoiding data loss and/or corruption.

Still [http://askubuntu.com/questions/86086/fsck-cant-find-fsck-ntfs](http://askubuntu.com/questions/86086/fsck-cant-find-fsck-ntfs) may be of help.> 
Keep in mind that this utility came from a reverse engineering process and are not the best option to manage your filesystem, the NTFS filesystem does not belong to the GNU/linux world.

I would use the Vista repair disk or a Windows product instead.

---

### Post by mcduck on 2014-07-23
Which one you actually want to do? Check the RAM on the computer (as the title suggests), check the integrity of the filesystem Vista is installed, or check the actual system files of Vista?

First one is easy, Ubuntu's boot menu contains option for testing RAM. (The test should be left to run for a good while, I'd recommend over night, and any errors are sign of faulty RAM or some other hardware issue).

The filesystem can be checked using fsck, but since NTFS is MIcrosoft's proprietary filesystem, checking it using Windows tools is likely to give you better results.

...and finally for checking the system files of Windows, you'll want to do that using Windows boot disk or install CD.

---

### Post by anon_private on 2014-07-24
> **TheFu said:**
> Well, sorta ...

You can run an fsck.ntfs from Linux, but you shouldn't. Use the tools from the OS file system (vista) if you care about avoiding data loss and/or corruption.

Still [http://askubuntu.com/questions/86086/fsck-cant-find-fsck-ntfs](http://askubuntu.com/questions/86086/fsck-cant-find-fsck-ntfs) may be of help.

I would use the Vista repair disk or a Windows product instead.


Thank you for responding.

I have Vista installed but it will not boot. I would like to check Vista's system files, and if corrupt, to repair them.

I am accessing the Internet through a live Linus pendrive.

From Linux (Command) I typed fsck.ntfs, but the programme did not run.

Best wishes.

A

Ps. I have had no luck with Vista's tools

> **mcduck said:**
> Which one you actually want to do? Check the RAM on the computer (as the title suggests), check the integrity of the filesystem Vista is installed, or check the actual system files of Vista?

First one is easy, Ubuntu's boot menu contains option for testing RAM. (The test should be left to run for a good while, I'd recommend over night, and any errors are sign of faulty RAM or some other hardware issue).

The filesystem can be checked using fsck, but since NTFS is MIcrosoft's proprietary filesystem, checking it using Windows tools is likely to give you better results.

...and finally for checking the system files of Windows, you'll want to do that using Windows boot disk or install CD.

Thanks for reposning.

Sorry about the tile and text conmfusion.

I have Vista installed but it will not boot. I would like to check Vista's system files, and if corrupt, to repair them.

I am accessing the Internet through a live Linux pendrive.

From Linux (Command) I typed fsck.ntfs, but the programme did not run.

Best wishes.

A

Ps. I have had no luck with Vista's tools

---

### Post by mcduck on 2014-07-25
If Microsoft's own tools have already failed, I doubt there is much you could do from Ubuntu. Like I said, fsck is just a much more feature-limited version of the filesystem check Microsoft's own tool are able to do to it's own filesystem, and there is no automatic tool in Linux for checking consistency of Windows system files.

What comes to using fsck, you need to tell it what drive & partition it should try to check. For example if Windows is on first partition of second hard drive, you'd run it like this:
```
sudo fsck -t ntfs /dev/sdb1
```
Also keep in mind the filesystem shouldn't be mounted at the time you try to check it. And if youa ren't sure about the corrrect drive/partition, fdisk can list all the drives to you:
```
sudo fdisk -l
```

---

### Post by TheFu on 2014-07-25
fdisk should NOT be used on drives with GPT or larger than 2TB. Use parted instead - I only use parted, since it works on all drives.

fsck.ntfs may not exist. It is just a link to another program - the link in my first reply explains. Did that work?
If the OS won't boot and you cannot use vista file system tools or a boot disk to fix it, I'm afraid you are out of luck. Others here may suggest going to all sorts of lengths - they usually will - my time is more valuable than theirs, I suppose. A new $100 HDD solves many problems and I'd be most likely to move on.

---

### Post by anon_private on 2014-07-25
> **TheFu said:**
> fdisk should NOT be used on drives with GPT or larger than 2TB. Use parted instead - I only use parted, since it works on all drives.

fsck.ntfs may not exist. It is just a link to another program - the link in my first reply explains. Did that work?
If the OS won't boot and you cannot use vista file system tools or a boot disk to fix it, I'm afraid you are out of luck. Others here may suggest going to all sorts of lengths - they usually will - my time is more valuable than theirs, I suppose. A new $100 HDD solves many problems and I'd be most likely to move on.

I used Disk Utility in Linux (from pendrive) to check my hard drive.

I found. 

One bad sector.
Overall assessment: Disk has a few bad sectors (green button).

Read Error Rate: Good (green button)
Spinup Time: Good (green button)
Start/stop count:N/A

My hard disk looks alright to me.

---

### Post by mcduck on 2014-07-25
While fdisk shouldn't be used for editing the partiton layout of GPT partitioned drives, it's just fine for listing the partitions (for example to simply check which is the correct device ID for the partition you want to check with fsck).

What comes to the Disk Utility, that's one more compeltely different tool with a different purpose.

- Disk Utility checks the *physical surface* of a hard drive, and reads any SMART status messages from the disk controller
- fsck checks the integrity of a *file system* (such as Ext4 or NTFS)
- Windows has it's own tools for checking the integrity of the actual *system files* it needs to run. (For example if a system file is replaced with a wrong version or corrupted file that would cause Windows to fail but everything would be normal on both physical disk level and on filesystem level)

(- and MemTest86 on Ubuntu's boot menu tests the operation of the RAM installed on the computer, which has nothing to do with any of the above)

What comes to one bad sector, that's not a problem. It's only when you see lots of them, or the bad sector count is increasing quickly, when you need to be worried about the drive failing.

---

### Post by Bucky Ball on 2014-07-25
> **anon_private said:**
> 

My hard disk looks alright to me.

Me too. The title of this thread is about checking your RAM with a Ubuntu USB, though, not checking a hard drive. So, have you resolved how to check your RAM?

---

### Post by anon_private on 2014-07-25
> **Bucky Ball said:**
> Me too. The title of this thread is about checking your RAM with a Ubuntu USB, though, not checking a hard drive. So, have you resolved how to check your RAM?

I don't think I have a RAM problem. I will retest

I believe that I have system file problem which I have been unable to check (Vista not running).

Unfortunately, I don't think that I can edit the title.

Best wishes.

Ps. I will soon be deciding whether to re-install Vista or Ubuntu 12.04.2. I find this a difficult decision.

Someone said that if I installed 12.04.2 then the latest version would be installed at the first upgrade. Does this happen automatically, and what happens if the latest version does not run as well as 12.04.2 - on my machine. Can I revert?

---

### Post by Bucky Ball on 2014-07-25
That was me, and why wouldn't that latest version work on your machine? If it's working now, nothing is going to be removed with an update. Only improved, at least that is the whole idea. 

If you have a support request, please ask ONE support request per thread, give the thread a descriptive title that is about your support request, and post it in the appropriate forum. Thanks and good luck.

---

### Post by anon_private on 2014-07-25
[QUOTE=Bucky Ball;13082607]That was me, and why wouldn't that latest version work on your machine? If it's working now, nothing is going to be removed with an update. Only improved, at least that is the whole idea. 

 The latest version od Ubuntu is ca. 14.

I am using 12.04.2 on a pendrive.

If I install 12.04.2 and upgrade presumably, I would receive ca.14

ca 14 probably requires more memory that ca 12.

So 14 may not work as well as 12.

You are helping me decide in favour of re-installing Vista. I am put off by some of your comments. Whose thread is it, mine I assume

---

### Post by sudodus on 2014-07-25
The normal updates/upgrades and updates/dist-upgrades make the version stay within 12.04 LTS, but move from 12.04.2 to 12.04.4 (I think soon 12.04.5). You need to activate another upgrade process to move to the next LTS release, 14.04. That will not happen automatically.

I am still running 12.04 LTS (now at 12.04.4) in my production computer, while I'm testing the new versions in other computers. I intend to test 14.04.1 LTS soon in my production computer, and upgrade to it, if the test shows good results.

---

### Post by Bucky Ball on 2014-07-25
> **sudodus said:**
> The normal updates/upgrades and updates/dist-upgrades make the version stay within 12.04 LTS, but move from 12.04.2 to 12.04.4 (I think soon 12.04.5). 

^^^
This.

Apologies. No offense intended. As sudodus explains, and what I was trying to say, is that you won't get upgraded to 14.04, but if you update normally you will get updated to 12.04.4. ;)

Thank you sudodus.

---

### Post by anon_private on 2014-07-29
> **Bucky Ball said:**
> Me too. The title of this thread is about checking your RAM with a Ubuntu USB, though, not checking a hard drive. So, have you resolved how to check your RAM?

Regarding the hard disk (ref. post #8)

Someone on another board suggested this.

What do you think of this advice - at the re-install stage it could be Linux,



'I've  seen this all before.. I've worked corporate IT, I've worked IT on a  college campus, and I helped run a computer repair store for 4 years. I  know the signs well. 

  You  said that you've discovered bad sectors on the disk. Modern hard drives  have a technology called SMART that keeps track of the drive condition.  Among other things, SMART can remap a small number of bad sectors,  replacing them with reserved sectors on the disk. If you ever actually *see*  bad sectors, this means the drive's on-board software has already  mapped out as many sectors as it can, and you actually have a  significant problem. Usually, when the bad sector count starts growing,  it gets worse. This doesn't always happen, but when it does, this means  you'll corrupt more and more data...'

'So here's a recap:'


  
[LIST]
[*]'Obtain a Linux live DVD (Mint or Ubuntu) or Hiren's Boot Disk. 
[*]Back up your data to a USB hard drive 
[*](optional) Install a new hard drive 
[*]Completely format the drive (NOT a quick format) 
[*]Re-install Windows 
[*]Set up maintenance cycle and scan for bad sectors every day for a week, then once a week' 
[/LIST]

---

### Post by Bucky Ball on 2014-07-29
If you have your RAM issue solved, please mark the thread as solved to help others (it won't close the thread) and please post a new thread regarding  hard drives. You will increase your chances of support with it. Good luck.

---

