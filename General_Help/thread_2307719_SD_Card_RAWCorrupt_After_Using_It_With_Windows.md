---
title: "SD Card RAW/Corrupt After Using It With Windows"
date: 2015-12-27
forum: General Help
---

### Post by ThePowerpuffGirls on 2015-12-27
I took my SD Card out of my phone and plug it into a computer with a fresh install of Windows 7. I copied my songs over my it froze (the copy window, not the OS). I took it out and plugged it back into my phone and now it says it's corrupt. I plug it into Windows and it wants to reformat it. I tried plugging it into Ubuntu and doing the ntfsfix but it says it's corrupted. I have all kinds of pictures and stuff that are important.

What can I do to fix this?

Same problem as here:
[http://ubuntuforums.org/showthread.php?t=1604486](http://ubuntuforums.org/showthread.php?t=1604486)

---

### Post by sudodus on 2015-12-28
Try in Windows to repair the file system (which is probably a Windows file system, FAT32, exFAT or NTFS). Try according to the following link

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

Please come back and tell us the result :-) If you still have problems, we can suggest other methods for repair or recovery of the files, that are more powerful but also more risky. It might be a good idea to make a cloned copy to a card or pendrive of at least the same size, and try to repair the file system and/or recover files from the cloned copy.

---

### Post by ThePowerpuffGirls on 2015-12-28
I tried "sudo dosfsck -a /dev/sdb" and got the following:
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
Logical sector size is zero.

---

### Post by sudodus on 2015-12-28
1. Is it possible for you to borrow a computer with Windows, and try to repair the file system in Windows? I think the tool in Windows is more complete (able to fix more problems) than the free tool dosfsck.

2. The next attempt might be testdisk, but as I wrote in the link, you should make a cloned copy before using that tool.

3. After that you can try to recover files via photorec. It works without a file system, but it is a lot of work, and you lose the file names (and the directory structure).

---

### Post by ThePowerpuffGirls on 2015-12-30
I just tried in Windows, and got the following error:

"The type of file system is RAW.
CHKDSK is not a available for RAW drives."

Edit: I've tried to check the disk for errors in Windows but it suggested to format it. I have not as I don't want to lose my data.

It's a 32GB MicroSD card.

---

### Post by sudodus on 2015-12-31
Then I suggest that you clone the card and after that use testdisk. See these links for cloning with ***ddrescue***

[help with ddrescue](http://ubuntuforums.org/showthread.php?t=2305804&p=13404147#post13404147)

[more help with ddrescue](http://ubuntuforums.org/showthread.php?t=2305804&p=13405801#post13405801)

Get info about ***testdisk*** including how to download it from

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

If that does not work, you still have ***photorec*** (from the same web site [http://www.cgsecurity.org/](http://www.cgsecurity.org/))

---

### Post by ThePowerpuffGirls on 2016-01-08
I've downloaded ddrescue and testdisk from the Terminal. I will work on it tomorrow. I'm sorry I have not gotten back to you sooner.
One question is how to you clone a copy of the drive is it's in RAW format?

- Blossom

---

### Post by sudodus on 2016-01-08
ddrescue will clone the drive. Each byte will be copied as it is from the source drive to the target drive. This is what cloning means, copying at a low level (below the level of file systems). And it is independent of what file system is on the drive, or if there is no file system.

---

### Post by ThePowerpuffGirls on 2016-01-08
Hi,

I'm not sure how to clone using DDrescue. I've looked at the info. There a bit I don't understand.
I bought another 32GB SD Card and have that in the computer as well. both are FAT, I think.
The original was FAT before somehow being in RAW state.

- Blossom

---

### Post by robo731 on 2016-01-08
I had a similar problem just yesterday, but with a USB drive. The solution I found was to run DISKPART in windows and run the CLEAN command to wipe the disk. After removing it and plugging it back in, it worked fine and I was able to format it. Obviously, you wouldn't want to do that because you'll lose your data, but if you can successfully clone your card, this may be able to fix it.

---

### Post by ThePowerpuffGirls on 2016-01-08
> **robo731 said:**
> I had a similar problem just yesterday, but with a USB drive. The solution I found was to run DISKPART in windows and run the CLEAN command to wipe the disk. After removing it and plugging it back in, it worked fine and I was able to format it. Obviously, you wouldn't want to do that because you'll lose your data, but if you can successfully clone your card, this may be able to fix it.



I think I tried this in Windows and it wouldn't let me without formatting the drive. I will try again in a bit.

- Blossom

---

### Post by robo731 on 2016-01-08
Make sure you run it as an administrator and select the correct disk.

---

### Post by sudodus on 2016-01-08
> **ThePowerpuffGirls said:**
> Hi,

I'm not sure how to clone using DDrescue. I've looked at the info. There a bit I don't understand.
I bought another 32GB SD Card and have that in the computer as well. both are FAT, I think.
The original was FAT before somehow being in RAW state.

- Blossom

You should clone the whole drive (not a partition) with ddrescue. When you clone the drive, everything on the target drive will be overwritten by the content from the source drive. So the cloned copy will also have a RAW 'file system'.

The reason for the cloning is that you will still have the original data, if you happen to destroy things during your work to recover the data files.

So I would suggest that you put the original (source) drive aside, and work on the cloned copy (target) drive.

After cloning you can use potentially dangerous methods without fear :-)


A. Some methods can be used in Windows file systems. I don't know much about those methods, but I'm sure robo731 and also other people can help you to find and use them.


B. Some method can be used in Ubuntu, for example

0. Get an iso file with ***testdisk*** and ***photorec***. See this link [https://www.cgsecurity.org/](https://www.cgsecurity.org/). Make a CD/DVD/USB boot drive and boot the computer from that drive.

1. Try to repair the FAT file system with ***testdisk***.

2. If no luck, maybe you can try some other linux method to repair the file system, for example with gpart (or via gparted).

3. If still no luck, use ***photorec*** to recover the files directly from the file data without any file system. You will probably not get your file names and you will not get the directory structure. It is a lot of work to identify the files and to check which files are good and which files are corrupted. For example fragmented files might not be recovered completely or correctly.

Many people (including me) have been able to recover many valuable files this way. ***photorec*** was originally made to recover picture files, hence the name, but now it can identify the data of many other file types, which is described at [https://www.cgsecurity.org/](https://www.cgsecurity.org/).

---

### Post by ThePowerpuffGirls on 2016-01-08
> **robo731 said:**
> I had a similar problem just yesterday, but with  a USB drive. The solution I found was to run DISKPART in windows and  run the CLEAN command to wipe the disk. After removing it and plugging  it back in, it worked fine and I was able to format it. Obviously, you  wouldn't want to do that because you'll lose your data, but if you can  successfully clone your card, this may be able to fix it.

I have diskpart rnunning, but not sure which one to select. It doesn
It  doesn't show any available to select from. I'm in the dark at guessing  which disk number it is. Like for example, I can type "Select disk 1" 2,  or 3, etc.


> **sudodus said:**
> You should clone the whole drive (not a partition) with ddrescue. When you clone the drive, everything on the target drive will be overwritten by the content from the source drive. So the cloned copy will also have a RAW 'file system'.

The reason for the cloning is that you will still have the original data, if you happen to destroy things during your work to recover the data files.

So I would suggest that you put the original (source) drive aside, and work on the cloned copy (target) drive.

After cloning you can use potentially dangerous methods without fear :-)


A. Some methods can be used in Windows file systems. I don't know much about those methods, but I'm sure robo731 and also other people can help you to find and use them.


B. Some method can be used in Ubuntu, for example

0. Get an iso file with ***testdisk*** and ***photorec***. See this link [https://www.cgsecurity.org/](https://www.cgsecurity.org/). Make a CD/DVD/USB boot drive and boot the computer from that drive.

1. Try to repair the FAT file system with ***testdisk***.

2. If no luck, maybe you can try some other linux method to repair the file system, for example with gpart (or via gparted).

3. If still no luck, use ***photorec*** to recover the files directly from the file data without any file system. You will probably not get your file names and you will not get the directory structure. It is a lot of work to identify the files and to check which files are good and which files are corrupted. For example fragmented files might not be recovered completely or correctly.

Many people (including me) have been able to recover many valuable files this way. ***photorec*** was originally made to recover picture files, hence the name, but now it can identify the data of many other file types, which is described at [https://www.cgsecurity.org/](https://www.cgsecurity.org/).

I just need to know what to type in to clone.

so far I figured out the command line is "sudo ddrescue /dev/sdg /dev/sdb"
SDG is the broken SD Card and SDB is the new one. Both are same brnad and size.

Thanks
- Blossom

---

### Post by robo731 on 2016-01-08
Once you have entered [DISKPART]("https://technet.microsoft.com/en-us/library/cc766465%28v=ws.10%29.aspx"), you can run the command: ```
list  disk
``` to get a list of all the disks on your system. From there  you should be able to determine which which disk you need to choose.  Sudodus makes a good point however, these methods will cause the data to  be erased. Ensure that any data you don't want to lose from the SD card  is backed up or cloned before you do this.

---

### Post by sudodus on 2016-01-08
> **ThePowerpuffGirls said:**
> 
I just need to know what to type in to clone.

so far I figured out the command line is "sudo ddrescue /dev/sdg /dev/sdb"
SDG is the broken SD Card and SDB is the new one. Both are same brnad and size.

Thanks
- Blossom

Please read the info page carefully ```
info ddrescue
```

You will find ***chapter 6 A small tutorial with examples***, and if there are no bad sectors the command line that you suggest should work. Otherwise you should also have a **logfile** and start with the two first command lines (with ddrescue, but add sudo and be very careful to select the correct source and target drives). See ***Example 1***.

---

### Post by ThePowerpuffGirls on 2016-01-09
I got my files back. I've used PhotoRec in Windows. Unfortunately, it didn't recover the names to them or the folders. Thank you for your help; it was much appreciated. :)

- Blossom.

---

### Post by sudodus on 2016-01-10
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

