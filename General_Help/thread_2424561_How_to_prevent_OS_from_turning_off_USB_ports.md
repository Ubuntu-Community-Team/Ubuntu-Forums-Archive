---
title: "How to prevent OS from turning off USB ports"
date: 2019-08-10
forum: General Help
---

### Post by peyre on 2019-08-10
I back up our files to external hard drive.  I have an .sh script on my desktop computer, and a batch file on the wife's Win10 machine.  They back up our important files, move the previous backup to the Old folders, and delete the backup before that, so I keep a running backup of all our files.  Then every few months I bring the HD into the office and bring home the one I was keeping there, to maintain an offsite backup.

One of our drives died recently so I took the opportunity to replace it with a portable drive instead.  It's much more convenient, but the trouble is, Xubuntu turns it off after a while if my computer's not active, so I can't start one of the scripts when I go to bed and find it done in the morning.  It literally takes about 3 days to complete on my system, where it took only about 6 hours before.

So, how do I prevent Xubuntu from turning off the USB ports?  Or a specific port, if that's easier?  In Power settings I've set my computer to Never suspend or lock the session.

---

### Post by haplorrhine on 2019-08-10
Here it goes.  I'm on WIndows.  :popcorn:
I know desktop environments are stored in usr/share/xsessions.  If you create a custom desktop environment, like the Gnome or KDE Unity environments, that only runs the terminal application, your system will never suspend.  Moreover, it should be approx 5% more efficient than an awake (and therefore bogged down) Unity environment.  If you MUST do something else simultaneously, launching it from the terminal might or might not be so straightforward.  Therefore I recommend a faster port like USB 3.0 or Firewire (or whatever superseded them within the last 4 years).

Otherwise, I am puzzled about what handles sleep mode.  I incorrectly guessed crontab.  In sleep mode, battery power consumption is nearly as low as the terminal-only session.
[this page lists desktop environments]("https://wiki.archlinux.org/index.php/Desktop_environment"), but Suspending and hibernating appear to be controlled by [systemd (ArchLinux link)]("https://wiki.archlinux.org/index.php/Systemd").  Suspension and hibernation seem to be *[power management (AL]("https://wiki.archlinux.org/index.php/Systemd#Power_management"))* features related to the *display manager.*  The section [systemd/mounting (AL)]("https://wiki.archlinux.org/index.php/Systemd#Mounting") mentions the partition's *TYPE GUID* in relation to its automounting.
Although it doesn't discuss the suspension and hibernation states in a broader scope that includes they're configurations, it does seem to discuss how the partitions are recognized for automounting, or, potentially, auto-unmounting.  Good luck.

---

### Post by peyre on 2019-08-11
Thanks haplorrhine.

---

### Post by TheFu on 2019-08-11
3 days for a backup?!!!!  You need a better method. 

I switched away from a backup method when it was taking 90 minutes per machine.  Now each machine usually needs 2-6 minutes and 1 needs 20-30 minutes because of the amount of data and the number of files.

Backing up 16TB takes about 8 minutes now, thanks to rsync. I haven't needed to do a "full" rsync in years.

I hope you'll find a better method.

Many portable HDDs support an external power adaptor. Use one if it is supported. I use an external "dock" which let's me swap HDDs into the available slots. No external enclosure, just the HDD.  

Any portable storage device, especially one with backups on it, needs to be strongly encrypted. Hope you have that covered with LUKS or even veracrypt.

---

### Post by peyre on 2019-08-13
No, this doesn't have an external power supply (or I'd have used it already).  The method I've used til now works well for us, though it is slow.  The trouble is that I have to back up both a Linux and a Windows machine, so I use scripts that copy the files.  Plus with a straight copy job I can just copy files back off it from anywhere.  When we travel I bring the backup drive and then can access files onto my laptop directly from the drive.  And, at the office I occasionally want a file from home, and can usually just pull it off the backup drive I keep there.  Overall it's been an ideal solution for us.

Most of our data really doesn't need to be encrypted, but anything sensitive (such as our tax records) is wrapped up in TrueCrypt files.

---

