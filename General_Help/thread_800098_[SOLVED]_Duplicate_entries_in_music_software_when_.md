---
title: "[SOLVED] Duplicate entries in music software when accessing usb drive"
date: 2008-05-19
forum: General Help
---

### Post by Budoc on 2008-05-19
Hi,

Apologies if I've posted this in the incorrect area. I wasn't sure whether this post would be best suited to the General, Hardware, or Multimedia support areas.

I own a Western Digital 160 GB Passport Essential, which I have formatted to NTFS with gparted to enable me to have a portable music collection that I can access from my Ubuntu laptop and others Windows computers. I have noticed that with several music programs such as Rhythmbox and Exaile when I set the library to a folder on my Passport, I get two entries for each mp3 I have. I have verified that this isn't due to mp3s located elsewhere as I have deleted the library database and reloaded the library and still had the same problem. Rhythmbox tells me that the location of each duplicate pair of mp3s is identical, and both pairs of mp3s play fine. I get the same problem if the drive is connected to my externally powered usb hub or directly to a usb port on my laptop. I have tried using Rhythmbox with another NTFS-formatted drive (a Lacie 120GB 3.5" usb drive) and this problem does not occur. 

Any ideas on how I can begin to work out what is going on? I've not had any previous problems with the Passport as I regularly use it to backup work without any issues. I've tried running Rhythmbox from the terminal, and the only error messages I get are concerned with some .rar files it finds in my Music directory. These same .rar files are on my other drives and I don't have the duplicate entry problem on these drives.

---

### Post by ajgreeny on 2008-05-19
I assume the external disk isn't mounted in two separate places on your ubuntu system, if that is even possible?  I suppose the two entries might show as different locations if that was so, though often the usb disk will simply show as "disk" in places, so locations might appear the same.

---

### Post by Budoc on 2008-05-19
> **ajgreeny said:**
> I assume the external disk isn't mounted in two separate places on your ubuntu system, if that is even possible?  I suppose the two entries might show as different locations if that was so, though often the usb disk will simply show as "disk" in places, so locations might appear the same.

The drive appears as /media/my_passport and corresponds to /dev/sdc1 currently. Only one usb drive logo is added on the desktop and on the disk mounter applet on my panel when I mount the drive. I renamed the Passport from "disk" to "my_passport" using the ntfslabel program found in the ntfsprogs package, so there hopefully shouldn't be any confusion with any other drives that I may mount.

---

### Post by Budoc on 2008-05-23
I reformatted the drive using gparted to NTFS again, and the error does not occur any more. I'm assuming that I made an error when copying the files to the drive the first time.

---

