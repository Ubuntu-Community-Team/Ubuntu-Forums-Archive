---
title: "Automount?"
date: 2008-02-22
forum: General Help
---

### Post by psychofish25 on 2008-02-22
Is there a way that I can automount to my other Harddrive on startup? I made a link to my music folder but I can't access it unless I mount my harddrive.

---

### Post by taurus on 2008-02-22
You can add an entry in /etc/fstab to have it mount automatically each time you boot.  Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by LuisGMarine on 2008-02-22
Yes you can.  You can add it to your fstab.  Fstab is what  controls your mounts during boot, you can find the file and edit it in /etc/fstab.

First thing first, you need to find out what /dev/ you hard drive is.  For example I have two HDD, one is /dev/sda and the second one is /dev/sdb.

you can read this tutorial to get yourself more familiar with fstab.  

[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")



However this post here is the one you are looking for.  If it is confusing post back and I'm sure more people can help you out including myself.  To me its straight foward, I guess it depends on your lvl of expertise. 

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

Good luck and let me know how it goes.

---

### Post by psychofish25 on 2008-02-22
Wow great answer and I barely had to wait. I love these forums so much. 

You can tell I'm new haha.

---

