---
title: "Can't make bootable Windows 7 USB stick in Ubuntu 14.04"
date: 2015-01-04
forum: General Help
---

### Post by mctwizle2 on 2015-01-04
I was sick of Windows and went full blown Ubuntu.  I wiped the drive completely and installed Ubuntu.  I can do everything I need to do in Ubuntu except I can't play a game I want to because I cant get everything working correctly.  I have decided to dual boot Ubuntu and Windows and just use Windows when I want to play games.  I have the image of Windows 7 I want to load from a USB stick.  I have been running in circles trying to get it to work.  I finally got an older version of Unetbootin to recognize my USB drive ( fresh format, NTFS ).  I followed some guides and always get stuck somewhere.  The most recent one is Unetbootin says the drive isn't mounted.  So I google and find how to mount it.  Come to find out Ubuntu says it is mounted.  I just want to put this Windows 7 iso on my flash drive, boot into it and load Windows 7 ( ick ) and then load Ubuntu for dual booting action.  My Ubuntu skill rating is 1/10 so take it easy on me.  Any help would be greatly appreciated.

-- The Twiz

---

### Post by piperdown10 on 2015-01-04
Could you burn the Windows iso onto a disc and install it that way?

---

### Post by yancek on 2015-01-04
The link below explains how to put windows on a flash drive and boot it from Grub after installing it to the drive.  I tried it after seeing it in another post here and it does work.  If you are not familiar with Linux/Ubuntu, I would suggest you read through it a few times before beginning so you understand the steps.  After going through this process, you should be able to set the flash drive to first boot priority in the BIOS and boot and install windows.  I haven't gone past starting it because I don't have any interest in installing windows.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

Here's the link to the other post which might have some helpful info.

 
[http://ubuntuforums.org/showthread.php?t=2258763](http://ubuntuforums.org/showthread.php?t=2258763)

---

### Post by mctwizle2 on 2015-01-05
@ piperdown10  I had one disc left and when I burned it ( in Ubuntu ) it hangs up at 100% complete but checking checksum never completes.  I cancelled but the disc seems to be trashed.  Probably going to stop and buy some after work.

@ yancek  I followed the first one and got some errors along the line somewhere.  I'm at work and can't remember off the top of my head.  I also tried the 2nd method in the next post.  I seen it somewhere else but was getting other errors.  I will try them both when I get home and post more information. 

Thanks for the quick replies.  I love messing around with Ubuntu.  It has that "new car smell" for me.

---

### Post by yancek on 2015-01-05
I'd suggest you stick to the first link which has the actual explanation of the process.  Isn't really that complicated but I had some problems with one of the flash drives.

---

### Post by mctwizle2 on 2015-01-05
Ok I am trying to use the method in the first link.  I get to the part where you open terminal and put in ' [FONT=inherit]sudo grub[/FONT][FONT=inherit]-[/FONT][FONT=inherit]install [/FONT][FONT=inherit]--[/FONT][FONT=inherit]target[/FONT][FONT=inherit]=[/FONT][FONT=inherit]i386[/FONT][FONT=inherit]-[/FONT][FONT=inherit]pc [/FONT][FONT=inherit]--[/FONT][FONT=inherit]boot[/FONT][FONT=inherit]-[/FONT][FONT=inherit]directory[/FONT][FONT=inherit]=[/FONT][FONT=inherit]"/media/<username>/<drive_label>/boot"[/FONT][FONT=inherit] [/FONT][FONT=inherit]/[/FONT][FONT=inherit]dev[/FONT][FONT=inherit]/[/FONT][FONT=inherit]sdX ' .  I replaced the stuff inside the < > so it looks like this ' sudo grub-install --target=i386-pc --boot-directory="/media/aaron/2F6ED3C207D0E52D/boot" /dev/sdb1 ' . 

After that I get this error :
grub-install: warning: File system `ntfs' doesn't support embedding.
grub-install: error: embedding is not possible, but this is required for cross-disk install.

I am going through google posts trying to figure this error out but am getting more confused.  Everything that comes up sounds more advanced then this should be.  Just wanting to create a windows usb boot stick.
[/FONT]

---

### Post by LostFarmer on 2015-01-05
> [FONT=inherit]sudo grub-install --target=i386-pc --boot-directory="/media/aaron/2F6ED3C207D0E52D/boot" /dev/sdb1[/FONT] Your command has an error- replace /dev/sdb1 with /dev/sdb.

> [FONT=Courier New]/dev/sdX[/FONT] with the USB drive, not the partition (e.g. [FONT=Courier New]/dev/sdb[/FONT])

---

### Post by mctwizle2 on 2015-01-05
Ok.  I changed it to /dev/sdb and it gives the message ' sh: 1: /etc/default/grub: 0#: not found ' but then says ' Installing for i386-pc platform. Installation finished. No error reported. ' so I continued on and got to the part where create a text file and I copied what is on the screen and replaced <drive_UUID> with [COLOR=#000000]2F6ED3C207D0E52D.  It says to save it as grub.cfg and put it in the boot/grub folder.  When I go to the boot folder ( in the USB drive ) there is no grub folder so I just saved it there ( in the boot folder ) and tried booting from it.  It just brings up a command window that says grub 2 and some other stuff.  I don't see anything that says windows or am not sure of the command to put in there.  I went back and made a folder called grub in the boot folder in the USB drive and moved the grub.cfg file into it.  When I try to boot from it I get the same screen.  Not sure what to do.[/COLOR]

---

### Post by yancek on 2015-01-06
It does actually tell you that you need to create the grub directory in the boot directory on the flash drive.  It is just below the grub.cfg template on the page.  All these file names need to be lower case letters so make sure of that.   You should see on screen when you boot, whatever is between double quotes on the menuentry line.

>  it gives the message ' sh: 1: /etc/default/grub: 0#: not found 

I don't know why you would get that message, I never saw it when I ran through the process.  If you got the installation finished message it should be OK.  If it was successful, it should boot after 15 seconds or when you hit Enter.   Post your grub.cfg file.

---

### Post by LostFarmer on 2015-01-06
> it gives the message ' sh: 1: /etc/default/grub: 0#: not found '  that indicates an error in /etc/default/grub -- some line start with "0#" that needs to be deleted or changed to "#0".   That error likely will not stop grub-install from working , but not sure.  

When you made and formated the usb partition, did you give it a Label ?   If yes:
With the USB stick removed, open a terminal and run  : ```
ls /media/aaron/
``` does it list a directory named  "[COLOR=#000000]2F6ED3C207D0E52D" ?[/COLOR] If yes, insert your USB drive, make sure sdb1 is mounted and rerun grub-install command with the Label name not the UUID #.

---

### Post by mctwizle2 on 2015-01-07
OK.  I had too much stuff to do last night so couldn't get around to messing with it.  I will after work.  On a cooler note my GF called and asked if she could use my computer in the game room.  I didn't care of course and told her the password.  About 2 hours later I got home and she was poking around in the software center with a list of stuff she wants to download.  I think she might be a fan now too.

---

### Post by mctwizle2 on 2015-01-08
@ lostfarmer  THANK YOU!!!  That was the trick.  Changed it to the label I gave it instead of the UUID and it fired right up.  It was late and I fell asleep during the install but cant wait to get home from work to get that rig dual booting.  You guys are gentlemen and scholars and I thank you.

---

