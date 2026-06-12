---
title: "cd wont eject"
date: 2007-03-10
forum: General Help
---

### Post by absol_of_doom on 2007-03-10
i put a cd-rw in my drive and attempted to write to it, but apparently windows had screwed   
up the disk so it is read-only now... but when i tried to get it to eject, it wont. can i use a kill command or something to eject it?


thanks

---

### Post by jms1989 on 2007-03-10
You would first have to unmount the disk; umount /dev/hdc

Replace hdc with the correct drive device. This will then allow you to eject the disk.

Cheers,
jms1989

---

### Post by fragos on 2007-03-10
You can manualy remove a CD even when the power is off.  Somewhere under the tray you should find a small hole about 1/16th inch in diameter.  Take a paper clip and unfold it until you get an "L" shape.  Insert it in thye hole and push the release catch untill the tray pops out.

---

