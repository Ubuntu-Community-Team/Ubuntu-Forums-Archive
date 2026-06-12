---
title: "Need help using Ubuntu to save files from broken Winows PC"
date: 2013-08-05
forum: General Help
---

### Post by cheezcat on 2013-08-05
Ok, first off, two things:
1) I am not very familiar with Linux. I have seen people use it a bit, including an older version of Ubuntu, but I don't know a lot.
2) I have tried searching the forums and documentation. I have found somewhat related issues and info, but I'm having a hard time finding concrete answers to my questions, so I need some help.

I have a laptop running Windows 7. I got a random blue screen of death and it will no longer boot. It just hangs. I attempted to repair Windows with no luck. I ran some diagnostic tests and it turns out my hard drive is failing. I have most of my stuff backed up, but I would like to salvage some newer data if I can. While searching the net for help I discovered that it's sometimes possible to boot from an Ubuntu Live DVD and backup data that way. I found this guide [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/). I burnt a copy of Ubuntu 13.04 and I was hoping I could just follow the steps but I ran into some problems. This page was obviously written when an older version of Ubuntu was out. I clicked the hard drive at the side of my screen and nothing happened. I didn't know if I was supposed to double click, or if it was just slow or if it wasn't working because it couldn't mount the drive, so I tried once or twice more. When I clicked on Files and tried to access the drive that way, I got the Cannot Mount Drive message, but mine was different than the one shown in the guide. I didn't have Choice 1 and Choice 2. I wrote down some of it but not the whole thing, unfortunately. It said:[INDENT]Error Mounting /dev/sda2 at/media/ubuntu/C816FDA16FD9622: Command-line 'mount -t "ntfs" -o
[/INDENT]
I remember seeing something about input/output. I think bitmp or something was in there. I don't know if that helps at all. I copied the whole text to Libre Writer. The guide says to force the drive to mount by typing a line similar to:[INDENT]mount -t ntfs-3g /dev/sda1 /media/disk -o force
[/INDENT]
I didn't get that whole line in my error message but it looks to me like I have to replace "/dev/sda1" with "/dev/sda2," correct? Only I didn't know where to find the terminal, since the Places and Applications menus as shown in the guide are non-existent. (I have since found out I could have just typed "terminal" into the dash.) I closed the message box since I could not click on the Files window with it still open. I believe I hit the minimize button on Libre Writer and it looked like it started to shrink and then everything froze. I could move the mouse pointer but I could not click anything. I ran to my other computer to try and find out if Ubuntu had any equivalents to ctrl+alt+del and task manger and if there was some way I could unfreeze it but I couldn't find anything quickly enough. The fan got pretty loud and I was afraid it would overheat so I had to shut it down by holding the power button. I hope I didn't screw it up worse by doing that but I didn't know what else to do. So I've been poking around here trying to figure out what I should have done and how to go about trying again. Apparently the System Monitor is the closest thing to the Windows Task Manager. I think I found some page showing how to kill a program with it, but I had no idea how to bring it up since I couldn't click anything. Is there no built-in keyboard shortcut (equivalent to ctrl+alt+del)? I found some page explaining how to add your own shortcuts. Is there some way I could have opened the System Monitor while my computer was frozen? Or some other way I could have unfrozen or rebooted the computer? And as I was searching these forums for instructions, I noticed some people saying you can force mount but it isn't recommended. Why is that? I don't know of any other way I can save my data, so I figure it's worth a try. I also noticed some people talking about using certain software to backup and copy files. I'm not sure what that's about.

And just to confirm that I more or less get what's going on here, I am to:
Open a terminal.
Type "sudo /bin/bash" (and hit enter, I'm assuming) to log in as root.
Type "mkdir /media/disk" to create a directory.
Type "mount -t ntfs-3g /dev/sda2 /media/disk -o force" to force the hard drive to mount.
And then hopefully I can just copy whatever files I want to an external hard drive.

If anyone could clarify any or all of this for me, that would be appreciated.

---

### Post by carl4926 on 2013-08-05
The partition should just mount on the fly, directly from the Nautilus file manager
It does for me

---

### Post by liam2 on 2013-08-05
Hello,

Indeed, when you go into the liveCD, all your windows drives should "just" be mounted - you should see them on the left hand side, under "devices", in file explorer. You said that when you click one, it says something about being unable to be mounted.. I know one possible culprit of that is hibernation, it's especially irritating in Windows 8. But you can't boot Windows, so I'm not sure if that would be the case, nor how you'd make it fully shutdown if that were the case.

As for your terminal commands, you can actually mount your drive anywhere you like. But, following where you want to put it, your commands ought to be more like this:

*You don't need to type /bin/bash as far as I'm aware*
sudo mkdir /media/disksudo mount /dev/sda2 /media/dish -o force

First note you'd need to be super user for both these commands <-> need to type sudo twice. Second note I removed the -t (type) flag you wrote: it should be able to work that out itself. Also, it would make the error given more useful ([http://ubuntuforums.org/showthread.php?t=1694368](http://ubuntuforums.org/showthread.php?t=1694368)). 
The consensus on google seems to be that forcing a mount is a last resort. Have you tried something like chkdsk first? If you have another windows machine to hand, you can make a recovery disk with a USB memory stick, which could be used to do such a thing.

---

### Post by cheezcat on 2013-08-05
The guide explains that usually the drive won't mount properly because Windows didn't shut down cleanly, which is exactly what happened. I first tried the Ubuntu disk in my working computer and all I had to do was click on the drive and it opened.

The exact instructions in the guide say:

> What you’ll want to do is open a new Terminal from Applications \   Accessories \ Terminal on the top menu. Once you’ve done that, then  you’ll want to type in a bunch of commands, which I’ll walk you through.

 First, we’ll want to switch to “administrator” mode, which in Linux  terms is known as “root”. The simplest way to do it is with this  command:[INDENT]sudo /bin/bash

 [/INDENT]
Now we’ll need to create a directory that we’ll mount the drive on.  The full explanation of mounting drives is a little complex, so just run  this command:[INDENT]mkdir /media/disk
 [/INDENT]
Now comes the tricky part. You’ll need to type out a command very  similar to this one, but you’ll need to replace /dev/sda1 with what you  see in that message box we showed you above. This command tells Ubuntu  to use the ntfs-3g driver, and force mount even if there is a problem.[INDENT]mount -t ntfs-3g /dev/sda1 /media/disk -o force
 [/INDENT]


So normally it should just mount on its own, but since Windows didn't shut down properly that's why it has to be done manually. That's my understanding.

Now, I'm just trying to make sure I understand what you suggest doing differently. I think you meant to type that as two separate lines:[INDENT]sudo mkdir /media/disk
sudo mount /dev/sda2 /media/disk -o force
[/INDENT]
So, you're writing sudo each time, whereas the original instructions say to type sudo /bin/bash and then you don't have to type it again, I guess. Do these two methods effectively do the same thing? Your commands say dish instead of disk. I'm just checking, the h was a typo? And you say it should be able to figure out the type on its own. I read somewhere that the ntfs-3g line mounts the drive while allowing read/write access. I don't need to write, I just want to copy files, but it would seem pretty pointless if you can't read or write anything. I should have asked this in my original post, but I'm wondering if all of these commands are all still applicable regardless of the version.

Chkdsk is not an option (as far as I know) since I can't boot into Windows. I entered the setup screen before booting and used the system diagnostics tools which are not part of Windows. That was how I found out the hard drive was failing but it didn't check for errors. And I don't think making a recovery disk is really what I want to do at this point. Since the drive is dying I don't want to reinstall Windows or anything. I just want to save my files if I can. I found this idea to use Ubuntu on the HP help forums and someone mentioned the reason it works is because booting from a disk doesn't stress the failing hard drive with the reads and writes involved in booting into Windows.

---

### Post by carl4926 on 2013-08-05
I do believe Gparted will check NTFS partitions. It may help your situation.

---

### Post by oldfred on 2013-08-05
Generally Linux runs a minimal check with ntfsfix of NTFS partitions and turns on the chkdsk flag, so it runs chkdsk on next boot. But you usually have to run chkdsk to get most NTFS issues repaired.

Some of the third party Windows partition tools may run chkdsk.
 Third party chkdsk tools
Also has chkdsk and some other Windows repairs in free version:
[http://www.partitionwizard.com/features.html](http://www.partitionwizard.com/features.html)
May be able to run chkdsk from Hiren's boot CD. (mini xp.)
Hiren's Boot CD, and do a chkdsk on the XP

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

But best to make your own Windows repairCD or flash drive. If you have access to another Windows 7 system that is either 32 bit or 64 bit to match yours and any version:
      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by cheezcat on 2013-08-06
Ok, so I made another attempt. When I clicked on the drive I got this error message (I hope I copied everything right):

Error Mounting /dev/sda2 at /media/ubuntu/C816FDA616FD9622: Command-line 'mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda2" "/media/ubuntu/C816FDA616FD9622"' exited with non-zero exit status 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
NTFS is either inconsitent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabccl). Please see the 'dmraid' documentation for more details.

So I tried opening a terminal and following the instructions in the guide I mentioned above. When I attempted to force the drive to mount, I got a similar error message (in the terminal, not a message box):

ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsitent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabccl). Please see the 'dmraid' documentation for more details.

So the drive did not mount and when I tried to close the terminal I got a message box saying there was a process still running and that closing the terminal would kill it. I don't know what was still running. Was it still attempting to mount? Am I supposed to do something to log out or whatever before closing it?

I did some searching to try and figure out what this error means and what to do about it. I found a few links regarding similar errors:
[http://superuser.com/questions/521011/how-to-mount-hard-drives-for-data-recovery-in-ubuntu](http://superuser.com/questions/521011/how-to-mount-hard-drives-for-data-recovery-in-ubuntu)
[http://errors.linuxnix.com/2013/01/failed-to-mount-inputoutput-error-ntfs.html](http://errors.linuxnix.com/2013/01/failed-to-mount-inputoutput-error-ntfs.html)
[http://askubuntu.com/questions/131831/problem-mounting-my-internal-hard-drive-any-suggestions](http://askubuntu.com/questions/131831/problem-mounting-my-internal-hard-drive-any-suggestions)
[http://askubuntu.com/questions/74105/how-do-you-repair-an-input-output-error-in-an-ntfs-partition](http://askubuntu.com/questions/74105/how-do-you-repair-an-input-output-error-in-an-ntfs-partition)
They're somewhat helpful, but I'm not exactly following what's going on. Again, I don't know a lot about Linux. I don't like just typing in a bunch of commands without understanding why or what they're doing. I may be able to use this ntfsfix thing if I can figure out how.


@oldfred:
Thanks for all those links. I haven't had a chance to check them all out yet but I'll see if anything in there can help me. I doubt a repairCD will help though. When I try to boot I get the options to "Launch Startup Repair" or "Start Windows Normally," both of which just hang. If I insert my Windows 7 disc and choose "Repair Windows" it hangs there too.

---

