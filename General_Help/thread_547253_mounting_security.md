---
title: "mounting security"
date: 2007-09-09
forum: General Help
---

### Post by AdotB on 2007-09-09
I am curious if there are any actual security issues involving mounting for home computer users (non-server).  
I was thinking about how macs use .dmg disk images. I don't have a mac, so i don't fully understand how they operate, but i like the idea of being able to open, browse, and use files in an image without having to extract anything like tar archives, or entering passwords. In other words, using disk images as easily as usb flash drives. Kind of like a portable folder.
I have considered adding “<user> ALL=NOPASSWD:mount”  to my sudoers file, or maybe a script that restricts the use of mount to a specific usage. 

If there is in fact a security issue, or if this is just ridicules to consider, or if theres another way to achieve similar results (like just using tar, perhaps), please let me know.

---

### Post by p_quarles on 2007-09-09
It would make more sense to add the drive to your /etc/fstab file. You can configure it to automatically mount a drive, or to be user-mountable (look at the lines for the CD drive to see how this works).

---

