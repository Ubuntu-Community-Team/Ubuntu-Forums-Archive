---
title: "System unuseable after Upgrade to 12.10"
date: 2013-01-13
forum: General Help
---

### Post by Asif786i on 2013-01-13
Hi
I just upgraded to 12.12 and I cant do anything as my screen is completely messed up. Please see image attached. I can make out mouse pointer moving but I cant read anything.
 
Could it be the graphics driver? Please help as I am a newbie when it comes to this type of stuff.
 
Thanx in advance
Asif

---

### Post by ivicks on 2013-01-13
> **Bashing-om said:**
> Uniplex; Hi !
 Utilize the "nomodeset" option in the grub menu-> boot onto the desktop.
Launcher->System Settings->Additional Drivers; install the recommended driver. Reboot.

[INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT]

This is from another thread and might help with your issue.

[http://ubuntuforums.org/showthread.php?t=2104570]("http://ubuntuforums.org/showthread.php?t=2104570")

---

### Post by Asif786i on 2013-01-14
Hi ivicks
 
I tried a number of the options mentioned in that post but none of them work.
I have, however got to the command line via CTRL + ALT + F1.
 
What command can I run here to check or update graphics drivers.
My machine is a HP DV6-2112SA with an ATI Radeon card.
 
All assistance greatly appreciated.
Thanx
Asif

---

### Post by Asif786i on 2013-01-15
Hi All
 
I came across an article that states the ATI Radeon 4200 driver is not supported under Xserver on 12.12. This is because Xserv has been upgraded.
The advice was to revert back to previous version of Xserv.
I tried that but unfortunately it didnt work. I now have a completely blank screen and CTRL ALT F1 dont work either.
 
However one of the older kernels does kind of boot and and I can get to the command line.
 
Any ideas please?
regards
Asif

---

### Post by sdowney717 on 2013-01-15
Why not reinstall 12.04

What makes that easier is if you had your home folder in a separate partition from your system files. then on install, you just reuse your old home partition and exchange system files. 
I would consider copying home onto a removeable drive and setting up a new OS with a separate home partition.
No chance you can pop in an Nvidia card is there?

---

### Post by sdowney717 on 2013-01-15
I did it this way
[http://ubuntuforums.org/showthread.php?t=2097275](http://ubuntuforums.org/showthread.php?t=2097275)

I installed a fully functional 12.04 64 bit on an external usb hard drive.

I then wanted to clone copy it onto an entirely different computer.
It worked out fine. Used separate partitions for system and home.

After the copy, all I had to do was edit the uuid names into fstab on the other pc.
Home files for other users are just a folder in the home folder. So you can even add new users to the system by copying home folders and adding a new user with that folder name.

---

### Post by Asif786i on 2013-01-17
Hi All
 
Some progress to report.
I installed fglrx drivers and set the graphcs mode to 771 in grub settings. I can now get to GUI but in low res mode. However I dont have launcher or top status bar. Does that mean Unity is not running? CTRL+ALT+F1 is now working again.
 
Or is it simply a matter of chaging the mode to higher than 771 ?
 
Regards
Asif

---

### Post by QIII on 2013-01-17
I'm going to suggest a couple of things.  You may take them for what they are worth.

It sounds like you did not uninstall the ATI driver before you upgraded, which would have been a good idea.  Upgrades, as opposed to reinstalls, often do not work well when proprietary drivers are installed.

The method of getting the ATI driver to work in Quantal with an HD 4XXX card by downgrading X Server is unwise.  It breaks Quantal and the future implications are unknown.

You would be best served with one of two set ups:

1.  An unbroken Quantal (12.10) using X Server 1.13 and the default open source Radeon driver.

2.  Precise (12.04) with the ATI driver.

---

### Post by Asif786i on 2013-01-17
Hi QIII
 
Thanx for your suggestions.
 
Am I right in thinking that I currently have the open source radeon driver installed?
 
If so I just need to upgrade Xserver back to 1.13. How do I do that?
 
regards
Asif

---

### Post by Asif786i on 2013-01-18
Hi all
 
I dont seem have the directory /usr/share/xserver-org
 
I was hoping to check my card against the list.
 
Any ideas why its missing and how to get it back?
 
Regards
Asif

---

