---
title: "Boot Error Mount all: event failed Ntsf Volume is already exclusively opened."
date: 2012-11-22
forum: General Help
---

### Post by GalloGlas on 2012-11-22
Don't really know why all this started.  I've been using a wubi installed 12.10 for a few days.  Got rid of that garbage unity desktop and am back to my gnome classic desktop that I remember from 10.04. Got rid of ugly lightdm login in favor of the gdm one.  Other than that I haven't dug around in the system too much.  Multiple boots, restarts, etc. Just regular use with web browsing.   Then overnight couldn't boot past grub.  Got a blinking cursor followed by black screen.  

At first I thought it was the nvidia black screen boot error as I had nvidia issues that I've since solved (dern headers why u no stay installed?). None of the nvidia black screen on boot solutions worked. (nomodset)

After telling the system to resume normal boot from recovery mode it'll give the cursor and sit for 1-2 min before finally giving me an error.  Mount all:event failed.  Mount is denied because the ntsf volume is already exclusively opened.  Finally, at the end of the paragraph it says an error occurred while mounting media/system reserved.   

Now if i tell it to skip mounting ubuntu will load and everything appears fine and dandy.   

Is there a way to tell it to stop trying to mount this volume so I don't have do all these extra steps each time?

---

### Post by dcstar on 2012-11-22
> **GalloGlas said:**
> 
.........
After telling the system to resume normal boot from recovery mode it'll give the cursor and sit for 1-2 min before finally giving me an error.  Mount all:event failed.  Mount is denied because the ntsf volume is already exclusively opened.  Finally, at the end of the paragraph it says an error occurred while mounting media/system reserved.   

Now if i tell it to skip mounting ubuntu will load and everything appears fine and dandy.   

Is there a way to tell it to stop trying to mount this volume so I don't have do all these extra steps each time?

Remove it from your /etc/fstab file, it is probably a Hibernated/Suspended Windows boot partition.

---

### Post by GalloGlas on 2012-11-23
> **dcstar said:**
> Remove it from your /etc/fstab file, it is probably a Hibernated/Suspended Windows boot partition.


Sweet.  Fixed.   Thanks a bunch.

---

