---
title: "Open Remote Files 8.04"
date: 2008-06-07
forum: General Help
---

### Post by allinurl on 2008-06-07
Hello, I was trying to open remote files on Hardy, if I open nautilus and then I type _[ftp://user@myserver.com/](ftp://user@myserver.com/)_ and click enter then I got a window asking for the password and then I can connect, BUT if I do it for instance on gedit, click open, then I type the same ftp url, I got _Could not find the file /home/user/ftp:/myserver.com._. Does anyone knows why this is happening?

---

### Post by RealPSL on 2008-06-07
Nautilus knows how to act as an ftp client.GEdit as far as I know expects the file to be accessible locally or via a network share but not ftp or http.

---

### Post by allinurl on 2008-06-07
but actually is not just on Gedit, also under bluefish is not possible, on 7.10 I was able to do it, Im not quite sure if gnome-vfs is the problem. what u guys think?

---

### Post by tramir on 2008-06-07
In GEdit you can go to File - Open location and then type the remote path and the file name. It's not as easy as browsing to the file, but it works. I couldn't get the file open dialog to display remote file systems yet (maybe using fuse could work? but that's a whole other thing).

---

