---
title: "media folder permissions - heyelp!"
date: 2007-03-26
forum: General Help
---

### Post by smurphs on 2007-03-26
Hi. I tried doing something complicated (i.e. stupid) with sbackup. I was trying to copy files from my windows NTFS partition to my external hard drive. 

Now I can no longer access either. They just don't appear in the file manager thingy (sorry, only recently left winworld), and I can only get to my media folder at all by using sudo -s in a terminal. 

Is this just a permissions thing or have I buggered it up completely? The data all seems fine and is perfectly accessible in windows.

Please help.

Dyl

---

### Post by smurphs on 2007-03-26
sorry - fixed it now. For anyone with similar problems, use the file browser thingy (nautilus) in root user mode by typing:

gksudo nautilus 

in the terminal window.

Then right click the media folder, select properties, goto permissions tab, and under 'others' change the folder access to 'access files'.

That should do it. reboot and your hard drive and windows partition will be on the desktop again. Huzzah!

see you

dyl

---

