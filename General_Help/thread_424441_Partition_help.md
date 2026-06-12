---
title: "Partition help"
date: 2007-04-26
forum: General Help
---

### Post by panzer77 on 2007-04-26
I have a clean install of 6.1 on hda1 with a swap on the same drive.  Everything with this drive is working fine.  During the install I also set up a second hard drive hdc1 with a mount of /ServerShare/.  This second hard drive is not detected or visable when I go to Places>computer.  I'm just looking for a way to set up this second drive with a share folder but have been unsuccessful.  If someone could point me in the right direction that would be great.

Thanks

---

### Post by Zuph on 2007-04-26
Does it hdc1 show up in your /dev directory?  Is /serverShare/ in your /etc/fstab file?  If so, try and create the directory /serverShare/ in your root directory, then reboot.

---

