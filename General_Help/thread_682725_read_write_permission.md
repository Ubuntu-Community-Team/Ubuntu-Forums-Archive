---
title: "read write permission"
date: 2008-01-30
forum: General Help
---

### Post by Atlio42 on 2008-01-30
can anyone tell me how to set my secondary hardrive to read and write?
i was able to format the drive in gparted and everything but it wont allow me to write to it. i have no idea how to do this. :popcorn:

---

### Post by jclmusic on 2008-01-30
the CLI way: 
sudo chmod (insert permissions and mount point) - search the forums for chmod, i think it's x=execute, r=read, w=write.

the GUI way:
in gnome, open nautilus, navigate to the mount point, right click on the icon and click 'properties'. you can then change the permissions in that dialog.
in xfce replace nautilus with thunar, and in kde replace nautilus with konqueror or dolphin.

---

### Post by nick_h on 2008-01-30
What filesystem are you using on your secondary hardrive?

---

