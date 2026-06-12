---
title: "Please Help with recovering/backing up files from faulty Windows laptop using Ubuntu"
date: 2016-01-30
forum: General Help
---

### Post by Golinas4980 on 2016-01-30
Hello. I am wondering if anyone might be able to help me with recovering/backing up a ton of files from my laptop. I am somewhat, but not terribly computer savvy, so please bear with me. I have a lot of important files on my laptop that I have no back-ups of, and my laptop decided to stop working today. Hard drive error 301, and it won't boot up. So I tried to use Ubuntu to recover the files on it, installed the latest Ubuntu version on a USB drive and went to "Try Ubuntu without installing" but I am lost as to how to find the Windows hard drive with my files on it. Tried following some other threads but it seems I cannot figure it out. If anyone would be willing to help walk me through it it would be greatly appreciated! Thank you!

---

### Post by dragonfly41 on 2016-01-31
Recovery workflow depends on what tools you have available.
Do you have another working Windows PC you can use?
You write that you have tried to use a LiveUSB (Ubuntu).
Was this created on another desktop?
Was it created with persistence flag set to allow apps/data to be retained in USB?

If you do bootup your LiveUSB  and "Try Ubuntu" I suggest that you adopt a "windows like" 
desktop layout so that you have less of a learning curve from your Windows environment.

Search for "install gnome-classic-desktop in Ubuntu 14-04"

Basically you need to install "gnome-session-fallback" package then reboot your LiveUSB.

Now when you login to Ubuntu you can switch to classic gnome layout so that Ubuntu desktop 
is reasonably similar to your familiar Windows desktop layout.

That is the desktop mode I am in now.

Now check if you have "testdisk" installed. 
Open command terminal with Ctrl+Alt+T and type "man testdisk".

If testdisk is not installed in the LiveUSB (I can't recall if it is installed by default) it can be installed 
but I would download the latest version and not the Ubuntu repo version (which is often an older version).


I have a dual boot Windows/Ubuntu and in Ubuntu I can view 
Windows files in NTFS partitions .. but only when the Windows partition is mounted.

...

If you read experiences of others trying to recover files from 
crashed Windows it is usual to use Windows apps to recover 
Windows files.   In my case I have used "Recover My Files" from [http://www.getdata.com/](http://www.getdata.com/)

Now this requires Recover My Files to be installed on a working Windows desktop.
This usually requires your failed hard drive to be 
(a) physically removed
(b) placed in a hard drive USB container purchased from a PC store (check compatibility before buying)
(c) connected to a working Windows PC as external USB drive.

You can test if you can recover files (evaluation mode) *before you need to purchase a licence* for Recover My Files. 
That is the sting.  Usually you need to pay for Windows file recovery apps.


[postscript]
Be aware that when recovering files you need space to actually *save* the recovered files. 
Whether you use test disk or Recover My Files for recovery you will be asked at the end of a long recovery process 
*where *the recovered files should be saved.  It can be annoying if you don't have space after waiting some time in recovering.
Since you appear not to have a backup drive perhaps this is the time to invest in purchasing one for recovery/backup.

I would also test the integrity of the failed drive which might need replacing.

---

