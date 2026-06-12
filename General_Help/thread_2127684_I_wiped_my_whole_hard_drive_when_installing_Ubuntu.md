---
title: "I wiped my whole hard drive when installing Ubuntu 12.10"
date: 2013-03-20
forum: General Help
---

### Post by tiubles on 2013-03-20
Hi

Long story short I have an old AMD system where I was using Windows 7. It was only my testing machine since I bought my laptop. But I had so many family photos and other important on the hard drive. But today I decided to install Ubuntu 12.10, when installing I selected the option replace windows 7 and install ubuntu. I thought it will only wipe my c drive.

My freshly installed ubuntu shows blank screen after login, which is a different story. it has an nvidia chipset. In 2010 when I installed ubuntu for the first time I had to do so many things in grub settings etc to get it work. I really don't want to fix it though. I was reading some forums and I saw that it is possible to recover files with test disk using live cd. So please guys tell me how I can do this.

I just want to recover my deleted files :(

Thanks!

---

### Post by TheFu on 2013-03-20
> **tiubles said:**
> Hi

Long story short I have an old AMD system where I was using Windows 7. It was only my testing machine since I bought my laptop. But I had so many family photos and other important on the hard drive. But today I decided to install Ubuntu 12.10, when installing I selected the option replace windows 7 and install ubuntu. I thought it will only wipe my c drive.

My freshly installed ubuntu shows blank screen after login, which is a different story. it has an nvidia chipset. In 2010 when I installed ubuntu for the first time I had to do so many things in grub settings etc to get it work. I really don't want to fix it though. I was reading some forums and I saw that it is possible to recover files with test disk using live cd. So please guys tell me how I can do this.

I just want to recover my deleted files :(

You know that backup that everyone has talked about for years?  This is the time to use it.
The **testdisk **tools are more suited to recovering a few files in specific directories.  I know this isn't what you wanted to hear.

A professional data recovery outfit might do better for $3000-$4000.  If you've decided not to do that, buy another HDD, mirror everything over using ddrescue and attempt all recovery on the new HDD. DO NOT TOUCH the old drive until you have decided you are done.  Only mount it read-only. Do not boot it. Do not use it in any other way until you have it mirrored - bit-for-bit.

Any old data that was overwritten by the new install - those are gone - gone - gone.

Backups rock.  DejaDup, rdiff-backup, Duplicati, Duplicity, and many others are easy to use, easy to automate, and extremely efficient in both storage and time.  Highly recommended.  **If you have only 1 copy of important data, you don't really have any copies.**

Sorry dude.  The data in the first 5-10G of the HDD is gone and I wouldn't expect much hope in getting anything from an old NTFS format when an EXT4 format has been applied over it.

Files towards the end of the HDD might come back, if you are lucky.

---

### Post by Frogs Hair on 2013-03-20
There are programs to recover deleted files while Windows is installed , but a formatted drive is a different matter .  You must have been in a hurry when you read step 4. [http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)

---

### Post by Mark Phelps on 2013-03-20
If you can connect the drive to a Windows PC, and are willing to spend a little money to recover those files, then read on ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

