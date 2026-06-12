---
title: "External USB RAID Box Not Showing Up"
date: 2007-07-31
forum: General Help
---

### Post by wcj786 on 2007-07-31
Sorry if this is a repost, but I could not find the info in my search.  I have a external RAID box made up of aa AMS Venus T4U and 4x500GB hard drives.  These can connect to a computer vis USB.

Under Windows, I could see these as RAID 0 (the external case has dip switches to make RAID 0 or JBOB).  Under Feisty, I can't see the drives at all.  I have a lot of data on them (approx. 2 GB of movies) and want to be able to use them in a Linux HTPC.  (Currently, I only have my laptop set up with Feisty.)

My real question is how do I get my laptop to recognise the drives (preferrably as RAID 0 without having to re-load all of the movies).  I would like to be able to leave the drives set up as NTFS, because I sometimes take this RAID box with me to relatives who have Windows HTPCs.

Any help would be greatly appreciated.

---

### Post by AlexThomson_NZ on 2007-07-31
Can you confirm you can see other USB disks when they are plugged in (USB keys, iPod, etc.)?

These are mounted under /media by default, if they don't automatically appear on the desktop

---

### Post by wcj786 on 2007-07-31
Thanks to your hint, I figured out what the problem was and was able to get my drive set up, but now, the problem is trying to have it automatically mount every time I turn the computer or the external hard drive on.

I found that the drive was not automatically mounting, then figured out how to mount it with:

sudo mount -t ntfs-3g /dev/sdb1 /media/RAID

I have also found directions as to how to build it in /etc/fstab, so that it will mount at start up (using either UUID, or directory mounting), but neither of these is currently working for me.  I have followed the directions to put this in /etc/fstab:

/dev/sdb1 /media/RAID ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1

but that did not work after logging out and restarting the computer, so I found out the command to get the UUID (which did not look like the UUID from the other devices) and, using the same command, input the UUID in place of the /dev/sdb1, with everything else staying in place.  That did not work either.  I am now looking for a way to make it always mount when I turn either the RAID device on, or the computer on.

---

### Post by AlexThomson_NZ on 2007-08-01
run "dmesg" after booting and that will show what errors occured when mounting your fstab

---

### Post by fjgaude on 2007-08-03
Your raid external device shows as sdb1?

/dev/sdb1 /media/RAID ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1

Shouldn't the command be:

/dev/sdb1 ntfs-3g /media/RAID defaults,locale=en_US.utf8  0  0

Hang with us and you will get it... just a matter of time and attention to detail.

frank

---

### Post by wcj786 on 2007-08-06
I was following a procedure that claimed to work when I added that line.  I have no idea what that line actually meant, but wanted to get it to auto-mount, so I tried it.  I have since removed it, since it did not work.

I have taken a break from trying to get it to auto-mount, as I am in the process of building a desktop and loading software (WinDOHs, due to using this for work).  I will be back trying to get it to work later.  (I am also adding a second HDD in the desktop in order to load Kubuntu.  I will switch the boot disk in BIOS when I want to boot up in Kubuntu.)

---

