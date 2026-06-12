---
title: "HELLLLLLLLLLLLLLLLLP (HDD/boot problems)"
date: 2012-10-31
forum: General Help
---

### Post by sherlockhomeboy on 2012-10-31
[SIZE=2]Hello good people:[/SIZE]
  [SIZE=2]Did I mention that I need help? If not  . . . . I really need help! [/SIZE] 
 [SIZE=2]Got big problems are with my Toshiba Satelite HDD, and/or other components. In a nutshell: [/SIZE] 
  
[SIZE=2]* Can't access HDD at all.[/SIZE]
  [SIZE=2]
* NO RECENT BACKUP OF DATA. Go ahead, scold away . . . but the very day I decided to TRY to back up was the day when Vista decided to stop booting. [/SIZE] 
  [SIZE=2]
* Tried all modes to boot Vista. Won't work. Keeps hanging at the ATICPIE driver. [/SIZE] 
  [SIZE=2]
* No Windows recov disk – discovered belatedly that Toshiba provides only a full reinstall disk, – which for data recovery purposes, is as useful as a flame-throwing fire extinguisher.[/SIZE]
  [SIZE=2]
* For a time, I was able to access HDD via Mepis and Ubuntu (11.04.x) Live CD's, and thought: Whew, this buys me a little time. I resumed somewhat normal usage of my computer, while also locating, consolidating and organizing my voluminous and very disorganized files prior to backing up. Also had to clear a few  USB's (since I haven't had $$ to buy bigger ones, nor an external HDD). [/SIZE] 
 [SIZE=2]
During this time, I got sidetracked with trying to make a bootable  Mepis stick – which proved to be its own very big headache. [/SIZE] 
  
[SIZE=2]* **BUT --** before I actually managed to back up, the damn HDD stopped mounting altogether, in either Mepis or Ubuntu! Curses! :mad:
[/SIZE]
[SIZE=2]Ubuntu keeps telling me to run Windows chkdsk, but my Windows are broken.  I tried to force mount in Ubuntu , with no luck. Ubuntu Disk Utility can't mount; neither does Gparted. (At least, Gparted is showing no sign of progress after about 40 minutes of "pending"...)[/SIZE]
  
[SIZE=2]* SMART self-test: The first couple times I was fooled by the green light and the message “Disk has a few bad sectors,” which didn't seem very threatening. Only later, running the detailed test (yesterday) did I find out that by “few” it meant one reallocated and 59 pending – which according to some comments I've read, is **very bad**. (Is it?)[/SIZE]
 

 [SIZE=2]* In the midst of all this, I've also been distracted sometimes by  spontaneous shutdowns, [/SIZE][SIZE=2] which may have done further damage to the HDD. [/SIZE][SIZE=2]This seems to be related to a bad power cord and a low battery. (At the moment, can't afford to replace either ..) At least I figured out that when I hear a faint clicking sound coming from inside the laptop, a shutdown is coming. The faster the clicks, the more imminent the shutdown. If slower, or nonexistent, then I'm fairly safe. Also, before a shutdown, the DC cord heats up at a certain spot, probably where there's a kink. [/SIZE] 
 [SIZE=2]If I adjust the cord just so (and clamp it in place) the clicks will stop, the cord cools down, and my laptop stays on. For the last few weeks, it has been stable when running Ubuntu. (Try to boot a Mepis LiveCD, though, that's another thing ... shutdowns start happening again!) :confused:[/SIZE] 
 [SIZE=2]But that's why I'm in Ubuntu now. For the most part, it's been smooth sailing power-wise.
[/SIZE]
 [SIZE=2]Have any of you seen these types of problems? What can I do to a)  [/SIZE][SIZE=2] avert an epic HDD fail(ure)? , b) [/SIZE][SIZE=2]rescue all my data? [/SIZE]

 [SIZE=2]I can provide further details if needed. Thanks in advance!:guitar:
[/SIZE]

---

### Post by oldfred on 2012-11-01
Are the clicks from a fan saying it is too hot? Or from a hard drive saying it is about to fail?

I always considered green is ok, it is growing numbers of bad sectors in a short time that can be an issue. Of course too many is a problem.

You have to have consistent power or you corrupt drive and cause even more issues.

You should have a repairCD or USB for the current version of every system installed. But you can use just about any version of Windows repairCD to run chkdsk. I used a Windows 7 repairUSB to run chkdsk on my XP install. It worked better than XP's chkdsk but changed boot sector to Windows 7 which I had to change back.

If you have access to another computer, preferably 32 or 64 bit to match yours, you can make a repairCD or USB.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by Wim Sturkenboom on 2012-11-01
My first step would be to take the HD out and place it in another system (friend / family) and try to pull your data off. You might have to use tools like testdisk/photorec to do some data recovery.

I think your HD is on it's way out and every power cycle might be another nail in its coffin.

---

### Post by sherlockhomeboy on 2012-11-04
* THANKS, Fred & Wim. Luckily, I did think of a computer guy*  I know, found his number,  and he was able to take the HDD out and run chkdsk on it for me for free. The HDD will now mount and chkdsk apparently kept all data intact. He did not have time to let me copy it all. I have to do that at home, since my stuff was INCREDIBLY disorganized, spread across 3 different users, which over 3-4 years has somehow resulted in me having SEVEN different desktops and God knows how many 100s of subdirectories. 

At the moment, I have no way to do a full disk image. I will have to gather & weed out a lot of less important stuff  (such as a lot of saved webpages, stuff like that) and then copy the most critical data to several USB's. I haven't had time to do this yet, but will be starting tonight. 

Later, perhaps after installing Mepis (I want to try out the latest version), I can then burn everything to DVDs. 
 
Wim, in the SMART test, it says self-tests "completed OK" and "Disk has a few bad sectors" -- specifically, 113.  If it doesn't get any worse than 113, and if no other warnings come up, would you say I'm safe for the time being (as long as I keep everything backed up, of course)? 

Fred: the clicks seem to have something to do with power supply. When I twist the power cord (the thin DC end) one way, the clicking starts from inside the computer, but on the opposite end from where the HDD is located. If it accelerates to about  2x/second, the computer will very shortly click off. However, if I twist the cord the other way, the clicks will slow or stop, and the computer stays on! So it's power. Maybe the sound is coming from the battery, I dunno. The battery is nearly depleted and will only hold about 1 min of power. 

I have clamped the cord so that it stays in the same position and so far, so good. I'm pretty confident that when I get a new power supply, this won't even be a worry. I just reported it because I wondered if any others had had that problem. 

Thanks for the suggestions. I will make sure to get a Windows repair CD, not only for myself (I'm about done with Windows, I think) but to help others.


* **PLUG:** If you're in south suburbs of Chicago, see his site: [http://www.sg-guitars.com](http://www.sg-guitars.com) He does all kinds of computer work, but nowadays focuses on repair, rescue, fixing people's Windows problems, and giving you all kinds of cool freeware.  He also makes electric guitars from genuine Fender/Gibson parts. He's also got a bunch of guitar-god videos, and something he calls the "D-Crapifier" for your PC, available for free.

---

