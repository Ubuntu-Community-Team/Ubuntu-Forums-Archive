---
title: "Guest account suddenly owns the backup drive 12.04"
date: 2014-04-08
forum: General Help
---

### Post by Withanie on 2014-04-08
Today, I logged in using the guest account, just to see what it could see. Was surprised that it had so much access to the hard drives and folders.
So, I logged in with my usual account and discovered that all of a sudden, I don't have access to anything other than the main hard drive. The backup drive, named Photos, now belongs to guest.  

I've tried running a sudo chown on /media/Photos.  No errors, but no success either.  How do I get ownership back and how could this possibly have happened?

---

### Post by mcduck on 2014-04-08
What filesystem does the drive use, and is it internal drive or portable one? If it's an internal one, is it configured to mount through /etc/fstab, or mounted using the automatic mounting (like with USB drives etc for example)?

Window filesystems like FAT and NTFS don't support ownerships and permissions Linux and Unix systems use, which would explain chown not having any effect. And if the drive is automounted, it's then mounted with the ownership&permissions set at mount time for the whole filesystem, using the user that connected the drive. So plugging in a FAT-formatted removable drive as guest would make the drive appear as being owned by guest, until you unmount the drive and connect it again as some other user.

---

### Post by Withanie on 2014-04-08
You nailed it. The drive was FAT before I threw a snit at Windows and became an Ubuntu user. And, it is auto-mounted.  Interested to learn that a simple re-boot didn't change anything, I had to do a full shut down and restart in order to remount the drive.
 I do believe that it's time to buy a reference manual and learn more about these details.

Much obliged.

---

