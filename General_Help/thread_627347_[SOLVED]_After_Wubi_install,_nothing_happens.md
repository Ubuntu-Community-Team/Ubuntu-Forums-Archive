---
title: "[SOLVED] After Wubi install, nothing happens"
date: 2007-11-30
forum: General Help
---

### Post by Planets on 2007-11-30
Hello all,

I just got finished downloading the ISO that Wubi installed. When it asks me to restart, I do. Nothing happens, though. What I'd expect is Ubuntu would finish installing during the reboot, but I just boot into Windows Vista as if nothing has happened.

Any thoughts?

Thanks.

---

### Post by ago on 2007-11-30
What version of wubi did you use? Possibly the bootloader was not modified successfully or you have multiple bootloaders
If you use Vista bootloader you can use EasyBCD to check it

---

### Post by Planets on 2007-11-30
I used this one:

[http://www.wubi-installer.org/devel/minefield/Wubi-7.10-alpha-rev386.exe](http://www.wubi-installer.org/devel/minefield/Wubi-7.10-alpha-rev386.exe)

Also, EasyBCD says I only have one entry. Thanks in advance for your help.

---

### Post by ago on 2007-11-30
Type %temp% in windows file manager and post the log here

---

### Post by Planets on 2007-11-30
Sorry...the file manager?

Edit: Not sure if you mean this one.

---

### Post by Planets on 2007-12-01
Okay, I seem to have made a little bit of progress. I uninstalled Wubi by running the installer again, and then reinstalled. This time, Ubuntu-Linux is now in the boot menu, but selecting it just leads to a black screen. At this point, Wubi is installed, but Ubuntu is not. Now, though, I can't install at all. Wubi keeps crashing in Vista when I attempt to install.

---

### Post by Planets on 2007-12-02
Good news, I have fixed it. This is what I did if anyone is having the same problem:

1. Downloaded a new ISO and installer
2. Used EasyBCD to add Ubuntu to the boot list, this made a folder named "NST", with one of the files inside being "menu.lst"
3. Installed Wubi
4. I replaced the menu.lst file in the NST folder with the one that Wubi installed.
5. Restarted, waited about 10 minutes. Computer booted back into Windows
6. Restarted again. Now I'm posting on Ubuntu.

Cheers.

---

### Post by paetyndog on 2008-02-04
Hi all,
Just joined and not even been able to boot to Ubuntu yet. This thread jumped out as my exact problem. I used Wubi-7.10-alpha-rev386.exe, and the download and installation completed with no errors. I rebooted, I see a flash on a black screen saying something (maybe) like "No boot.ini, using c:\Windows" (again, maybe --  it happens fast) - Windows boots normally after this, but no option to boot to anything else

I dunno if the wubi installer wiped out my existing boot.ini, or if it was never there... either way, I've looked for c:\boot.ini with "hide protected operating system files" diabled and "show hidden files" enabled"  and I don't see it

Even launching Control Panel -> System -> Advanced -> Startup and recovery gives me "The c:\boot.ini file cannot be opened. Operating System and Timeout settings cannot be changed"

I am on XP.  I've considered CREATING a boot.ini based on some samples, but I'm not 100% sure which disk and which partition to reference - I'd hate to lock myself out of windows..

Any suggestions? Newer version of Wubi?

TIA,
p

---

### Post by ago on 2008-02-04
Might well be that boot.ini wasn't there to begin with, since wubi does not delete boot.ini, it only appends a line to it. That would also explain why you did not have a boot entry at all. Regenerating the boot.ini file is quite easy, but you might want to keep a linux live CD around in case you have problems so that you can edit (or delete) the boot.ini file again.

---

### Post by paetyndog on 2008-02-05
Hi guys,
I figured it out - I am on an IBM/Lenovo laptop which has an intel pro network adapter - they install a boot manager to allow the adapter to boot from the network, or boot on network activity or something else. 

This is what must have removed my boot.ini (maybe) - in any case, since I was still getting the "invalid boot.ini message, I decided to make up my own boot.ini from scratch. But to make sure I got the digits right in the file, I started windows in safe mode where it output the exact location (diskNo, and partiionNo) that was valid for my existing Windows installation :

Here is my newly created boot.ini
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional" /fastdetect

I restarted with this boot.ini just to make sure windows came up, uninstalled wubi, and reinstalled - this time on reboot, I was given the option to boot to ubuntu.

Here is my new/updated  boot.ini
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional" /fastdetect
c:\wubildr.mbr="Ubuntu-Linux"


Wireless worked great, but even the 15G drive space left only 3G free, so I'm gonna free up some space and reinstall will as much of my Windows drive as I can.

It was news to me that from Ubuntu, I could mount my other data drives and see all the files - cool

Thanks - I'll be back I'm sure

---

### Post by ex-navy on 2008-02-07
I have made the same error that you have made . 

I burned the iso image to a CD, checked in my bios that the DVD drive was first to boot, re-booted the PC and nothing happened. No cd live.

So,  I explored the CD and inadvertently double clicked on wubi-cdboot.

My XP boot.ini is now called boot.ini.backup here: 

C:\windows\pss folder.

and now have these files showing here:

C:\wubildr 
C:\wubildr.mbr
C:\WUBI-CDBOOT.exe -1BOD87F0.pf

I understand that wubi-boot is the Windows installer for Ubuntu.

If I reboot, will I have lost my WIN XP mbr.

If so, how can I get it back??

What can I do??

The PC has not been re-booted and is still running in XP home

Thanks for any help!!

---

### Post by ago on 2008-02-08
Windows-cdboot simply allows you to boot off a physical Live CD without editing the bios. 

It does not alter the MBR, it only adds a new boot option to the existing bootloader and it can be uninstalled so that you will not see the boot menu entry anymore. You can boot into windows and Linux at will.

If you do use the CD and click on the install button though (and after that confirm your changes), the MBR/default bootloader will be replaced but you will still be able to boot into Windows.

---

### Post by ex-navy on 2008-02-10
Ok,

Thank you for your reply.

Not being familiar with Linux and always the perception that something will go wrong with "windows", you have provided me with confidence.

As I understand it, the iso image I downloaded can be run  from the CD without changing anything on my PC. More like a "test drive" without changing the PC. Just double click the wubi-cdboot.exe file to do this.

When the PC starts, you are given 2 options.

Run Windows
Run Ubuntu

Selecting Run Ubuntu just runs it from the CD.

No partitions, mbr, etc are changed on your PC. You are running Ubuntu from the CD only.

Once you test drive Ubuntu running off the CD you can see if your sound, video, internet, printers, mouse, keyboard, display, etc etc etc works with that distribution and you have
no worries.

Look in the examples folder on the desktop. Here you find ogg files, office files, video files, etc. You double click on these to see if Ubuntu works with your video, audio, printer, etc, etc.

If you're happy, then you can install Ubuntu onto the HD if you wish.

Go to the CD and select Install.exe or Setup.exe on the CD iso image to now install Ubuntu.

You then are still given the option at start up to select Windows or Ubuntu.

That's a great idea.

---

### Post by ago on 2008-02-10
> **ex-navy said:**
> 
As I understand it, the iso image I downloaded can be run  from the CD without changing anything on my PC. More like a "test drive" without changing the PC. Just double click the wubi-cdboot.exe file to do this.
You only need CDBoot if your bios boots from HD first. In most cases you can simply reboot leaving the CD in the tray. In which case you do not have the dualboot menu, the dualboot is only shown if your machine cannot boot off CD and hence you have to use wubi-cdboot.

> If you're happy, then you can install Ubuntu onto the HD if you wish.
If you are happy then click the install icon within the demo itself


> You then are still given the option at start up to select Windows or Ubuntu.
correct

---

