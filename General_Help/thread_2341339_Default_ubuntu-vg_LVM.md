---
title: "Default ubuntu-vg LVM"
date: 2016-10-27
forum: General Help
---

### Post by thorep on 2016-10-27
Hi! I have just set up my first ubuntu server (desktop version with gui) and have sucsesfully created a LVM volume on my second harddrive.
BUT on my 1st harddrive ( a 128gb) drive there is alot of free space. It is located in the ubuntu-vg group.

How can i "move" this space over to my vg-media group and volume?

---

### Post by TheFu on 2016-10-27
[https://linux.die.net/man/8/vgmerge](https://linux.die.net/man/8/vgmerge) if you can't wait ... 

Posting the output from the typical LVM commands is needed to get more specific help. lsv, vgs, pvs, and the *display things.  Plus **df -h** would be nice. **Code tags** are appreciated so things line up.

---

