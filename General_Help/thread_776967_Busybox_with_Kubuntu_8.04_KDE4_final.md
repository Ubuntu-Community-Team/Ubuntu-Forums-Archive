---
title: "Busybox with Kubuntu 8.04 KDE4 final"
date: 2008-05-01
forum: General Help
---

### Post by a2h on 2008-05-01
I finished downloading Kubuntu 8.04 KDE4 Remix yesterday, installed Wubi, and everything was fine. Today, I decided to start up Kubuntu, ending up greeting "Busybox" just after the Kubuntu loading screen flashes.

Any help?

---

### Post by Aearenda on 2008-05-01
This often means it can't find the root partition - any hardware changes overnight :-)?

This occurs before entry to KDE, so all ubuntu/xubuntu threads are relevant too. 

It it a Dell 530 by any chance? If so, try all_generic_ide as a boot-time parameter for the kernel, in Grub. [http://ubuntuforums.org/showthread.php?t=762257](http://ubuntuforums.org/showthread.php?t=762257) has the details.

Searching for 'busybox' in the forums might help as there are several other threads that sound similar, such as [http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195).

---

### Post by a2h on 2008-05-01
No hardware changes overnight, the computer was off =P

I've scheduled a chkdsk /r for the next reboot though.

The computer is an HP, so your Dell note doesn't apply of course...

---

### Post by ago on 2008-05-01
See if chkdsk /r fixes it. you might want to boot in debug mode (add debug=y as boot parameter) if it does not. Logs are in /tmp and /var/log/syslog

---

### Post by a2h on 2008-05-01
> **ago said:**
> See if chkdsk /r fixes it. you might want to boot in debug mode (add debug=y as boot parameter) if it does not. Logs are in /tmp and /var/log/syslog

> **a2h said:**
> I've scheduled a chkdsk /r for the next reboot though.

=/

Well, I might as well add that cmd was too stubborn to want to run chkdsk saying another process has locked the drive or something to do with locking...

---

### Post by a2h on 2008-05-02
Weird, I didn't see whether autochk or whatever it was called scanned.

Anyway, I tried chkdsk /r again and here's the message:
```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\*****>chkdsk /r
The type of the file system is NTFS.
Cannot lock current drive.

Chkdsk cannot run because the volume is in use by another
process.  Would you like to schedule this volume to be
checked the next time the system restarts? (Y/N) n
```

Also, please note that I'm not very experienced with the Linux terminal.

Give me something to do that cannot be done with a GUI without helping me and I will most likely run screaming.

---

### Post by ago on 2008-05-02
Select yes and reboot windows, then chkdsk should run. Then try again to boot into Ubuntu.

---

### Post by a2h on 2008-05-02
> **ago said:**
> Select yes and reboot windows, then chkdsk should run. Then try again to boot into Ubuntu.

I did that. chkdsk didn't run. Spybot did report the startup entry being changed to /* instead of C:\ /r or something...

---

### Post by ago on 2008-05-02
In this case use a Windows CD. You can run chkdsk /r from the recovery console in there

---

### Post by a2h on 2008-05-02
I don't have a Windows CD; I have an OEM installation.

Oh and I did a defragment; the Wubi disk file was the only thing that could not be defragmented.

---

### Post by a2h on 2008-05-03
This... is... weird.

I got chkdsk to work yesterday, but after restarting when chkdsk finished, I got greeted by Busybox, yet today, Kubuntu worked fine without any problems. O_o

---

### Post by Danish989 on 2008-05-04
I'm having the same BusyBox problem and have no idea at all what to do :S Started having it after 2 complete days of having fun in Ubuntu ......

---

### Post by dreamsayer on 2008-05-06
> **Danish989 said:**
> I'm having the same BusyBox problem and have no idea at all what to do :S Started having it after 2 complete days of having fun in Ubuntu ......

Same here, but with Ubuntu. Had 3 days of no problems, then today when I started, got the BusyBox error. Thank god the web files I was working on was backed up to a flash drive. 

The only thing that my system did was last night I started with Vista. OneCare did a tune-up. Later shut down machine. This morning when I turned on my computer, decided to boot into Ubuntu. BusyBox error.   

It is reasons like this why I will NEVER trust any Linux OS whether it be Ubuntu or any other ever be my primary OS. Because everything runs hunky dory, then one day it doesn't boot! I have come across this more times than I can remember! IMO, Linux is just a bucket of bolts toy OS!

---

### Post by ago on 2008-05-06
Well in fact odds are 9 to 1 that the reason it does not work is because your Windows filesystem is corrupted and/or was not shutdown cleanly. Since Wubi sits on top of the windows filesystem that is of course an issue. Anyway if you run chkdsk /r from within windows and make sure you reboot properly, things should work again in most cases.

---

### Post by dreamsayer on 2008-05-07
> **ago said:**
> Well in fact odds are 9 to 1 that the reason it does not work is because your Windows filesystem is corrupted and/or was not shutdown cleanly. Since Wubi sits on top of the windows filesystem that is of course an issue. Anyway if you run chkdsk /r from within windows and make sure you reboot properly, things should work again in most cases.

When I got home today and turned on my computer and selected Ubuntu, low and behold in booted up! No BusyBox error.

So I rebooted from Ubuntu into Vista and did a chkdsk /r. But before I did that, I did a search for Ubuntu in case I had to do a re-install to find the iso. Come to find out, wubi had downloaded the amd-64 version. My system is 64 bit, but I have Vista 32 bit installed. 

After chkdsk ran, which took a really really long time btw, almost 2 hours, no errors found. I have done this check before in the past, and it has been quick. So I'm a bit surprised why it took so long.

Another error which I was going to report separately, is when I boot Ubuntu, I receive an error message 81 unrecognized partition table for device 81, run a a msft compatible fdisk program on the disk. However Ubuntu still loads.

So I wonder if this has to do with a 64 bit Ubuntu, rebooted back to a 32 bit Vista and vice versa?

---

### Post by ago on 2008-05-07
> **dreamsayer said:**
> When I got home today and turned on my computer and selected Ubuntu, low and behold in booted up! No BusyBox error.
Then it was most likely because of a premature shutdown, so that the ntfs partition is flagged as dirty and Linux refuses to mount that for obvious reasons (I know the error message in such case is absent and/or confusing, there will be a clear error message in coming versions).

> Come to find out, wubi had downloaded the amd-64 version.
This is expected

> After chkdsk ran, which took a really really long time btw, almost 2 hours, no errors found. I have done this check before in the past, and it has been quick. So I'm a bit surprised why it took so long.
As mentioned if you shutdown windows prematurely or uncleanly, even if there is no fs corruption per se', ntfs gets flagged as "dirty". To fix that you have to boot into windows and shutdown cleanly. We could ignore the "dirty" flag of course, but it would not be wise to do so.

---

### Post by dreamsayer on 2008-05-07
> **ago said:**
> Then it was most likely because of a premature shutdown, so that the ntfs partition is flagged as dirty and Linux refuses to mount that for obvious reasons (I know the error message in such case is absent and/or confusing, there will be a clear error message in coming versions).

Hmm, your answer seems to explain why this "might" be happening, but I always shutdown my machine properly. I've never had Vista balk at me or do a check disk on startup because of an invalid or improper shutdown. And given all the other folks who are having similar troubles, I suspect it's something more...

Also, what is this error 81 I'm receiving about the partition before booting Ubuntu? You skipped over that without a comment. This seems like a critical error message even though it still boots.

Thanks for the help! :KS

---

### Post by ago on 2008-05-07
It means that for 1 drive it cannot understand the partition table, but shouldn't matter if it is not a drive where you have wubi and windows is happy with it :)

Anyway you can check the dirty flag theory by running ntfs-3g.probe (or simply trying to mount manually) when you are thrown into the busybox.

See also: [https://bugs.launchpad.net/wubi/+bug/226622](https://bugs.launchpad.net/wubi/+bug/226622)

---

