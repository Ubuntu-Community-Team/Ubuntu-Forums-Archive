---
title: "How to replace new Home folder with saved Home folder..."
date: 2014-04-13
forum: General Help
---

### Post by sillyboy on 2014-04-13
I just installed 12.04 LTS (from a CD) on my wifes computer.  She had 10.04 LTS.  I want to take the Old Home folder I saved, and replace the New Home folder with it.  How is this done?
I also have installed Gnome Classic on her computer.
Thank You...  :D

---

### Post by yXmNpV8z on 2014-04-13
Copy and paste??

I think we need a bit more info. Have you just saved the files to disk/media device? Copied all the hidden files? What??

Gav.

---

### Post by sandyd on 2014-04-13
Moved to General Help

---

### Post by buzzingrobot on 2014-04-13
Assuming old home was simply left in place or just copied on the same drive:

If what you want are the files in the old home directory,  copy or move them, including any directories that are not in the new home. 

Going from 10.04 to 12.04, I would expect some apps to change the format and/or location of the config files they put in home. So there could be glitches with the old 10.04 config files.  If so, delete them and configure the app from scratch.

---

### Post by oldfred on 2014-04-13
Is /home a separate partition or just a folder?
Often easier as a separate partition and copy it before install so you can just mount it during install using the Something Else install option.

If just a folder you should be able to rename current home and copy in saved home.

If partition it would be more like this, but you may not need to copy with rsync commands:
       
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

