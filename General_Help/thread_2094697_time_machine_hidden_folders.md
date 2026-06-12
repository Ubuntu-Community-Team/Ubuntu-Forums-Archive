---
title: "time machine hidden folders"
date: 2012-12-14
forum: General Help
---

### Post by bigloftus on 2012-12-14
Hello,

I have taken a time machine backup, imaged it and have mounted it in Ubuntu. Several of the folders are hidden from view unless I use ls -a or a similar command. Is there any way that I can access these hidden directories as I need to get to the further directories inside. Note that the image is mounted as read-only.

---

### Post by Habitual on 2012-12-14
Since you are talking about files as "folders" this leads me to conclude you are asking for a graphical filter to show all files, yes?

Ctrl+H in most file managers.

---

### Post by bigloftus on 2012-12-14
I may have used the incorrect phrase, I meant directory not folder. I'm looking for a command to use in the terminal that will allow me to enter a directory that I cannot see.  Currently all I see is a Backups.backupdb directory and not the .HFS+ Private Directory data directory. I hope this helps you understand more.

---

### Post by Impavidus on 2012-12-14
Hidden files in a terminal: view/list: ls -a, enter: cd .dirname
Last time I checked cd didn't care whether directories where hidden or not, just don't forget the dot, which is part of the directory name.

---

### Post by iMac71 on 2012-12-15
there are some useful tools for managing HFS+ volumes; you can install those tools as follows:
```
sudo apt-get hfsplus
```

---

