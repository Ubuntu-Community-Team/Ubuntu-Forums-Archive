---
title: "How do I add USB support to server version?"
date: 2007-03-11
forum: General Help
---

### Post by macjones on 2007-03-11
Hi All,

I'm writing a custom system that needs to recognise USB devices (cameras and flash drives), and open Nautilis or Thunar.

I have started with a "Server" install of Dapper, and all the messages come up nicely in dmesg. But I want to add the packages that will make the drive appear in:

/media/USB DISK 

(they show up fine in a full install of dapper, but are not mounted in the server version). I'd also like to make a hook in the mount script so that I can automatically open the thunar file window for a user to browse their files (just as the full dapper does).

Thanks 
Mac
New Zealand.

---

### Post by yabbadabbadont on 2007-03-11
I think you will get that behavior if you install hal, dbus, and pmount.

---

### Post by macjones on 2007-03-11
Nope, same thing after apt-getting those..

ls /media
**cdrom cdrom0**

---

### Post by macjones on 2007-03-11
P.S USB Mouse support is working just fine, it's just automatically seeing file storage in /media that I can't get working.

---

