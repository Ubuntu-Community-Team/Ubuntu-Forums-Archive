---
title: "Problems backing up system with DD"
date: 2014-02-16
forum: General Help
---

### Post by AlliumPorrum on 2014-02-16
I have a PC where Xubuntu 13.10 is installed on USB drive. I would like to make an exact bootable copy of it with DD, but for some reason, a copied USB drive won't boot but it just always opens some "grub rescue" terminal. What's wrong with it?? Everywhere it is said that a drive copied with DD should be an exact copy (like; dd if=/dev/sda of=dev/sdb)

I also have tried to format the new disk to different file systems with Gparted, and it seems that a disk formatted to ext2 or ext4 and DD'd after that do not work at all i.e. all I get is blinking cursor on a blank screen. Only fat32 is getting me to grub rescue, but nothing works correctly. 

And; the USB sticks are exactly the same type.

So, could someone please tell me how to do an exact bootable copy of my current USB stick??

---

### Post by AlliumPorrum on 2014-02-16
Now I also tried to format the disk on Windows and after that DD from sda to sdb, but no help, it won't boot from a copied disk. What should I try next?

---

### Post by oldfred on 2014-02-16
Do you have both still plugged in. Since duplicate and you cannot have duplicate UUIDs, you cannot have both connected at same time.

dd will not use any pre-formatting as it copies everything, bit for bit.

 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by AlliumPorrum on 2014-02-17
> **oldfred said:**
> Do you have both still plugged in. Since duplicate and you cannot have duplicate UUIDs, you cannot have both connected at same time.[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Do you mean that did I have both of them plugged in when I rebooted after the DD? The answer is no, I had just the new copied stick plugged in.

Is there any good tool for Ubuntu, which would make an exact bit-to-bit copy of a _bootable_ USB stick?

---

### Post by sudodus on 2014-02-17
1. Please post the command you used to clone the pendrives (the whole command line)!

2. Please insert both pendrives, run the command

```
sudo fdisk -lu
```

and post the output of the command.

There might be a number of things that made it fail. For example, that you cloned the partitions, when you should have cloned the whole drive, or if the target drive is smaller (maybe only a little bit smaller).

If the target drive is slightly larger or exactly the same size, you can use [Clonezilla]("http://clonezilla.org/") to clone or make an image. Clonezilla does not copy unused blocks, so it is more efficient than dd. But the main advantage with Clonezilla is that it is much safer than 'the disk distroyer'.

If the target drive is smaller than the source drive, but there is space enough for the files, and it is an 'installed system' you can also use the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), make a tarball, and then install the system from the tarball. It will not be an exact copy, but a working system with different UUIDs for the root file partition and the swap partition. The One Button Installer is *not* intended for live systems or persistent live systems.

---

### Post by AlliumPorrum on 2014-02-17
> **sudodus said:**
> 1. 
If the target drive is slightly larger or exactly the same size, you can use [Clonezilla]("http://clonezilla.org/") to clone or make an image. Clonezilla does not copy unused blocks, so it is more efficient than dd. But the main advantage with Clonezilla is that it is much safer than 'the disk distroyer'.


Thanks sudodus, I will try that! I'll come back if I have any problems with that also ;=)

---

### Post by AlliumPorrum on 2014-02-18
No luck with Clonezilla either :=( The two USB sticks are EXACTLY the same model and size, but still Clonezilla claims that the destination is smaller that the source and it won't do the copying. It says that destination disk is 7.7GB and source is 8.0GB. WTF??

How in earth can this be so difficult!?!? Isn't there really any simple way to clone the bootable USB stick? :(

---

### Post by sudodus on 2014-02-18
Have you checked with
```
fdisk -lu
```
that the target drive has at least as many sectors (or blocks) as the source drive? Clonezilla won't work if the target is one single sector smaller.

In that case the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") might solve your problem: Make a tarball, and create a system that does the same thing, but is not exactly the same on the other drive.

> [SIZE=4]**Typical cases for the One Button Installer**[/SIZE]

**Tool that is easy to use and just works**

 The normal linux installers that come with iso files are complicated to  use or freeze during the installation process, and you want a tool that  is easier to use and just works. 
 
**Replace Windows XP**

 Replace Windows XP because you want the computer to work faster or  smoother with an Ubuntu based linux operating system, or at the end of  life in April 2014, when there will be no more security updates for  Windows XP. 
 
[COLOR=#006400]**Backup**

 You want a simple method to backup (and restore) your whole installed  linux system. The One Button Installer combines installation, backup and  restore in one set of tools. 
 [/COLOR]
**Your own portable Ubuntu based linux system**

 You want to make your own linux system portable and port it to a USB  pendrive or to be installed in another computer to be used by yourself,  or to be uploaded to the internet for sharing with other people. The One  Button Installer can do it in a simpler way than to remaster the code  and make an own iso file. 

---

### Post by AlliumPorrum on 2014-02-18
Well it seems that they are not:

~$ sudo fdisk -lu

Disk /dev/sda: 8011 MB, 8011120640 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00027dc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    13672447     6835200   83  Linux
/dev/sda2        13674494    15429631      877569    5  Extended
/dev/sda5        13674496    15429631      877568   82  Linux swap / Solaris

Disk /dev/sdb: 7798 MB, 7798947840 bytes
22 heads, 33 sectors/track, 20981 cylinders, total 15232320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002821e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    15230975     7614464   83  Linux


How come is this possible?? I have 5 of these USB sticks that I bought at once (DataTraveler 100 G3 8GB), and they *all* give very different results with fdisk. :confused:

Is there some trick that should be known when formatting the destination? Actually, I would have thought that when making a bit-to-bit copy, it should not matter at all if it even formatted or not..?

---

### Post by coldcritter64 on 2014-02-18
> **AlliumPorrum said:**
> <snipped for brevity>
How come is this possible?? I have 5 of these USB sticks that I bought at once (DataTraveler 100 G3 8GB), and they *all* give very different results with fdisk. :confused:

Is there some trick that should be known when formatting the destination? Actually, I would have thought that when making a bit-to-bit copy, it should not matter at all if it even formatted or not..?
It appears to be normal from my recent experience with Lexar Jumpdrives (2 "identical" units weren't exactly "identical" unfortunately) being similar to your situation. I was lucky the larger one was left to take the clone of the first usb stick, but I was shocked at the difference, like you.

Cloning to a larger drive is OK as has been noted, you may need to adjust partition sizes/filesystems to fill unused space if you like to. As sudodus notes, "one sector smaller", and problems occur though. Always check the destination first with fdisk for sufficient space.

To clone a usb stick the method I use, 
1. check sizes, with fdisk OR gparted, on BOTH sticks.   
2. shred (zero out) the destination stick (_*not entirely necessary*_, dd does a fine job of flattening a destination drive ;)).   
3. dd the original to the destination stick (formatting the destination is not necessary, dd copies over everything including the drives "unique" identifier etc).   
4. remove the original (and boot, if bootable, the second usb stick) -important to remove the original as oldfred noted, there will be duplicate UUIDs on the system (which can get very messy).

If you can get a handle on the use of clonezilla, it is a safer option generally than such a low level tool like dd. 
dd has cost me a 75 GB partition full of stored data when an image was restored back to the wrong partition (not enough coffee content in my system that day :)), thank goodness for backups that I only lost a few unimportant files after fixing the mess from the backups.

---

### Post by sudodus on 2014-02-19
> **AlliumPorrum said:**
> 
How come is this possible?? I have 5 of these USB sticks that I bought at once (DataTraveler 100 G3 8GB), and they *all* give very different results with fdisk. :confused:

Is there some trick that should be known when formatting the destination? Actually, I would have thought that when making a bit-to-bit copy, it should not matter at all if it even formatted or not..?

The production process of flash memory is not entirely reproducible. There are many bad memory cells, that must be marked bad and excluded from usage. And then the result might be undersized pendrives (less than nominal size, and variations as well).

But as I wrote in posts #5 and #8, you can use the One Button Installer and store the backup as a tarball. It works when the target drive is smaller (as long as there is space enough for the files).

*Edit*: The system can be re-installed or ported to another disk or pendrive, also smaller, because the copying process does not involve the blocks. The One Button Installer creates a file system and expands the directories and files into that file system.

---

### Post by monkeybrain20122 on 2014-02-19
> **AlliumPorrum said:**
> No luck with Clonezilla either :=( The two USB sticks are EXACTLY the same model and size, but still Clonezilla claims that the destination is smaller that the source and it won't do the copying. It says that destination disk is 7.7GB and source is 8.0GB. WTF??

How in earth can this be so difficult!?!? Isn't there really any simple way to clone the bootable USB stick? :(

It is difficult because you use the wrong tools. :) Use fsarchiver, it is in the repo. 

It doesn't have the silly requirement that the target has to be smaller than the original partition like clonezolla, it just has to be big enough for the contents. I use it routinely to duplicate Linux distos in different drives and machines. It is really the safest and easiest way I find to make clones and restore. [http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

There are only two commands and some options you need, see post #8 for some brief explanations
[http://ubuntuforums.org/showthread.php?t=2204491&p=12923983#post12923983](http://ubuntuforums.org/showthread.php?t=2204491&p=12923983#post12923983)

P.S. dd is dangerous if you're not sure what you are doing, strange that you do that for your first attempt. :)

---

### Post by AlliumPorrum on 2014-02-19
Thank you veeery much for your support guys! :D

I'm going for a one week's vacation after tomorrow, so I'll come back to this issue a bit later. 

But, two more questions before that:
- Are One Button Installer and fsarchiver doing exactly the same thing? Any difference between them?
- Can they both be run on a currently active USB stick (sda), or should I start the PC with some live CD, and then copy from sdb to sdc?

---

### Post by monkeybrain20122 on 2014-02-19
I don't know about one button installer, but fsarchiver can run on a currently active disk with options -a and -A for the savefs command (see example from post #8 on my second link above). Though in that case you shouldn't be doing something that changes the system like installing software or upgrading. Going on the internet and reading documents are fine. But since you are on a usb I suspect it will be slow if you do that.

---

### Post by sudodus on 2014-02-20
> **AlliumPorrum said:**
> Thank you veeery much for your support guys! :D

I'm going for a one week's vacation after tomorrow, so I'll come back to this issue a bit later. 

But, two more questions before that:
- Are One Button Installer and fsarchiver doing exactly the same thing? Any difference between them?
Not exactly the same thing, but similar in the sense that the files are taken care of separately from the partition and file system. The One Button Installer stores the files in a compressed tar archive, a tarball. I have read the information at the web site of fsarchiver, and I think it is also a good system, but I have not used it. Maybe it is a matter of taste, which of these systems that would be best for you.
> 
- Can they both be run on a currently active USB stick (sda), or should I start the PC with some live CD, and then copy from sdb to sdc?

The One Button Installer, OBI, itself is made to run from USB, and it can install into USB as well as internal drives and eSATA drives. At the standard OBI level it is booted from one USB pendrive and can install to another pendrive. At the advanced OBI level it should be able to install into another partition on the same pendrive (but you should be careful when messing with the device it is booted from). Anyway, the tarball is stored in the USB boot drive, in the directory /tarballs

So to avoid complication, I suggest that you think like this: Use one pendrive for the One Button Installer, where you write the tarball. Later on you should copy (or move) the tarball to a hard disk drive, for example a USB disk, that you use for backup of personal files (documents, photos and multimedia files).

In order to test that restoring (alias installing) from the tarball works, I suggest that you use another pendrive of similar size, at least big enough for the files and maybe a small swap partition. If you have no swap in your current USB pendrive system, 'noswap' should be part of the tarball's name.

---

### Post by AlliumPorrum on 2014-03-02
Ok, back to "business" after a vacation. I just readed documentations about the OBI, but for a newbie like me, it seems to be far away from "one button" installer... I really thought that I just install it from the Software Center, press a huge "Create image" button, and that's about it :-) But that doesn't seem to be the case...

I readed this document about creating a tar ball: [https://help.ubuntu.com/community/OBI/MakeOBItarball](https://help.ubuntu.com/community/OBI/MakeOBItarball)
And then I read this about installing from it: [http://ubuntuforums.org/showthread.php?t=2172971](http://ubuntuforums.org/showthread.php?t=2172971)

But I just could not understand how to install OBI on my Ubuntu or how to backup my system with it :oops: So could some please try explain it step-by-step...?

Once again I'm wondering how come it really can be so difficult to copy a Linux system from USB stick A to USB stick B?? I know, it might not be difficult it you're very familiar with Linux and all it's trick, but I have fighted with this issue for a month now without any success. Whatever I try, "something" goes wrong :=(

---

### Post by AlliumPorrum on 2014-03-02
And hey; does OBI or fsarchiver actually create identical swap partitions etc. to the destination USB disk? At least fsarchivers pages say that "Here is how to use FSArchiver to backup a _partition_ of your disk", not "partitions"..?

---

### Post by monkeybrain20122 on 2014-03-02
> **AlliumPorrum said:**
> And hey; does OBI or fsarchiver actually create identical swap partitions etc. to the destination USB disk? At least fsarchivers pages say that "Here is how to use FSArchiver to backup a _partition_ of your disk", not "partitions"..?  Usually I don't back up swap so I don't know. But it can create  a single archive for several  partitions (e.g / and /home) and restore from it. (So if you create a new swap partition you would have to edit /etc/ fstab and /etc/initramfs-tools/conf.d/resume since the uuid of swap has changed, just run blkid to find out the new swap's uuid and edit these files to make sure they match)

---

### Post by sudodus on 2014-03-02
> **AlliumPorrum said:**
> 

But I just could not understand how to install OBI on my Ubuntu or how to backup my system with it :oops: So could some please try explain it step-by-step...?

Please view or download [this OBI quick start manual file]("http://ubuntuone.com/42AIgmpo9lsz7YNfXKCROV") with a *short description* how to make a boot drive with the OBI and how to use  the OBI to install an Ubuntu based linux operating system.
> 

Once again I'm wondering how come it really can be so difficult to copy a Linux system from USB stick A to USB stick B?? I know, it might not be difficult it you're very familiar with Linux and all it's trick, but I have fighted with this issue for a month now without any success. Whatever I try, "something" goes wrong :=(

If you want a simple clone of the iso file, you get an Ubuntu install system (a 'live' system with a button for installing the system (normally to an internal drive)). Such a system does not use the whole drive. Next step is to use some kind of tool like the One Button Installer, Unetbootin or fsarchiver, that can re-create the system on a drive of another size. This is not simple copying. But if you follow the instructions for each of the tools carefully, you will succeed (to make a bootable system on a USB drive).

Some computers might not work with such a system. You may need a proprietary driver or a boot option for the linux system to cooperate with the hardware.

---

### Post by sudodus on 2014-03-02
> **AlliumPorrum said:**
> And hey; does OBI or fsarchiver actually create identical swap partitions etc. to the destination USB disk? At least fsarchivers pages say that "Here is how to use FSArchiver to backup a _partition_ of your disk", not "partitions"..?

No, the sizes of the partitions made to fit the size of the target drive. The root partition is created and filled with copies of the directories and files. The content of the swap partition need not be copied. It is temporary (with prolonged lifetime only when you hibernate the state of the computer). Identical partitions are not necessary, not even the best in this case.

---

### Post by AlliumPorrum on 2014-03-03
> **sudodus said:**
> Please view or download [this OBI quick start manual file]("http://ubuntuone.com/42AIgmpo9lsz7YNfXKCROV") with a *short description* how to make a boot drive with the OBI and how to use  the OBI to install an Ubuntu based linux operating system.

I try and I try, but I just don't understand these instructions :(

[I]"Select one of the compressed image files
(where
xx
= version x 10
)
dd_blank-obi_4GB_xx_text.img.xz
dd_blank-obi_8GB_xx_LubuntuSaucy.img.xz"[/I]

WHERE I download these from?? The instruction says that "f[I]rom either phillw.net with a complete set of files or google drive with selected files
[http://phillw.net/isos/one-button-installer/](http://phillw.net/isos/one-button-installer/)
[http://drive.google.com/folderview?id=0BzX-18u3W1sQblBTYXNacGVsVkk&usp=sharing](http://drive.google.com/folderview?id=0BzX-18u3W1sQblBTYXNacGVsVkk&usp=sharing)[/I]"

If I go to that phillw- address, there is a bunch of files and directories, but no those .xz- files at all!?

It also says *"d. Download the files. Let mkusb help you in linux."* But my Ubuntu just says that "mkusb: command not found"?

So I can't even install this freaking OBI, to start studying the copying process. Not quite a "one button" after all :( Isn't it possible to install it easily from Software Center??

---

### Post by sudodus on 2014-03-03
It is obvious that the instructions at those web sites are not good enough. After helping you I have to rewrite them.

-o-

[mkusb]("http://phillw.net/isos/one-button-installer/scripts/mkusb") must be downloaded (and it helps to download also the file with instructions [mkUSB-quick-start-manual.pdf]("http://phillw.net/isos/one-button-installer/scripts/mkUSB-quick-start-manual.pdf")) from this directory

[http://phillw.net/isos/one-button-installer/scripts/](http://phillw.net/isos/one-button-installer/scripts/)

Have you downloaded the OBI yet? I suggest that you get version 2.3 with the compressed image file

[dd_blank-obi_7.8GB_23_LubuntuSaucy.img.xz]("http://phillw.net/isos/one-button-installer/dd_images/dd_blank-obi_7.8GB_23_LubuntuSaucy.img.xz")

from the directory [http://phillw.net/isos/one-button-installer/dd_images/](http://phillw.net/isos/one-button-installer/dd_images/)

and there are fairly detailed instructions how to create a tarball at this link

[https://help.ubuntu.com/community/OBI/MakeOBItarball](https://help.ubuntu.com/community/OBI/MakeOBItarball)

From your previous attempt with dd (from post #1), I think that 'Make tarball' at the main menu should work, but the names of the devices may change when booting from the OBI; check with 'Help text' at the main menu of the OBI or

```
sudo parted -l
``` and ```
sudo blkid
```

So if the source pendrive is **/dev/sdb**, quit to a bash shell and run

```
sudo bash mktbl /dev/sdb1
``` instead (the digit 1 indicates that your root file system is in partition one)

---

### Post by monkeybrain20122 on 2014-03-03
> **AlliumPorrum said:**
> 
So I can't even install this freaking OBI, to start studying the copying process. Not quite a "one button" after all :( Isn't it possible to install it easily from Software Center??

Unless you try to have a learning experience,--which is a valid goal,-- fsrachiver is a lot easier, it is in the repository too. :)

---

### Post by AlliumPorrum on 2014-03-05
> **monkeybrain20122 said:**
> Unless you try to have a learning experience,--which is a valid goal,-- fsrachiver is a lot easier, it is in the repository too. :)

I just want to know the easiest possible way to handle this issue. Or at this stage; ANY way which works for me...

I read the documentation of fsrarchiver, and it says: *If you want to backup partition which are in use, the best thing to do is to make an LVM snapshot of the partition using lvcreate -s, which is part of the LVM userland tools.*

I did not quite get this, so could give me an advice how should I use this tool..? I have 8GB USB stick as /dev/sda where sda1 7GB partition with Xubuntu 13.10 running from it, and sda2 is 1GB swap. So what exactly should I do the have identical setup for an USB stick in /dev/sdb?

---

### Post by monkeybrain20122 on 2014-03-05
Actually a simpler way to do live backup would be to just use the options -a and -A 
so if I am now running Ubuntu on /dev/sda1 and I want to back it up to some where
```
sudo fsarchiver -v -jn -zn -a -A  savefs /path/to/backup/bak.fsa  /dev/sda1 --exclude=dir1 --exclude=dir2

```
/path/to/backup is the path to the folder where you want to save the backup to, may be an external device.
bak.fsa is the name of the backup file, you can name it anything but the extension has to be .fsa
For the options
-v verbose, I get nervous when nothing shows up in the terminal
-jn is the number of threads used, so if you use 4 threads it would be -j4
-zn is the level of compression, see the quickstart guide (since your system is small, you can just leave that out and use the default
-a for backing up mounted volume
-A for live backup
--exclude for excluding directories which you don't want to backup. In the command above the directories "dir1" and 'dir2" are excluded. If you want to keep everything just don't invoke that option

I have used -a and -A to do some live backups and it never failed. Important thing is you can't alter the system while live backup is in progress or the backup file will become inconsistent. So basically that means don't do things like update and install and don't delete things while this is happening.

Edited: Just try it out, do some experiments. If it doesn't work for some reasons it won't bust your system. The only risk is that the backup file would be corrupted  (bak.fsa) and you can simply delete it.

---

### Post by monkeybrain20122 on 2014-03-05
> I have 8GB USB stick as /dev/sda where sda1 7GB partition with Xubuntu  13.10 running from it, and sda2 is 1GB swap. So what exactly should I do  the have identical setup for an USB stick in /dev/sdb?                 

You would need a third external drive to store the .fsa file.

(But if you have enough room in your usb stick to hold the xubuntu system and the backup of itself AND the temp files generated during the copying you may try this

```
mkdir bak
sudo fsarchiver -v -jn -zn -a -A savefs ~/bak/xubu.fsa  /dev/sda1 --exclude=bak
```

Note the two ns have to be user specified. See above.

This is a bit paradoxical as you are doing a live backup and modifying the system at the same time, but maybe it will work because bak is excluded

If it succeeds, then when it is done, plug in the second usb (say /dev/sdb, can always check with "sudo blkid" if not sure)

Unmount /dev/sdb1 which you want to restore the clone to.

and 
```
sudo fsarchiver -v -jn restfs ~/bak/xubu.fsa id=0, dest=/dev/sdb1

```

The swap has to be created manually. You can't clone it as Sudolus explained.)

Edited: if this succeeds you would need to edit /etc/fstab in /dev/sdb1 for the new swap partition, but that is easy, so don't worry about it at this point.

---

### Post by AlliumPorrum on 2014-03-06
> **monkeybrain20122 said:**
> You would need a third external drive to store the .fsa file.

Why in the world I would need 3 USB sticks?? I mean, can't I just use fsarchiver to store the Ubuntu in sda to a empty stick in sdb? What would be the point for third stick??

---

### Post by monkeybrain20122 on 2014-03-06
> **AlliumPorrum said:**
> Why in the world I would need 3 USB sticks?? I mean, can't I just use fsarchiver to store the Ubuntu in sda to a empty stick in sdb? What would be the point for third stick??

So usb1 =  /dev/sda
usb2 =  /dev/sdb

Now you make a clone of /dev/sda (a .fsa file) while in /dev/sda
you want to then restore this clone to /dev/sdb (still running xubuntu in sda)

So /dev/sda --> bak.fsa --> /dev/sdb
Where '-->' means running fsarchiver in xubuntu on /dev/sda
The first one means savefs , the second restfs

Where do you store the clone/image (the .fsa file) if you don't have a third drive? 

If you want to store it in sdb. It has to be big enough to hold the .fsa file **as well as** the restored OS (so about 2 x the actual installed size of your xubuntu in /dev/sda).  You have to partition sdb so that the .fsa file lives in one partition and you restore to another. Suppose the backup (bak.fsa) is stored in /dev/sdb2 and you now want to restore it to /dev/sdb1

Running in xubuntu on /dev/sda
```
sudo fsarchiver -options restfs /dev/sdb2/bak.fsa  id=0,dest=/dev/sdb1
```
 
Then afterwards you use gparted in xubuntu (/dev/sda1) to delete /dev/sdb2 and expand /dev/sdb1

---

### Post by AlliumPorrum on 2014-03-06
Aaa OK, now I got it, thanks for the explanation monkeybrain! :=)

So does this mean that fsarchiver can only write to .fsa- file, and it cannot copy all files as such from sda to sdb? And it also creates boot partition etc. to the destination USB?

---

### Post by monkeybrain20122 on 2014-03-06
> **AlliumPorrum said:**
> 
So does this mean that fsarchiver can only write to .fsa- file, and it cannot copy all files as such from sda to sdb? And it also creates boot partition etc. to the destination USB?

That's right. fsarchiver is basically a backup tool so instead of directly copying (like dd) it creates a backup archive.

The partition layout has to be created by other means like gparted. The .fsa file is basically an archive of the file system in the original partition (with metadata such as uuid) and then to restore you have to specify the partition and the device to restore to. They have to be given to fsarchiver, it doesn't create them for you.

---

### Post by AlliumPorrum on 2014-03-08
Ok, trying to make a backup to sdb, but fsarchiver just gives an error message:

[I]:~$ sudo fsarchiver -v -jn -zn -a -A savefs /dev/sdb1/xubuntu_backup.fsa /dev/sda1

fsarchiver.c#202,process_cmdline(): [n] is not a valid number of jobs. Must be between 1 and 32
====> fsarchiver version 0.6.17 (2013-02-25) - [http://www.fsarchiver.org](http://www.fsarchiver.org) <====[/I]

What's wrong with my command now..? Tried to google it, but no hits.

---

### Post by sudodus on 2014-03-08
I think the easiest alternative is to buy a new pendrive with more memory than the source (several GB more), and use dd as you did originally. That is likely to work, as long as you check and re-check that there are no typing errors. Do not let dd act as 'disk destroyer' ;-)

Boot from one drive. Copy from a second drive (the source) to a third drive (the target).

---

### Post by Iowan on 2014-03-08
Another source of information on fsarchiver might be [http://www.fsarchiver.org/forums/](http://www.fsarchiver.org/forums/)
(Not that you can't seek help here... :) )

---

### Post by AlliumPorrum on 2014-03-08
Ok, discussion is now continued here: [http://www.fsarchiver.org/forums/viewtopic.php?f=16&t=1687&p=4362#p4362](http://www.fsarchiver.org/forums/viewtopic.php?f=16&t=1687&p=4362#p4362). Previous problem solved, and then to next one.

Damn I just can't use these OS's without a mouse, it seems that EVERYTHING is made really difficult for a newbie...

---

### Post by oldfred on 2014-03-08
If new partition, you need to take owership & give yourself permissions.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
**sudo chmod -R a+rwX,o-w /mnt/data**
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
**sudo chown -R $USER:$USER /mnt/data**

      
 [URL="https://help.ubuntu.com/community/FilePermissions"]https://help.ubuntu.com/community/FilePermissions
[/URL]
 [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

[URL="https://help.ubuntu.com/community/FilePermissions"]
[/URL]

---

### Post by AlliumPorrum on 2014-03-08
Thanks oldfred, but it did not help:

[I]~$  sudo mkdir /mnt/data
~$  sudo mount /dev/sdb1 /mnt/data
~$  sudo chmod -R a+rwX,o-w /mnt/data
~$  sudo chown -R $USER:$USER /mnt/data
~$ sudo fsarchiver -v -j4 -a -A savefs /dev/sdb1/xubuntu_backup.fsa /dev/sda1
[errno=20, Not a directory]: archwriter.c#116,archwriter_create(): cannot create archive /dev/sdb1/xubuntu_backup.fsa[/I]

---

### Post by oldfred on 2014-03-08
I do not know fsarchiver, but your */dev/sda1 *is a device not a mount point.
Try using the mount you just created or /mnt/data.[I]

[I]sudo fsarchiver -v -j4 -a -A savefs /dev/sdb1/xubuntu_backup.fsa [COLOR=#ff0000]/dev/sda1[/COLOR]

*sudo fsarchiver -v -j4 -a -A savefs /dev/sdb1/xubuntu_backup.fsa /mnt/data*[/I]
[/I]

---

### Post by AlliumPorrum on 2014-03-08
But the mounting point I made according the instructions was for the destination, not for the source:

 ~$ sudo mount **/dev/sdb1** /mnt/data

Sorry but I really have no idea about these "mounting points" or "devices", I just did what was suggested above. How can I find out what should I put for the destination and for the source?

---

### Post by oldfred on 2014-03-08
It looks like the first command must be a mount but the second can be a device.
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)
fsarchiver savefs /mnt/backup/gentoo-rootfs.fsa /dev/sda1

---

### Post by monkeybrain20122 on 2014-03-09
> **AlliumPorrum said:**
> Ok, trying to make a backup to sdb, but fsarchiver just gives an error message:

[I]:~$ sudo fsarchiver -v -jn -zn -a -A savefs /dev/sdb1/xubuntu_backup.fsa /dev/sda1

fsarchiver.c#202,process_cmdline(): [n] is not a valid number of jobs. Must be between 1 and 32
====> fsarchiver version 0.6.17 (2013-02-25) - [http://www.fsarchiver.org](http://www.fsarchiver.org) <====[/I]

What's wrong with my command now..? Tried to google it, but no hits.

Note you have to specify n, jn would be like j4 for 4 threads, zn would be something like z3 but you can ignore it since your file is small the lowest level of compression is ok. It is like x is algebra. :)

---

### Post by monkeybrain20122 on 2014-03-09
> **AlliumPorrum said:**
> But the mounting point I made according the instructions was for the destination, not for the source:

 ~$ sudo mount **/dev/sdb1** /mnt/data

Sorry but I really have no idea about these "mounting points" or "devices", I just did what was suggested above. How can I find out what should I put for the destination and for the source?


No worry about mount point. It is very simple, everything is just a file system. It doesn't even have to be bootable so the whole business of grub and mount point is irrelevant for this operation (it would be if you want to change the uuid of your root partition later, but most people won't have a reason to do it except for yours truly :))

You have a partition in some dev. You want to create an archive of its file system and place it somewhere. The source has to be unmounted (unless you do live backup and use the options -a -A) the place to store the .fsa has to be somewhere you can reach, so if an external device then it should be mounted, it is mounted automatically if you just plugin it in.

So if

source = /dev/sdb1
folder for .fsa is /dev/sdc1/backups/
 
and you are running Ubuntu in /dev/sda1 say
So plug in /dev/sdb, unmount sdb1 (say with gparted)
plug in /dev/sdc DO NOT DISMOUNT sdc1 and if it is somehow not mounted, mount it

the command is (using 4 threads)
```
sudo fsarchiver -v -j4  savefs  /dev/sdc1/backups/bak.fsa /dev/sdb1
```
Then just wait.

Edited: For your immediate purpose the most straight forward way would indeed be using dd from one pen drive to a bigger one. But fsarchiver is a real beauty, it is so versatile and actually very easy to use (after you have done it once). There are other tools like rsync, clonezilla etc but none is so easy IMO (and clonezilla is definitely very limited in comparison though many power users here recommend it)

---

### Post by AlliumPorrum on 2014-03-09
Ok, this did it, thank you very much for all the help: *sudo fsarchiver -v -j4 -a -A savefs /mnt/data/xubuntu_backup.fsa /dev/sda1*

But, then I formatted third stick with GParted to have sdc1 with 7GB of ext4 and sdc2 to 500GB's of swap, and tried to restore the system to it, but once again, it failed:

[I]~$ sudo fsarchiver -v -j2 restfs /media/xxxx/Tikku/xubuntu_backup.fsa id=0, dest=/dev/sdc1
oper_restore.c#145,convert_argv_to_strdicos(): cannot find "dest=" key in "id=0,"[/I]

I also had to reboot my system, and for some reason, there is nothing on the /mnt/data/ now?? I found out that my .fsa- file can now be found from /media/<username>/, and I have now idea why?? GParted can see all USB's just fine.

---

### Post by oldfred on 2014-03-09
Default mount of flash drive is /media/$USER/xxxx now before it was just /media/xxxx. 
I label my flash drive partitions with gparted when I create them or with Disk Utility or Disks, so the XXX or mount is by the label.

---

### Post by AlliumPorrum on 2014-03-09
Yes but for some reason this sdc- stick is not shown under the /media/ at all. Does this have anything to do with the restoring problem..? Should I again use some "magical" command to tell Xubuntu about the sdc, even though GParted formatted & shows it just fine??

---

### Post by monkeybrain20122 on 2014-03-09
> **AlliumPorrum said:**
> Yes but for some reason this sdc- stick is not shown under the /media/ at all. Does this have anything to do with the restoring problem..? Should I again use some "magical" command to tell Xubuntu about the sdc, even though GParted formatted & shows it just fine??

sdc should be unmounted. You can check that it is attached with
```
sudo blkid
```

I just restored fedora's home to another computer, the command was
 ```
sudo fsarchiver -v -j4 restfs ~/Downloads/backups/fedhm.fsa id=0,dest=/dev/sda6

```
Here I am booting from Ubuntu in an external drive /dev/sdb and I have the .fsa file in my ~/Downloads/backups folder (in your case it would be /media/usr/xxxx)
/dev/sda6 is unmounted.

BTW, 500G of swap??!

---

### Post by AlliumPorrum on 2014-03-09
> **monkeybrain20122 said:**
> sdc should be unmounted. You can check that it is attached with
[BTW, 500G of swap??!

Well, 500MB, naturally ;=)

But do you really mean that sdc should be UNmounted?? I thought that Ubuntu can use only sticks that are mounted?? Anyway, this is what blkid shows:

[I]:~$ sudo blkid
/dev/sda1: UUID="27f1634a-2b3b-46e0-be97-be0062272e6a" TYPE="ext4" 
/dev/sda5: UUID="578226a6-8f70-4881-a77b-929a3f1634a2" TYPE="swap" 
/dev/sdb1: LABEL="Tikku" UUID="8e04034d-7188-49f6-8a62-d8e64748780d" TYPE="ext4" 
/dev/sdc1: LABEL="Xubuntu" UUID="8406bb49-a99b-45d7-8409-79ca908f7ae1" TYPE="ext4" 
/dev/sdc2: UUID="d73e36ee-2219-48b9-a146-ec3cbe4ca505" TYPE="swap" [/I]

What exactly should I do to unmount sdc1? I did not found an option for unmount from "mount" command, and there seems not to be "unmount" command?

---

### Post by monkeybrain20122 on 2014-03-09
It should be attached but **unmounted**.
"sudo blkid" would show you whether it is attached.

Edited: incidentally, your restored OS would not see the swap. After installation you need to edit /etc/fstab to change the uuid in the swap entry (it has the one in your original install)

---

### Post by AlliumPorrum on 2014-03-09
I don't know if it is mounted or not, but I can't either mount or unmount it:

[I]$ umount /dev/sdc1
umount: /dev/sdc1 is not mounted (according to mtab)
$ mount /dev/sdc1
mount: can't find /dev/sdc1 in /etc/fstab or /etc/mtab[/I]

And as you can see from blkid above, it should be attached OK. Why why why oh why!?! This Ubuntu is really driving me crazy, since everything has to be this difficult... :=(

---

### Post by monkeybrain20122 on 2014-03-09
Yeah in xubuntu all volumes show up at the desktop whether mounted or not. I suppose you can just open the file manager and see if it is mounted? gparted will also show you if it is mounted or not.

---

### Post by AlliumPorrum on 2014-03-09
Both sdb and sdc are shown on the file manager and GParted. Now I tried to click that Unmount button from file manager, but few seconds after that it always comes back. So it seems that Xubuntu is always automatically mounting it? How the heck I then can unmount it??

---

### Post by monkeybrain20122 on 2014-03-09
So you are saying even if you unmount it in gparted it got remounted again? It is weird. I had an xfce partition running Manajaro but I had just deleted it for reintstall, so can't really check at the moment.

---

### Post by AlliumPorrum on 2014-03-09
Previously I tried umount command, but now I did unmount with GParted. If I now check "mount", sdc is not listed. But still;

[I]$ sudo fsarchiver -v -j2 restfs /media/xxx/Tikku/xubuntu_backup.fsa id=0, dest=/dev/sdc1
oper_restore.c#145,convert_argv_to_strdicos(): cannot find "dest=" key in "id=0,"
[/I]

---

### Post by AlliumPorrum on 2014-03-09
Hey hey hey! I just noticed that there is a typo in my command!! it should be *id=0,dest=/dev/sdc1*, not *id=0, dest=/dev/sdc1*. There was one space too much :^o Now the restore is running. Let's see if it will also boot from it...

---

### Post by AlliumPorrum on 2014-03-09
Ok, now the restore process seemed to go thru just fine, I'm getting there step-by-step :D

But (not so surprisingly after all...), when I tried to boot with the new stick, all I got was blank screen with blinking cursor. So, it seems that fsarchiver does not make the disk bootable automatically, and there are still few tricks to be done  ](*,)](*,)](*,)](*,)

Weird thing is that when I now boot from the original USB as sda, and insert the restored USB as sdb, Xubuntu will not mount it at all. It is not shown on the desktop, "mount" command shows only sda, and there is nothing seen in /media/xxx nor /mount/data. But if I check with GParted, it shows it just fine. So maybe I formatted & partitioned my stick in a wrong way. * Sigh *

You guys have leaded me thru this extremely frustrating process, and I can't tell how much I appreciate your knowledge and helpfullness during the weeks. I would NEVER had this done by myself. My sincerest Thank You's for all of you!!  ):P

But, I still need your help with the one last step to finalize my setup; could someone please explain this restoring process, starting from the formatting & partitioning the USB stick in a correct way. [-o<


EDIT: I do not know if this helps, but this is what fdisk shows. As you can see sdb is there, but it is not identically partitioned compared to sda. So most likely I once again messed something up:

[I]
~$ sudo fdisk -lu

Disk /dev/sda: 8011 MB, 8011120640 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00027dc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    13672447     6835200   83  Linux
/dev/sda2        13674494    15429631      877569    5  Extended
/dev/sda5        13674496    15429631      877568   82  Linux swap / Solaris

Disk /dev/sdb: 7798 MB, 7798947840 bytes
240 heads, 62 sectors/track, 1023 cylinders, total 15232320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002821e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    14338047     7168000   83  Linux
/dev/sdb2        14338048    15230975      446464   82  Linux swap / Solaris
[/I]

---

### Post by monkeybrain20122 on 2014-03-09
> **AlliumPorrum said:**
> Ok, now the restore process seemed to go thru just fine, I'm getting there step-by-step :D

But (not so surprisingly after all...), when I tried to boot with the new stick, all I got was blank screen with blinking cursor. So, it seems that fsarchiver does not make the disk bootable automatically, and there are still few tricks to be done  ](*,)](*,)](*,)](*,)


Well it should. But maybe some how grub gets messed up. Did you see something like "grub rescue" on the screen?

Try reinstall grub as follows:
boot into your original xubuntu,
plug in the usb with the restored copy on it.
make sure you get the correct device name, run 
```
sudo blkid
```
So let's say it is now /dev/sdb1
do
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```
Notice that it is /dev/sdb1 in the first and just /dev/sdb in the second.
Then try boot again.

---

### Post by AlliumPorrum on 2014-03-09
Ok, thanks, I'll try that. But before I do it, do you think that my destination (sdb below) is partitioned in a wrong way since it is a bit different that original (sda):

[I]Device Boot Start End Blocks Id System
/dev/sda1 * 2048 13672447 6835200 83 Linux
/dev/sda2 13674494 15429631 877569 5 Extended
/dev/sda5 13674496 15429631 877568 82 Linux swap / Solaris

Device Boot Start End Blocks Id System
/dev/sdb1 2048 14338047 7168000 83 Linux
/dev/sdb2 14338048 15230975 446464 82 Linux swap / Solaris[/I]

---

### Post by monkeybrain20122 on 2014-03-09
No it doesn't matter how you partition your drives. It just copies files from one partition and restores to another, doesn't care about the rest. (of course the file formats have to match: ext4 to ext4)

Edited: Do you remember getting error messages during savefs?
Since your installation is very small it wouldn't take long to redo everything. If I were you I would if just as an exercise to get used to the software.

---

### Post by AlliumPorrum on 2014-03-09
That did it; now the new destination USB boots & works like a charm!! Yeah baby! :popcorn::guitar::lolflag: 

Again; thank you VERY MUCH for your kind support, monkeybrain. It's great to have guys (?) like you supporting us newbies.

Now that I started thinking this whole process; what exactly does that fsarchiver do??? I mean; it does not format or partition the destination disk, it does not seem to create boot sectors, it does not change the pointers to swap etc. etc. Would it make any difference if I just format & partition the destination USB myself, install grub as you instructed, and then just COPY all the files from sda to sdb??

---

### Post by monkeybrain20122 on 2014-03-09
> **AlliumPorrum said:**
> 

Now that I started thinking this whole process; what exactly does that fsarchiver do??? I mean; it does not format or partition the destination disk, it does not seem to create boot sectors, it does not change the pointers to swap etc. etc. Would it make any difference if I just format & partition the destination USB myself, install grub as you instructed, and then just COPY all the files from sda to sdb??

It doesn't do anything of the sort. Just copy the file system and make an archive so that you can restore it anywhere. That's why it is so flexible, whereas if it does other things it will be more restricted in terms of drive layouts and so on (clonezilla for example requires that the image has to be restored to a partition of the same size or bigger, it won't work for me because I create multiple clones for various purposes on different devices) 

Then you may ask why not dd? For one thing dd is a lot slower I think and prone to destroying your system if not careful. Another thing is the same .fsa file can be used as many times as you want, whereas dd works only once.

**Edited**: Normally you shouldn't need to reinstall grub, so something was messed up somehow, I don't know what.

---

### Post by monkeybrain20122 on 2014-03-09
Oh, now to make sure that your restored system can see the swap partition, do the following.
Boot into it, run
```
sudo blkid
```
note the uuid of the swap partition.
then
```
gksudo gedit /etc/fstab
```
and locate the line with swap was installed on ..it has the uuid of the swap partition of the original system.
change the uuid to what you see from the output of blkid
save it.
Reboot. Now open system monitor or whatever it is in xfce and you should see swap is activated (though obviously may not be in use)

Now if everything works, please go to thread tools and from the menu choose 'mark the thread as solved"

---

### Post by AlliumPorrum on 2014-03-22
Aaand another problem with this issue... ;=)

Now I was able to mess up my Xubuntu install, and need to restore the stored system from .fsa- file. Since my Xubuntu install won't even start anymore, I booted up from Xubuntu 13.10 Live CD, and before restoring the backup, tried to install grub to the newly formatted USB stick in sdc. But, all I get is an error message:

[I]xubuntu@xubuntu:~$ sudo grub-install /dev/sdc
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.[/I]

What's wrong with this??

---

### Post by oldfred on 2014-03-23
You can only issue the grub install command from your working install or after mounting (mini-chroot) the install (and boot partition if seperate).

       #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub


 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

