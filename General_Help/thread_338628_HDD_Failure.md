---
title: "HDD Failure?"
date: 2007-01-14
forum: General Help
---

### Post by Kerry Lange on 2007-01-14
I've had HDD crashes while using Windows and today I think I've got my first with Linux.  That's a problem for me because I'm completely lost when it comes to Linux, since I've been running Ubuntu for about three months on and off.

Anyway, the first sign was when the X Windows system didn't boot and I got a screen full of info telling me what went wrong.  It was no help to me though since I don't have a clue.

So, I booted to Windows thinking I might be able to grab a utility to view the files I needed from the Linux drive.  I downloaded the utility and installed in my Windows installation.  

Of course, it didn't do anything for me except slow down my Windows install.  I ran a diagnostic that accompanies the utility and it tells me that there is a problem with the drive.  It said the system may not have been closed down properly.  So, my Windows install is now stuck in permanent slow mode while it tries to read that FUBARed drive.  What's more is I can't uninstall the utility because I can't get a list of all the applications installed now that I've got this problem reading the Linux drive.

So, I tried booting to Linux again to see if I can recover the disk using fsck.  When I booted this time, I found that even the shell isn't available to me.  I get that busybox command prompt.

Does anyone know of a good utility I can use to try recovering the Linux drive and / or files?  I'd like to find out what's up with the drive.

---

### Post by Nate53085 on 2007-01-14
what I would do is pop in a live cd and boot of that.

Then run fsck on the unmounted filesystem to make sure its not a filesystem issue.

Also, there are MANY utilities to test whether or not your drive is dying.  They are sometimes specific to your hard drive manufacturer.  Check the website of the manufacturer for specific utilities.

---

### Post by Kerry Lange on 2007-01-15
Hah, I've got the live CD running right now but I can't figure out how to run fsck on the drive since the live CD doesn't mount the hardware I'm trying to access.

So, I know I need to mount the drive but don't know how to do that.  I've had a look at the manual but I can't seem to find how to reference the unmounted hardware.

Can anyone tell me how to do this?

BTW, I found a Windows utility that allowed me to get the data I needed from the crapped out drive.  However, another utility I got says there's nothing wrong with the drive.

---

### Post by futz on 2007-01-15
> **Kerry Lange said:**
> Hah, I've got the live CD running right now but I can't figure out how to run fsck on the drive since the live CD doesn't mount the hardware I'm trying to access.

So, I know I need to mount the drive but don't know how to do that.  I've had a look at the manual but I can't seem to find how to reference the unmounted hardware.
You can't fsck a mounted drive anyway. Just start a terminal and type 'info fsck' (without the apostrophes) for some help/hints.

Or read futz's handy fsck guide right here :mrgreen: If you just use fsck with no filesystem specified, it will check all filesystems listed in your /etc/fstab file.

Some various fsck example commands:
sudo fsck /dev/sda2
sudo fsck /media/sda2

---

### Post by Kerry Lange on 2007-01-15
Well, fstab has only the live CD relevant drives.  Running the live CD doesn't mount any of the HDDs present on the system, at least that I could see.

I tried running sudo fsck /dev/sdb2 to check the Linux drive but I get the following error:

fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb2
Could this be a zero-length partition?

I know that's the drive I need to check / repair and I know there's data on it since I was able to retrieve some from Windows. 

Any suggestions?

---

### Post by Wordcrasher on 2007-01-15
I'm not sure, but maybe with dmesg you can see wich devices are connected.

---

