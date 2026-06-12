---
title: "Help! desktop not working"
date: 2007-02-17
forum: General Help
---

### Post by ll88 on 2007-02-17
I have been using xubuntu for a half year now almost with no problems. Today however, i was just normally using my computer without doing anything extraordinary and suddenly my desktop icons dissapeared and i couldnt use right mouse button either (panels however were working) so I opened process manager and noticed that xfdesktop wasn't running but when i try to run it on terminal it gives me this:

(xfdesktop:4415): thunar-vfs-CRITICAL **: thunar_vfs_mime_database_get_info_for_name: assertion `*name != '\0'' failed
Segmentation fault (core dumped)

So how can I get my desktop running again? I have tried reinstalling xubuntu-desktop and also tried check "allow xfce to manage desktop" and save session but didin't work... Can anypody help me?

---

### Post by bettlebrox on 2007-02-17
Rename your .xfce4 directory and see if that fixes it.

---

### Post by ll88 on 2007-02-17
Didn't help but thanks anyway.

---

### Post by bettlebrox on 2007-02-17
Login to the console and make sure there are no xfce programs running and try again. Next I'd create a new user and see if Xfce works for them, and least that will let you know if it's a problem with your account or if the Xfce packages have gotten corrupted. If Xfce doesn't work for the new user then I'd suggest purging all the Xfce packages and reinstalling them.

---

### Post by ll88 on 2007-02-17
I added a new user and now it works! :)   How can I now transfer the contents of my previous user folder to the new one?

---

### Post by bettlebrox on 2007-02-20
I don't use Xfce myself, but I'd guess you'd copy over the Xfce settings files, which are probably in .xfce or .xfce4. Make a copy of your originals first.

---

