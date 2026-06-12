---
title: "Windows XP Hibernation corrupting shared FAT32 partition"
date: 2005-05-07
forum: General Help
---

### Post by NeTo on 2005-05-07
I use a dual boot computer at home, since I'm the only one using linux. 

On windows, fast user switching and hibernation are used because it means a very short load time.

I have set up a 40gb Fat32 partition to hold some music and documents, so they can be used in both Windows XP Pro and Ubuntu Hoary. 

The problem is that if I do the following:

1. Hibernate Windows
2. Restart on Ubuntu and write/rename some files to the FAT32 partition
3. Resume Windows from hibernation

The fat32 parition returns to its original state. That means any change I did to it on Ubuntu gets wiped out. I have lost a bunch of documents now, and I don't want to make the same mistake once I reinstall Hoary tomorrow.

I have found only a single page with a similar problem in [Microsoft's KB](http://support.microsoft.com/default.aspx?scid=kb;en-us;Q327086), but the solution listed there won't apply to my case.

**EDIT**: I have now proposed a solution to this. The windows service I coded (plus instructions) are in the attachment in this post. Read [below](http://www.ubuntuforums.org/showthread.php?p=171082) for info on my HiberFix Service.

---

### Post by dave9191 on 2005-05-07
Im using a dual boot machine with a fat32 drive to share info between them (i hibernate and suspend to disk using both OS's). I havent come accross this problem and Ill experiment with this. This might be a very good warning to people. I'll get back to you with what i discover on my comp.

---

### Post by dave9191 on 2005-05-08
This is quite a serious problem. Ive messed around a little with it and Ive managed to loose an important file in the process when windows kindly truncated it for me. Its been restored from backups, but Ill need to do a full backup before I play around anymore. 

After the backup Ill try mounting and unmounting the drive in windows after a hibernate restore. Im hoping that there is a solution and I dont have to give up on hibernate either. 

Dave

---

### Post by Julius on 2005-05-08
I thought hibernation actually turned the Hardisks off, or something (on my comp there was a noise from the hardisk when it was on hibernation mode).

---

### Post by dave9191 on 2005-05-08
[QUOTE=Julius]I thought hibernation actually turned the Hardisks off, or something (on my comp there was a noise from the hardisk when it was on hibernation mode).[/QUOTE]

Hibernation completly shuts down the system, but when you come out of it, it restores the RAM in its previous state. So if it loads the HDD tables into the RAM, they will be restored when you turn the OS back on again.

---

### Post by NeTo on 2005-05-08
[QUOTE=dave9191]This is quite a serious problem. Ive messed around a little with it and Ive managed to loose an important file in the process when windows kindly truncated it for me. Its been restored from backups, but Ill need to do a full backup before I play around anymore. 

After the backup Ill try mounting and unmounting the drive in windows after a hibernate restore. Im hoping that there is a solution and I dont have to give up on hibernate either. 

Dave[/QUOTE]
 It's sad to hear it wasn't a specific problem of my setup. I don't have my hoary setup ready yet (I think that at least until tomorrow) so I can't test anything right now. I want to check if mounting the FAT32 partition in a folder instead of assigning it a drive letter would make a difference, but I think that will have to wait, being today mothers's day and all :p

PS: This could be a serious issue in my opinion. What if the OS/bootloader resides in the Fat32 partition? You could end up with an unbootable system in the worst case , right?

---

### Post by NeTo on 2005-05-09
[QUOTE=dave9191]This is quite a serious problem. Ive messed around a little with it and Ive managed to loose an important file in the process when windows kindly truncated it for me. Its been restored from backups, but Ill need to do a full backup before I play around anymore. 
[/QUOTE]

It's sad to hear it wasn't a specific problem of my setup. 

I have tried mounting the FAT32 partition in a folder in the windows partition (instead of letting windows assign it a drive letter) and disabling System Restore without positive results. I don't know what else to try right now.

PS1: This could be a serious issue in my opinion. What if the OS/bootloader resides in the Fat32 partition? You could end up with an unbootable system in the worst case , right?

PS2: I have been just reading [this article](http://msdn.microsoft.com/library/default.asp?url=/library/en-us/dnxpesp2/html/HORMDismountingVolumesInHibernateOnceResumeManyConfiguration.asp). Check the example at the end. Although the article is oriented to Windows XP Embedded, the dismount example should work on Windows XP SP2.

I will download the Windows SDK now to test it, unluckily is a 300+ mb download so it'll take me a while. So far is the only possible solution I have found to the hibernation issue.

---

### Post by NeTo on 2005-05-10
After a couple of hours searching on the net and testing I think I finally understand the problem.

**The issue:**

1) When Windows goes to hibernation mode it stores, among other things, the file cache memory. The saved cache doesn't get flushed the next time windows is started; it is reloaded instead.

2) If the structure of the drive changes somehow after hibernation, and before the next windows boot up (i.e. creating/deleteing a file in Linux), the windows file system cache will point to wrong file segments, even if the file allocation table on the drive is correct. Any change made to the drive won't be reflected in Windows after it resumes from hibernation.

3) As new segments are added/removed from the cache, *the file allocation table will eventually get corrupted* (you can check that with fsck on Linux or chkdsk on windows). Changed sectors will most likely be marked as unallocated. Hence, the files won't be recovered by popular undelete utilities. Only the freeware [Restoration](http://www.geocities.jp/br_kato) seems to be able to look for file fragments in the unallocated space of the disk.

As I said before, this has a huge system-breaking potential. This an extreme example: Let's say you set hibernation in windows and then install Linux+Grub on a Fat32 partition. Next time you boot windows all changes in the fat32 drive will be wiped out. Not only you will lose your linux install, but since the MBR won't be changed, chances are that your system won't boot next time.


**Possible solutions:**

There seems to be three possible way-arounds to this issue:

1) *Disable hibernation in windows*: the simplest way, meh.

2) *Unmount any Fat32 volumes in Windows before setting the hibernation and remounting them again when windows is started*.
It seems that coud be achieved using the Windows SDK, but I don't think that would be an easy task, especially if other processes are accessing the drive

3) *Flushing the file cache before hibernation*.
That would force windows to reduce the cache size and luckily remove any reference to file segments of the Fat32 drive(s).

I have so far tried 3) and it seems to work well. Unluckily I don't have anything right now that could be used in a daily basis, as I just allocated the memory, set hibernation, and killed the memory-eater process when the system resumed.

Sorry for the very long post. I hope this can be of help to anyone insterested.

---

### Post by dave9191 on 2005-05-10
Well I havent had time to play with this some more, but after reading your post i spent a couple of min browsing online to see what i could find. Good post btw. 

[http://www.sharewareconnection.com/cache-cleaner.htm](http://www.sharewareconnection.com/cache-cleaner.htm)
[http://www.howtodothings.com/viewarticle.aspx?article=97](http://www.howtodothings.com/viewarticle.aspx?article=97)

Those links are there cause they seem relevevant and i dont want to loose them until i have more time to try out the stuff. 

Dave

---

### Post by NeTo on 2005-05-13
After several days coding I have made my first C project. Meet HiberFix...

From the Readme:

[i]HiberFix is a Windows NT-based service that sets additional security measures
when the computer is set to an hibernation state.

In its current form, HiberFix flushes the system file cache before hibernation
occurs, in order to eliminate any references to file segments. This MUST BE DONE
if you have a dual-boot system (for example, Linux-Windows) and you want to use
the hibernation feature. Otherwise you will may end up with data CORRUPTION.

HiberFix runs silently in the background as a system service, so it will be
active even if no user has logged on. [/i]

I have attached the program. Just unzip to a directory of your choice and follow the instructions in the Readme.txt file to install it.

I haven't tested it throughfully, so any feedback would be appreciated.

---

### Post by dave9191 on 2005-05-13
I havent had a chance to play with this hibernation prob for a while. But Ill give your app a go when I find some more time to boot into windows. Ill give you any feedback I can. 
Dave

---

### Post by lupo on 2005-05-21
Yea, it seems that I'm not the only one who has this amazing problem!  :smile: 
I have excatly the same problem:
 - Dual-Boot Win XP Pro / Ubuntu Hoary
 - When Windows is in the hibernation mode and I create a file on the fat32 partition under Linux, I cann't see the file after resume Windows.
- Normally a reboot of Windows helped to see the new created file. But it also happened that I lost the files irrepealably! And that was /still is very annoying!! 

I didn't have a clue why this happended but know I finally know the reason!

So thanks a lot to NeTo! I will imediatley test your HiberFix, the next time I start windows  ;-) 
I will post my feedback here.
Greets
  Lupo

---

### Post by lupo on 2005-07-21
Hi there,
after working a few months with this fantastic tool I can say that it work's like a charm! After a Windows resume I can find all the new files created under linux!  \\:D/ 
Thanks a lot to NeTo! Well done!!

---

### Post by NeTo on 2005-07-28
[QUOTE=lupo]Hi there,
after working a few months with this fantastic tool I can say that it work's like a charm! After a Windows resume I can find all the new files created under linux!  \\:D/ 
Thanks a lot to NeTo! Well done!![/QUOTE]
 It's nice to hear it is working as intended. I haven't had much time to test the service with what I would call critical files.

I have checked the code today and found some minor mistakes. I have uploaded a new version in the first post of this thread. If anyone is using the service, I recommend to upgrade (you need to stop the service first, and then just copy the files over, the service can be started afterwards.).

---

### Post by kolemik on 2008-06-24
Hi! There is now such file includes.h in the attached sources. Can you please post this header file? I can't found all the needed includes by hand :(

---

### Post by thomasa88 on 2008-07-18
Does this also work with Vista?

---

