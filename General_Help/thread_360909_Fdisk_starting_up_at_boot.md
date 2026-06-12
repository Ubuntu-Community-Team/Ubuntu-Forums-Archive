---
title: "Fdisk starting up at boot?"
date: 2007-02-13
forum: General Help
---

### Post by ctsdownloads on 2007-02-13
Something strange has happened after a few updates ago. For whatever reason, I am seeing fdisk starting up during a boot before displaying my list of OS' in GRUB. Tons of text during the scan, sentences like "file system not clean" and more stuff than I can remember happening. Why would fdisk be doing this? Is it simply GRUB falling on its face again? Any help would be appreciated.

Running Edgy fully patched/updated. Thanks.

---

### Post by louieb on 2007-02-13
Wow that makes no sense. fdisk is a program that partitions a drive. There is a DOS/Windows version and a Linux version. Neither have anything to do with checking the file system.  After you select your Linux OS in GRUB the program  fsck is run to check the file system, it is similar functionally to windows scandisk.

You say you are seeing these messages before the GRUB menu is displayed.
Is the Grub menu getting displayed? 
If it were mine I think I would  Reinstall GRUB (see link in signature) or try the Super Grub Disk.
Question Have you been logging on as root and playing around?

---

### Post by ctsdownloads on 2007-02-13
That is exactly what I was thinking as you are spot on, why would I be seeing something to do with fdisk (Linux)? It has me blown away and I suspect it may be GRUB related as it happens after GRUB is displayed. Yeah, it looks like I may need to utilize the Super Grub disk. I have kept it downloaded for sometime now, just for such an emergency.

---

### Post by ctsdownloads on 2007-02-13
OK, I was on crack, it was never Fdisk. It was [file system consistency check]("http://en.wikipedia.org/wiki/Fsck")

Here is what I am seeing **after** choosing Ubuntu from GRUB:

[IMG]http://www.computertroubleshoot.com/images/screen3.JPG[/IMG]

then


[IMG]http://www.computertroubleshoot.com/images/screen1.JPG[/IMG]

and then 


[IMG]http://www.computertroubleshoot.com/images/screen2.JPG[/IMG]

What could be the problem? After this, it's back to the blinking cursor and then finally, my login screen.

---

### Post by ctsdownloads on 2007-02-13
bump

---

### Post by dcstar on 2007-02-13
> **ctsdownloads said:**
> bump

The problem is what the screen says: The Filesystem is not clean.

You have to run fsck on the relevant filesystems to fix them, if you want them automatically fixed at boot time, then in a terminal:
```
gedit /etc/default/rcS
```
and change the FSCKFIX line to "YES"

---

### Post by ctsdownloads on 2007-02-13
Perfect, I am trying this now.

Will report back, thanks.

---

### Post by ctsdownloads on 2007-02-13
OK, so after running this, the file system is now being reported as "clean". 

Great, I am able to login and all of that, just like before. Login was never the issue though. It was the wasted time watching all of this (see screen shots) go by just to make this happen that was the issue. Taking forever, etc.

Unfortunately, I am *still* dealing with the same issue as before. I am still being presented with FSCKFIX rather than a speedy boot like usual.

Back to the same old sloooooow text display. So, I am assuming that it is time for a reinstall as the corrective measures are apparently non-applicable? Could this be related to something else? ](*,)

[IMG]http://www.computertroubleshoot.com/images/latest1.JPG[/IMG]

[IMG]http://www.computertroubleshoot.com/images/latest2.JPG[/IMG]

---

### Post by ctsdownloads on 2007-02-14
Any ideas how to stop this FSCKFIX display? Unless something changed within Edgy, I have never needed it to come up with every single boot. Thanks

---

### Post by dcstar on 2007-02-14
> **ctsdownloads said:**
> Any ideas how to stop this FSCKFIX display? Unless something changed within Edgy, I have never needed it to come up with every single boot. Thanks

It **only** appears if there is a problem with one of your filesystems.

If there is something that is corrupting your filesystems then you need to fix that, not worry about the thing that is informing you of the problem and trying to repair the damage.

If fsck is saying that your root filesystem needs repair, then you must do that manually by booting off another device (like the Ubuntu Live CD) - the auto repair can only work on unmounted filesystems (and the root filesystem is mounted as it boots up).

---

### Post by ctsdownloads on 2007-02-14
Ah, there's the rub. You bring up a good point that I did not consider. So even though the system is being reported as "clean", this is apparently false then?

Alright, any thoughts on tracking down the culprit? No new software has been installed since the error, so the only thing I can think of is an upgrade to Beryl or another part of the OS that went wrong?

Thanks

---

### Post by louieb on 2007-02-14
> **ctsdownloads said:**
> OK, I was on crack, it was never Fdisk. It was [file system consistency check]("http://en.wikipedia.org/wiki/Fsck")

Ok, that makes sense.
That happened to me once to my /home partition and running fsck did not fix it. What I did to fix it was:
Backup the partition to an external USB drive. (How to section of forum has a couple of good threads on Backup and Restore)
Reformatted the partition.
Restored from backup.

In my case I don't know if its something Linux did or if its the fact that 10 year old drive the partition is on is starting to go bad. Bur its been a couple of months since that happened and haven't had any trouble since then.

---

