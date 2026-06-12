---
title: "Power failure frustration"
date: 2007-08-19
forum: General Help
---

### Post by dvfreelancer on 2007-08-19
Okay, I know what a UPS is and should have one :mad: ...now that's out of the way.  

I'm running Kubuntu 7.04 (Feisty Fawn) and everything was peaches and cream until a power failure last night.  When the power came back on this box wouldn't boot until it ran through a disk repair that came up automatically.  The disk utility got it running again but there's a lot not working.

When I try to login to adept updater I get this error message:
> 
The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem

I tried to sudo apt-setup (not found) and apt-get update in a console window but get this error:

>  Could not open lock file /var/lib/apt/lists/lock - open (2 No such file or directory)


Network manager is not working.  If I go into the system settings app and try the system administration tools I get errors when trying to access Disk & Filesystems and the System Serivces tab.  

The system will no longer shut down normally.  It hangs on a message about shutting down HP image and printer something or other.

I can boot into protected mode but don't know what to do when I get there.  fsck throws a scary error about running a forced check on a mounted drive will cause kittens to die.  Okay, that's not what the error says but it's pretty scary.  

I've pretty much resigned myself to backing up my desktop folders and reinstalling.  But before I wipe out weeks worth of customization and tweaking I wanted to check to see if there was anything obvious I'm overlooking?  Any disk utilities I can try or recovery options I'm not seeing.  

I will never take electricity for granted again.  Also want to learn how to re-image my drive in the event something like this ever happens again.

---

### Post by Happy_Man on 2007-08-19
Indeed. I sympathize with your sad tale, and recommend you keep regular backups with a cron job to an external every few days. And also, go get a UPS. Those things rule. 

Have fun reinstalling, and you do know you can backup all your settings folders and restore them so that it was like nothing ever happened, right? All those hidden folders are actually where the settings are. Back them up too, and the world will be OK. Also, consider putting in a /home partition when you reinstall. Such usefulness..... 

OK. Enough with the advice from me.

/Happy_Man

---

