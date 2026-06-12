---
title: "how to change a drive name"
date: 2008-04-25
forum: General Help
---

### Post by PsyWolf on 2008-04-25
I just wiped my main drive and installed hardy heron.  I chose the guided full disk partition instead of the manual, so my NTFS drive didn't mount automatically.  I added this line to my /etc/fstab to fix that.

# /dev/sda1
UUID=86F076BAF076AFD3 /media/windows ntfs-3g defaults,locale=en_GB.utf8 0 0

Now the drive mounts on startup, but it is named "82.3 GB Media" and i want it to be called "windows"

Could someone show me how to change it?

---

### Post by GlitchEXE on 2008-04-27
I was actually looking for this myself today since I like to have my NTFS drives nicely named.  I followed the information here [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive").  Even though the title says its for USB it works for internal drives as well.  It did the trick for me.

---

### Post by PsyWolf on 2008-04-27
thanks man.  that did the trick for me too.

If any developers notice this, this would be a really great thing to include in a more user friendly (read as GUI) version in ubuntu itself.  Namely, in the drive properties window, or possibly a whole andministrative disk management utility.

---

### Post by quixote on 2008-04-28
The drive name thing was driving me crazy.  *Crazy*  Don't even get me started.  (Note to Ubuntu devs:  never, ever, ever make it impossible for users to call their partitions whatever they need to call them!)

Okay.  Anyway.  Back on topic.  I found the rename page on the community help pages too.  Excellent explanation.  But the only option for vfat drives is TO RENAME EVERYTHING IN UPPERCASE.  I HATE UPPERCASE.  (You can see why.)

For God's sake -- or my sanity's sake -- solve this issue!  I don't care what the system has to call the partition.  Just make me able to put the name I need on the desktop icon and the mount directory!

---

