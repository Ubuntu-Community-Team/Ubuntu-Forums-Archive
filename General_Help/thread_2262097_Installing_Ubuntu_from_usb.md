---
title: "Installing Ubuntu from usb"
date: 2015-01-22
forum: General Help
---

### Post by chopra on 2015-01-22
Hi guys, 
I'm attempting to install Ubuntu 14.01 LTS on a new computer, a toshiba satellite, which doesn't have a disk drive.  So I've got a flash drive, installed Ubuntu on that using the instructions on pendrivelinux.com, and was in the process of setting up Ubuntu 14.01.  In the setup process, however, Ubuntu said that there was no existing operating system on the machine.  The options it gave me were  to wipe out the entire disk and install ubuntu, or a "something else" option.  From what I understand, there's supposed to be a third option, to install ubuntu side-by-side with the other OS, but that didn't appear, as windows 8.1 wasn't detected.

As much as I dislike windows, I'd like to keep it (it's currently only occupying 28 gigabytes of a 750 gigabyte hard drive) as there are occaisionally times when I might use it.  The something else option led me to a screen that I have no understanding of, showing drives sda, sda1, sda2, etc.  I know those are block or character device files, but I don't know what relation they have to the disk partition.

So my problem appears to be that the installer won't recognize windows.

Thanks, Chopra

---

### Post by Dreamer Fithp Apprentice on 2015-01-23
> **chopra said:**
> windows 8.1 wasn't detected.You are wise to be cautious in that circumstance. It SHOULD have been detected. What I would do is:
1-Back up the present installation to external media with Clonezilla. Or you could use fsarchiver from a live disk, but that would be a little more involved.
2-Back up any personal data to external media.
3-Decide how you want to partition the drive. Lots of threads here on that if you haven't already decided.
4-Partition the drive with a Windows partitioning tool. Make the partition sizes such that you can't possibly confuse the Windows partitions (there should be 2, 1 tiny and 1 big, unless things have changed since W-7) with the ones you want to install to and use for other things (such as a seperate data partition, which I strongly recommend, but that's another subject).  In other words, if you shrink your windows partition to, for example, 35 giB, make the sizes of the other partitions sufficiently different from that size so that you can't possibly get them confused when you are installing the 'nix. The partitioning tool you'll use in the Ubuntu installation, not to partition, which you will have already done, but to tell the installer where to put what, will show the size of the partitions, so you don't have to worry about which is which this way.

Then reboot with the installation thumb drive and choose "something else". When you come to the partitioning part of the installation just leave the Windows partition alone (unless you want it mounted automatically when you boot into linux, which can be done, but normally you probably wouldn't want to*) pick a filesystem type (I'd use ext4 for anything but swap) and mountpoint for each partiton. If you want to keep it simple, just put the whole system on 1 partiton, mounted as "/", perhaps 20 giB, perhaps a swap partition twice the size of your RAM if you intend to hibernate or suspend (I'm not up on that subject - I use a desktop and for most modern desktops I think swap is pointless) and make the rest a data partiton, mounted as /media/data with an ext4 filesystem if you expect to primarlily be using Ubuntu, an NTFS one if you expect to primarily be using Windows (which will, of course, cause you to forfeit all your coolness points), or if 50/50 or no idea, either one will do in any case.

Good luck.

----------------------------------------------------------------------
* If you do want to, despite the fact it is probably a bad idea, tell the installer what sort of file system Windows is on, probably NTFS, do NOT check format, repeat, do NOT check format, be very sure format is NOT CHECKED. Remember, since the installer can't see windows it is entirely up to you to not wipe it out. Then tell it how you want to mount it. I'd suggest /media/windows, but that's purely personal preference. I can't think of any good reason to want to do this and the only not-so-good reasons I can think of would be if you planned to frequently poke around in Windows from Ubuntu, maybe to fix broken stuff, or because you don't use a data partition and need to get to personal data on the Windows partition. This is only if you need the Windows partiton mounted AUTOMATICALLY every time you boot. If you will just need access to the Windows partition from Ubuntu occasionally, don't do it this way. It is easy to mount it after you've booted.

---

### Post by buzzingrobot on 2015-01-23
> **chopra said:**
> Hi guys, 
I'm attempting to install Ubuntu 14.01 LTS on a new computer, a toshiba satellite, which doesn't have a disk drive.

What are trying to  say with that?  You later say the machine has a 750gb drive with Windows on it.

---

### Post by sudodus on 2015-01-23
I suggest that you start along the advice of *Dreamer Fithp Apprentice*, first backup, then shrink the Windows partition from Windows.

But then, I suggest that you reboot into a live linux drive (the Ubuntu install USB pendrive) and 'Try Ubuntu'. Start ***gparted*** and do the partitioning of the Ubuntu partitions in the unallocated space.

The philosophy is 'use Windows tools for Windows systems (the NTFS file system) and use linux tools for linux systems'. For example, if you create partitions with Windows, it might create 'dynamic' partitions, which do not work with linux.

After partitioning with gparted you can head back to the advice of *Dreamer Fithp Apprentice* and start the installer ...

---

### Post by raptir on 2015-01-23
> **buzzingrobot said:**
> What are trying to  say with that?  You later say the machine has a 750gb drive with Windows on it.

He means it doesn't have an (optical) disc drive.

---

### Post by startas on 2015-01-23
Dont you ever use that buggy and machine breaking side by side devil ... just run windows, make a partition for linux, launch ubuntu instalation, use advanced option at the bottom when ubuntu will ask where to install it, use that partition to install ubuntu, you will have dual boot without messing up your windows, done.

---

### Post by Impavidus on 2015-01-23
Have you disabled fast boot? And reboot Windows a couple of times after shrinking its partition, so that it can run its file system checks. Then Ubuntu should detect Windows.

---

### Post by chopra on 2015-01-23
Hi Guys,
Thanks for the responses.  Some of the stuff was a little over my head. Let me summarize what I think people are saying.

First, after backing up the current windows system, use a windows program to partition windows to a smaller disk space.

Then, choose the "try ubuntu without installing" option, and use gparted to create partitions among the remaining (ubuntu designated) disk space.
This will involve installing gparted before installing ubuntu, but I guess that's possible.

Then, go back and install ubuntu, and choose "something else", which will now show me the different partitions, and choose one to put ubuntu on.

So some things I'm not clear on. First, on a really old dual-boot desktop I have Ubuntu 10.04 on, the grub menu has all different ubuntu options, including recovery mode.  I always just choose the top one.  I've never set up partitions manually before. I'm also not sure what a data partition is. Is it treated like an external drive? This is something that would be done automatically, I imagine, if I don't choose "something else".

Then someone mentioned mount points and filesystem types. The "something else" option has a list of devices, /dev/sda, /dev/sda{1-5}, and "free space".  Mount points are all blank, and type is listed as efi for sda2 and ntfs for all others.  I have no idea what that means. Then, there's a drop down menu for each partition I highlight, with different options (extN journaling file system, etc).

So I guess I'll have to lookup that stuff. This will be a usefull learning experience for me, especially as I am not in a hurry to replace my older machine.  Is there a resource for any of this that anyone would reccomend?

Thanks, Chopra
PS: The BIOS on my laptop does not have a "fast boot" option.  I have tried disabling secure boot, but that has no effect.

---

### Post by startas on 2015-01-23
fast boot is not an option in bios, it is windows feature. Control panel - power options - plan settings or somewhere there is check box for fast boot.

---

### Post by efflandt on 2015-01-23
For shrinking the Windows partition use Windows' own Disk Management in Administration Tools.

But first, if this computer is using UEFI maybe someone familiar with that could tell the OP if they need to do something related to that, which is something that I have not had to deal with yet. Or does Ubuntu automatically accomidate that now if BIOS is in UEFI mode?

---

### Post by sudodus on 2015-01-24
gparted comes with the Ubuntu desktop install iso file, so you need not install it.

The grub menu and its options are rather independent of the partitions. You can see partitions as separate parts or containers in the (hard disk) drive. You put a file system into the partition and then you can put and keep track of files there. gparted will give you a graphical representation of the partitions.

The simplest Ubuntu system has one root partition, which is symbolized with the slash character / and one (small) swap partition. In UEFI you must also have a very small EFI partition. Maybe you get some help at the following links

There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295").

See also these links and links from them

[https://help.ubuntu.com/community/DrivesAndPartitions](https://help.ubuntu.com/community/DrivesAndPartitions)

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

[https://help.ubuntu.com/community/Partitioning%20issues](https://help.ubuntu.com/community/Partitioning%20issues)

---

### Post by Dreamer Fithp Apprentice on 2015-01-24
Added by edit: I see Sudodus has posted succinctly while I was slowly pecking away verbosely. Some of this is probably redundant now. That's life. /me shrugs.

> **chopra said:**
>  . . . use a windows program to partition windows to a smaller disk space.More accurately, you are to use a Windows program, the name of which I forget, to SHRINK THE WINDOWS PARTITION. The same program can be used to add or delete partitions, or grow partitions, so you might call the program a partitioner or a partitioning utility or something like that. You partition a DRIVE, not an OS. A partition is just a part of the drive, managed seperately from the rest of it. Windows assigns "drive letters", like C: (traditionally the partition on which the Windows installation exists), A: & B: which are reserved for floppy drives which not too many machines have any more, and D:, E:, and so on for additional partitions. They are called drive letters because when that practice began in the OS that was the ancestor of MS-DOS, drives weren't commonly divided into multiple partitions. They are essentially analogous to the mountpoints in a unix-like system in that they are arbitrary and can be changed. In other words if you want to call the one now called C:, D:, and vice versa, you can get Windows to do that.

> **chopra said:**
>  Then, choose the "try ubuntu without installing" option, and use gparted to create partitions among the remaining (ubuntu designated) disk space.That is a good way to do it. Sudodus's point is interesting. I'm glad he caught the potential error. I'll have to look up "dynamic partitions" - I never heard of them.
> **chopra said:**
> This will involve installing gparted before installing ubuntuMaybe. If it isn't already on the live/installer thumb drive. I think it usually is. But installing isn't hard. After booting from the thumb, if gparted isn't already installed, you can install it by bringing up a terminal and typing "sudo apt-get install gparted" and pressing enter. If it asks for a password, try just pressing the "enter" key.
 > **chopra said:**
> I've never set up partitions manually before.The actual doing of it is not hard. Gparted is pretty self-explanatory. Being self-explanatory is what gui is all about really. What is not so obvious is DECIDING exactly what to do, i.e, how many partitions, how big, mounted how, etc. If you aren't clear about that I suggest you type "partitioning" in the search box at the top of the page. You can read a lot of ideas on the subject without even leaving the forum. Don't get too hung up on it. A lot of us will passionately defend our own schemes cause we all know we're right and the other schmucks just haven't seen the light yet. But just about any way you see recommended will work. Just don't pick a scheme so complicated you're not sure you understand it.

> **chopra said:**
> I'm also not sure what a data partition is.A partition where you keep your STUFF. The letter you're writing to your sister. The report you're doing for work. The novel you'll never finish. The plans for the revolution. Your Xmas pics and porn. The spread sheet modeling the effect of greenhouse gases on skirt length. Music. E-books. Etc, etc, etc. The more traditional place to keep your stuff (more formally called "data") is in /home/your-user-name/. That makes a lot of sense on a system with multiple users, especially a system with multiple users who might have data they might not want to share, which is the kind of environment 'nix systems evolved in, back in the day when computers were WAY to expensive for individuals to own and took up whole rooms. But a typical pc, used almost exclusively by one person is another matter. Many of us, me definitely included, think it makes more sense to have a seperate partition (which might or might not be on a seperate drive) mounted somewhere else (/media/data/ being my preference) to keep your stuff in and leave /home/your-user-name/ (also casually refered to as "home" or, more clearly, "your home" and alternately symbolised as "~/" or just "~") for the config files that will be put there automatically. Some people keep Stuff in ~ along with the config files but make /home/your-user-name/ just a mountpoint for another partition. If they do it that way they usually call it a "home partition". That's a very traditional approach. People who speak of a "data partition" have in mind something just for Stuff and leave the config files in ~. To me the advantages of keeping Stuff in its own directory on its own partition rather than mixed in with the config files in ~ is that it is a LOT easier to backup Stuff and System seperately. And That Is Good, because the backup strategies that make the most sense for Stuff are not the ones that make the most sense for System.  And it is a lot easier to find some specific piece of Stuff if it isn't mixed in with all the config files and vice versa. But that's a whole 'nother topic.

 > **chopra said:**
> Is it treated like an external drive?
No, not that there is much distinction between external and internal drives anyway. It is just another partition, another filesytem on another chunk of hard drive real estate. Could be internal or external.
> **chopra said:**
> This is something that would be done automatically, I imagine, if I don't choose "something else".No. Definitely not. Data partitions are not orthodox in the High Church of Unix. And AFAIK all 'nix installers follow suit.

> **chopra said:**
>  Then someone mentioned mount points and filesystem types. The "something else" option has a list of devices, /dev/sda, /dev/sda{1-5}, and "free space".   Whooooa. 5? Whacha got on the other 3? Might better find out before you go wiping them out. A standard Windows just has 2, one of which is tiny. Unless something has changed radically since I played with Windows, which is possible. I wouldn't do anything with shrinking or partitioning until you figure this out. "/dev/sda" refers to the whole drive, specifically it it the first SATA (or SCSI) drive that the bios looks at when looking for something to boot. "/dev/sda1" and so on refer to partitions of (or you could say "on") the drive /dev/sda.

> **chopra said:**
>  Mount points are all blank, Right. Mountpoints are arbitrary, not inherent. You tell it what you want the mountpoint to be. The mountpoint is where in the directory structure of the system you are installing will be shown the contents of the filesystem on that partition. So if you mount a filesystem on sda3 as "/some/directory" the contents of that filesystem will be shown as subdirectories of /some/directory when running the system you are installing.

> **chopra said:**
> and type is listed as efi for sda2 and ntfs for all others.  I have no idea what that means. NTFS is the standard Windows file system. I don't know what efi is. Might be what they call the file system they use on the little tiny partition Windows uses for it's bootloader. Dunno. If it is tiny, that is probably it. Otherwise, better look it up and find out before doing more.

> **chopra said:**
> Then, there's a drop down menu for each partition I highlight, with different options (extN journaling file system, etc).That is to set what kind of filesystem the OS you are installing should expect to find on that partition. If you check the format box it will create that filesystem. Otherwise it will expect to find it there already.

> **Impavidus said:**
>  . . .  reboot Windows a couple of times after  shrinking its partition, so that it can run its file system checks.  Then Ubuntu should detect Windows.A good idea. But if you  haven't done anything yet, I think I'd run the filesystem checks first. I  might be wrong, but I think I'd prefer to fix filesystem errors before I  shrunk the partition. And you don't need to reboot repeatedly waiting  on Windows to decide when to run the checks. I think you can just  explicitly tell Windows to run chkdsk or whatever they call it on boot  and then reboot. I've grown a little hazy on Windows since it's been  quite a while since I used it regularly. Maybe someone current can  comment on how to do that. If I were just bumbling around on a Windows  system trying to do that I'd look for some kind of disk utilities gui.  You might have to log in as admin to do that, idk. From a command line,  I'm thinking maybe the command is just "chkdisk" or maybe "checkdsk",  something like that. I think I vaguely remember the Windows equivalent  of "man command" is usually "command /?" so maybe try "chkdisk /?" and  similar variations unless somebody posts with more specific instructions  before you try it.

---

### Post by Impavidus on 2015-01-24
If I understood correctly (but I haven't used any Windows version after XP), shrinking a partition in Windows will trigger a file system check on the next reboot. The on line partition changes aren't complete, so it has to finish them during a reboot. Only after these checks Ubuntu will be able to read the NTFS partition and detect Windows correctly.

---

### Post by chopra on 2015-01-26
Hi Guys,
(First, apoloties, I realized that this thread probably should have been posted in Installation and Upgrades.)
So I've read the links that were provided, and there are some things that are puzzling.  I'm not sure if some of the information in the links is outdated.
First, one of the links says to disable quickboot/fastboot in BIOS, but these are not options in BIOS.  I did disable FastStartup from the Windows control panel. (I think someone on the board said to disable FastBoot from the Windows control panel, maybe FastStartup is the same thing. Ubuntu still can't see Windows, though.) It also says disable Intel Smart Response Technology, but, again, there is no such option any of the BIOS menus.

So I figure that's probably just a matter of changes made since the link was posted.  There was something else about making sure my USB drive was EFI only.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
However, that link also said that if my computer does not boot the installation *DVD* in EFI mode, I wouldn't have gotten to the menu screen that lets me choose to install or try.  So, I figured that this was nothing to worry about either, though I'm not entirely sure. 
[https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode)

Next, there's the issue of defragging, cleaning, and filesystem check, which were reccomended to be done before resizing.  I'm not sure if this is worth the effort or not.  I think somewhere, one of the links said that if I'm using GParted, defragging is not necessary, though I can't seem to locate it now.  Are these steps important?

edit: the check disk for errors option on the ubuntu installer reported errors on two files, though it didn't give me any further information or instructions.

Thanks, Chopra

---

### Post by chopra on 2015-02-13
COMPLETED!
Finally, after a lot of time spent shrinking and backing up windows, I installed Ubuntu side by side, and the dual boot works fine.  Dedoimedo is very helpful.  Thanks to Sudosus for the link, and all who contributed.  Just one comment:
EaseUS is an excellent third party software for shrinking windows and backing up the entire system.  After a week or so messing around with windows partitions, I just shelled out $40 for the software, and it was done, easier than tying my shoes.  I guess that's Microsoft.  

Chopra

---

### Post by sudodus on 2015-02-13
Congratulations :KS

and thanks for sharing your solution :-)

---

