---
title: "Ubuntu 16.04 Windows 7 hibernate: Windows files corrupted"
date: 2016-12-10
forum: General Help
---

### Post by numessanguis on 2016-12-10
I have the following setup:
- SSD with Windows 7 64-bit (NTFS)
- SSD with Ubuntu 16.04 (Ext4)
- HDD for data (NTFS)

My usual work flow is: Do stuff on Windows and programming on Ubuntu.
After I'm done programming, I almost always hibernate Ubuntu and because of boot order priority, after an hibernation, it will always start into Windows 7.
However yesterday when I booted into my Ubuntu, I noticed I forgot to dismount the HDD, so I dismounted it.
Still on Ubuntu, I remounted it and wrote a picture to the HDD, then I think I dismounted it again before hibernating.
Now I started Windows and it seems the files I created during the past few days have been corrupted.
(I should write a script that dismounts any external mounts in Ubuntu when I hibernate it.)
During the time Ubuntu was hibernated, I once hibernated Windows, but I booted again into Windows (I never booted into Linux while Windows is hibernated).

My questions are:
- How my Windows files got corrupted? I always thought Windows was the aggressive controller and you would risk losing files written by Ubuntu (however the picture I put on the HDD when in Ubuntu was not corrupted).
- I'm now on Windows and scared I screw up things more if I boot into Linux again (but it is still hibernated). How do I recover my files (since I started Windows I didn't write anything to my HDD)?
I found this topic: [https://ubuntuforums.org/showthread.php?t=2108966](https://ubuntuforums.org/showthread.php?t=2108966)
but since it was from 2013, I'm not sure what the best current options are.

---

### Post by oldfred on 2016-12-10
You cannot hibernate any system and access hibernated file systems from another system and expect the hibernated system to see the updates from the other system.
It may have worked if you unmount the NTFS system in either system first. But Windows does not make it easy to unmount an internal partition.

In Linux it is testdisk or photorec. But some that still use Windows have suggested the Windows NTFS recovery tools may be better.
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk

[/URL]
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam. 

[URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

---

### Post by numessanguis on 2016-12-10
I ended up using PhotoRec: [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
It recovered 258 files ^-^, the interesting things was that it also recovered files from years ago.
Not sure if that was because of the hibernate and dual-boot or from a previous corruption.
The only disadvantage is that I have to put back every file back manually.

Still don't know how the data got corrupted though.

Edit:
I also ran Recuva, but it only recovered 108 files.
It didn't recover any .mkv files for example.
So in my case PhotoRec worked better (although with some of the recovered .mkv files only the beginning of the video works).

---

### Post by numessanguis on 2016-12-10
Thanks for the software recommendations!

> **oldfred said:**
> You cannot hibernate any system and access hibernated file systems from another system and expect the hibernated system to see the updates from the other system.
It may have worked if you unmount the NTFS system in either system first. But Windows does not make it easy to unmount an internal partition.[URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

The thing is that the files I copied to the HDD under Windows 7 were corrupted when I try to view the files on Windows.
The file I put under Ubuntu to the HDD could be opened in Windows without problem.
Or do you mean the file I put from Ubuntu on the HDD overwrote the files I put on the HDD through Windows (because in Ubuntu the change by Windows was not known)?

It is the first time this happened to me and it seems that it normally goes well as long as I dismount the HDD on Ubuntu before hibernation.

---

### Post by oldfred on 2016-12-11
Probably, as one system does not know what the other system has done.

When I ran photorec I lost a batch of text files that I saved often, but had a backup. Issue became like you found it recovered all the old deleted files also. I had to figure out which files were which and then do a lot of compares to original back up to see which had newer data.

---

### Post by HermanAB on 2016-12-11
In my experience, it is best to use a virtual machine for Windows on Linux/Mac and use Virtualbox to shut down or suspend Windows, while Linux/Mac can shutdown/suspend as normal, irrespective of what the Windows VM is doing.  This way, I have never experienced corruptions.

---

### Post by numessanguis on 2016-12-11
I want to auto unmount all my NTFS devices on hibernate to prevent what happened to me today, help is appreciated:
[https://ubuntuforums.org/showthread.php?t=2346082&p=13581281#post13581281](https://ubuntuforums.org/showthread.php?t=2346082&p=13581281#post13581281)

@HermanAB
Ubuntu works a bit quirky on my laptop hardware (integrated and nvidia card are conflicting among others), so I don't want to rely on Ubuntu as my main system.
On the other hand I'm going to do deep learning (AI, computational intensive) on Ubuntu, so Ubuntu in a VM in Windows is probably also not a solution, as I need my full resources.
Also I like the idea that if 1 OS stops working, I can use the other one.
Although before I had Windows 7 + Ubuntu in a VM and I liked that you could work in both OSes at the same time.

---

### Post by oldfred on 2016-12-11
One of the answers here (one not accepted) uses diskpart and some .bat files/scripts to unmount NTFS. Seems to be more for having mounted a Linux partition inside Windows, do not know Windows to know if it would work for a NTFS data partition or not.

[http://askubuntu.com/questions/849872/how-can-i-prevent-windows-10-from-corrupting-the-ext4-superblock-every-time](http://askubuntu.com/questions/849872/how-can-i-prevent-windows-10-from-corrupting-the-ext4-superblock-every-time)

---

