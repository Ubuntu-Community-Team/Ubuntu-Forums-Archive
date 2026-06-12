---
title: "Unable to boot Windows Install CD on machine with Ubuntu already installed"
date: 2008-01-19
forum: General Help
---

### Post by Will Pittenger on 2008-01-19
I have a machine that started out with a blank hard drive.  Using my Partiton Magic emergency floppy (the CD wasn't booting for some reason), I created a series of NTFS 3.0 partitons, one as a primary with the others as secondary.  I then had it resize them to make room for Ubuntu's partitions.  I then installed Ubuntu before Windows.

I didn't know how to format the partitions that Ubuntu needed, so I had it create them during installation.  PartitonMagic only made room.

Now both my Windows XP Pro SP1 install disk and [BartPE]("http://en.wikipedia.org/wiki/BartPE") (a LiveCD version of XP) won't boot.  BartPE shows the standard XP boot graphic (with the animation going), but no harddrive or CD activity.  It just sits there.  The XP install disk does something similar.

Worse.  My PartitionMagic floppy can no longer read the drive.  I also had GParted (which only runs at all when I boot the Ubuntu LiveCD) create partitions on a USB 2.0 portable drive.  PartitionMagic now is convinced that my 120 GB portable is a 500 MB drive.  That's only half a gig!

Can someone help me straighten all this out?

---

### Post by logos34 on 2008-01-19
PM and gparted don't play together nicely.  And you should always install windows before ubuntu (mainly because of bootloader issues.) although I realize you're having trouble.

Here's what I'd do:

Boot the ubuntu live cd and use gparted to delete all the partitions.

Try to boot XP disk.  If successful, create ntfs partition(s) the desired size (do a FULL format for each), leaving the remaining disk space empty for ubuntu.  You can have at most 4 primary partitions, so if you create 3 primary ntfs, you need to make the last one an extended and put ubuntu inside it (ubuntu requires at min an ext3 / and a /swap partition).

Boot into XP and check that all is working ok.  

Reinstall ubuntu on remainder of disk.  It will overwrite mbr with grub, which will give you a choice os OS's at boot.

---

### Post by samosamo on 2008-01-19
just to clear all that up, your main problem is that you're unable to boot off of a CD?  it doesn't matter what OS is installed, whether its Windows or ABCOS or XYZOS, the problem is the boot order in the BIOS or another hardware configuration issue.

---

### Post by Will Pittenger on 2008-01-19
> **samosamo said:**
> just to clear all that up, your main problem is that you're unable to boot off of a CD?  it doesn't matter what OS is installed, whether its Windows or ABCOS or XYZOS, the problem is the boot order in the BIOS or another hardware configuration issue.
The CDs won't boot.  I have the CD drive **[COLOR=Red]before[/COLOR]** the hard drive in the boot order.  I doubt the hardware is an issue as both CDs, as I stated above, do start booting, but fail to get very far.

> **logos34 said:**
> PM and gparted don't play together nicely.
I now see other partition managers listed in Add/Remove...  Do they work better?

> **logos34 said:**
> And you should always install windows before ubuntu (mainly because of bootloader issues.) although I realize you're having trouble.

Here's what I'd do:

Boot the ubuntu live cd and use gparted to delete all the partitions.

Try to boot XP disk.  If successful, create ntfs partition(s) the desired size (do a FULL format for each), leaving the remaining disk space empty for ubuntu.  You can have at most 4 primary partitions, so if you create 3 primary ntfs, you need to make the last one an extended and put ubuntu inside it (ubuntu requires at min an ext3 / and a /swap partition).

Boot into XP and check that all is working ok.  

Reinstall ubuntu on remainder of disk.  It will overwrite mbr with grub, which will give you a choice os OS's at boot.
And I am finally starting to get Ubuntu configured.  Actually, now that I know what Ubuntu needs for partitions, PM can create them.

Other things:[LIST=1]
[*]Grub can detect and boot XP partitons?
[*]With XP, I want to put some swap space on my USB external.  Windows can use multiple swap files when they are on different physical drives as that allows it to access both at the same time.  Can Linux do that?  I have yet to push Linux's memory needs to the point of needing swap files.  That won't last.
[*]You did not mention what to do with the portable.  GParted doesn't see any partitions there.[/LIST]

---

### Post by ChaosParser on 2008-01-19
> **samosamo said:**
> just to clear all that up, your main problem is that you're unable to boot off of a CD?  it doesn't matter what OS is installed, whether its Windows or ABCOS or XYZOS, the problem is the boot order in the BIOS or another hardware configuration issue.

This is actually incorrect. 

Windows CDs will occasionally halt when a non windows filesystem is on a drive.  It does not happen often, but it DOES happen. 

Essentially, Windows Setup is inspecting the hard drive, seeing ext3, getting confused and giving up. 

Reformatt to NTFS with the Ubuntu Live CD, then reinstall windows, THEN reinstall ubuntu. 

Good Luck!

---

### Post by logos34 on 2008-01-19
> **Will Pittenger said:**
> I now see other partition managers listed in Add/Remove...  Do they work better?

there's qtparted, but it uses libparted too.  not much diff except the kde gui.  You could try fdisk or cfdisk from the command line.  

> And I am finally starting to get Ubuntu configured.  Actually, now that I know what Ubuntu needs for partitions, PM can create them.

Why use PM when it's causing so many problems? 

> [*]Grub can detect and boot XP partitons?

Grub is *usually* very good at detecting them during installation and adding the appropriate menu.lst entries.

> [*]You did not mention what to do with the portable.  GParted doesn't see any partitions there.

I thought you said it was PM that didn't detect the partition size correctly.  So you formatted the external with gparted and now it can no longer see the partitions?

---

### Post by Will Pittenger on 2008-01-19
> **logos34 said:**
> there's qtparted, but it uses libparted too.  not much diff except the kde gui.  You could try fdisk or cfdisk from the command line.
From the Linux command line?  I don't have the DOS version of fdisk.  XP now has diskpart, and it only runs under Windows.  It doesn't have any real mode support.

> **logos34 said:**
> Why use PM when it's causing so many problems?
It's GParted causing problems, not PM.  PM partitions are accepted by the Windows installer.  Others in this thread have stated that Windows can't accept GParted partitions.

> **logos34 said:**
> [quote=Will Pittenger]
[*]You did not mention what to do with the portable.  GParted doesn't see any partitions there.I thought you said it was PM that didn't detect the partition size correctly.  So you formatted the external with gparted and now it can no longer see the partitions?[/quote]
PM sees the drive a empty with only 500 MB available.  GParted sees the drive as empty.  It had failed to create the partitions I asked it to create.

When I install Ubuntu, is it possible to save my existing Ubuntu config on my portable?  I plan to do that with my Firefox config if I can get it partitioned.

What about extra swap space for Linux?

---

### Post by logos34 on 2008-01-19
For swap, see this:
[http://www.linux.com/feature/121916](http://www.linux.com/feature/121916)

My experience with Gparted is that it works fine creating ntfs partitions which I can then install windows xp on (32-bit home and x64 pro).  

All I can can say is try the GParted Live CD--it's better (and more up-to-date) than the version on the ubuntu install cd.

To save your existing ubuntu config either copy (cp -a or tar) your home directory to the usb or [make a separate /home]("http://www.psychocats.net/ubuntu/separatehome") before you reinstall.   Back up your installed packages with AptOnCD.

Good luck.

---

### Post by Will Pittenger on 2008-01-20
> **logos34 said:**
> For swap, see this:
[http://www.linux.com/feature/121916](http://www.linux.com/feature/121916)

My experience with Gparted is that it works fine creating ntfs partitions which I can then install windows xp on (32-bit home and x64 pro).  

All I can can say is try the GParted Live CD--it's better (and more up-to-date) than the version on the ubuntu install cd.
How big of a download are we talking?  I have dial-up for the time being.  DSL is expected next week, but is no sure thing.

> **logos34 said:**
>  To save your existing ubuntu config either copy (cp -a or tar) your home directory to the usb or [make a separate /home]("http://www.psychocats.net/ubuntu/separatehome") before you reinstall.   Back up your installed packages with AptOnCD.
What will that omit?  My screen resolutions got messed up by accident, and I don't see a way to reset them.  I misunderstood what Linux was telling me and botched them up.  Also, I spent a lot of time downloading packages for upgrades and other stuff.  Even with DSL, I would prefer not to have to redownload them.

---

### Post by logos34 on 2008-01-20
gparted live cd = [~54 mb download]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828") 

cp -a will do even the hidden folders.

You won't have to redownload anything if you use AptOnCD

---

### Post by Will Pittenger on 2008-01-20
> **logos34 said:**
> gparted live cd = [~54 mb download]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828")
Too big to dl without DSL.  That may have to wait.

> **logos34 said:**
> cp -a will do even the hidden folders.
I would have probably used the GUI for that.

> **logos34 said:**
>  You won't have to redownload anything if you use AptOnCD
What is that?

---

### Post by logos34 on 2008-01-20
[http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html](http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html)

---

### Post by imjustabill on 2008-01-20
I had a similar problem, but found an easy way to get around it. Go into your BIOS and disable your hard drive. I'm not exactly sure why it works, but when I tried it, the installer started right up. Make sure you re-enable your drive when the installer has you reboot. Also, installing XP over Ubuntu will wipe out grub, so you'll have to reinstall that from the live cd.

---

### Post by Will Pittenger on 2008-01-20
> **imjustabill said:**
> I had a similar problem, but found an easy way to get around it. Go into your BIOS and disable your hard drive. I'm not exactly sure why it works, but when I tried it, the installer started right up. Make sure you re-enable your drive when the installer has you reboot. 
Interesting.  However, at first, I misread your suggestion.  I read "disable your hard drive" as "so it can't be read".  That wouldn't work.  I do understand now that you only meant the boot order.  How does one reinstall Grub?  Also, if I go that route, I need to fix my screen resolution problem.

> **imjustabill said:**
> Also, installing XP over Ubuntu will wipe out grub, so you'll have to reinstall that from the live cd.
You are talking about XP and Ubuntu on separate partitions, right?

> **logos34 said:**
> [http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html](http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html)
APTonCD is now installed.  Not sure when I will make the disk.  Would that be a full fledged Ubuntu Install disk with the settings pre-made?

---

### Post by Will Pittenger on 2008-01-20
OK.  I have QTParted and GParted downloaded and installed.  QTParted can't find any devices.  GParted does find them, but errored out creating an extension partition.  This version of GParted It also does not support creating NTFS partitions.

Edit: QTParted shows the external drive now that I turned it on.  It still doesn't see the internal.  When I told it to create an Ext3 partition on the external, it gave the same error that GParted gave.  The presence of NTFS partitons may be why it doesn't see that drive.  Opinions?

---

### Post by IOA on 2008-01-20
I am also having your problem. Do you seriously need to delete EVERYTHING on your hard drive to get the Windows XP installer working? I have the exact same architecture as  you, the same Windows SP1 disk, the same LiveCD....

>_>
<_<

I can create NFTS and Fat32 partitions, but I heard that you're supposed to go with FAT32 because it can be read by both Linux and Windows.

---

### Post by Will Pittenger on 2008-01-20
> **IOA said:**
> I can create NFTS and Fat32 partitions, but I heard that you're supposed to go with FAT32 because it can be read by both Linux and Windows.
My understanding is that Linux can mount NTFS.  However, it fails to mount the empty NTFS volumes that I created earlier.

---

### Post by IOA on 2008-01-20
My issue is the damn Windows XP not being able to be booted up. It shows the files when I put it in my computer, but it just won't boot up when I tell it to.I emptied all my drives and now it gives me "Boot From CD* :* DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"I pressed enter with it in and it failed. Gave me the same message.

And it still can boot up Ubuntu disk....interesting.

---

### Post by imjustabill on 2008-01-20
> **Will Pittenger said:**
> Interesting.  However, at first, I misread your suggestion.  I read "disable your hard drive" as "so it can't be read". 
Actually, that's exactly what I mean. Just go into the bios at turn the drive off. For whatever reason, the installer will start fine, recognize your disk, and let you install just fine. When the installer reboots after copying files to the drive, you have to turn it back on. 

> 
You are talking about XP and Ubuntu on separate partitions, right?


Yep, When you install XP, it will overwrite the MBR with the windows bootloader, so you have to reinstall grub from the live cd ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) ). You

---

### Post by IOA on 2008-01-20
What do you mean, disable hard drive? Is that in Advanced BIOS settings or CMOS?

What is it called? Or do I just replace all boot devices with cdrom?

---

### Post by imjustabill on 2008-01-20
> **IOA said:**
> What do you mean, disable hard drive? Is that in Advanced BIOS settings or CMOS?

What is it called? Or do I just replace all boot devices with cdrom?

I just went into my bios settings, went to the drives tab, and completely turned the drive off, so as far as the bios is concerned it's not even connected. However, your error would make me think there's something wrong with your install cd if you're getting that message.

---

### Post by IOA on 2008-01-20
Damnit...I'll try again.

~EDIT~

**** this ****. It's not going to work. There is nothing in my BIOS that allows me to enable or disable hard drives.

---

### Post by Will Pittenger on 2008-01-23
> **imjustabill said:**
> [quote=Will Pittenger;4174490]Interesting.  However, at first, I misread your suggestion.  I read "disable your hard drive" as "so it can't be read".Actually, that's exactly what I mean. Just go into the bios at turn the drive off. For whatever reason, the installer will start fine, recognize your disk, and let you install just fine. When the installer reboots after copying files to the drive, you have to turn it back on.[/quote]
I did that and BartPE could boot.  However, its partition manager, DiskPart (older copy that can't deal with LBA addressed drives correctly), refused to see the external at all which it used to do.  Part of the portable's problem might have been that BartPE wouldn't boot until the portable was turned off.  However, I expected XP (BartPE is a free alternative to WinPE and is  built around XP) to see the drive once it was turned on.  Furthermore, the only thing I could there was to clean the internal -- which can't happen until I get stuff onto the portable.

Windows didn't even get as far as before.  I saw it show "Setup is inspecting your hardware."  After a couple of seconds, that vanished and the screen stayed completely blank with no drive activity.

I have until January 31st to get Windows installed.

---

### Post by tj.baker on 2008-01-27
> **Will Pittenger said:**
> 

Windows didn't even get as far as before.  I saw it show "Setup is inspecting your hardware."  After a couple of seconds, that vanished and the screen stayed completely blank with no drive activity.

.

This is where I am ..... same response...

I'll let you know if I find anything.... 

tj

---

### Post by Will Pittenger on 2008-01-28
It turned out that I still had my external drive enabled.  I took that out and it booted.

---

