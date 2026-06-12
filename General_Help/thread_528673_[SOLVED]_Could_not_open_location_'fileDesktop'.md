---
title: "[SOLVED] Could not open location 'file:///Desktop'"
date: 2007-08-18
forum: General Help
---

### Post by sawjew on 2007-08-18
This is the message I get whenever I try to access my desktop through the Places menu.  

Also when I drag and drop a file or anything onto the desktop it doesn't show up on the desktop.  I can find the files I dropped on the desktop by going to /home/stephen/Desktop/ but they do not show up on the actual desktop and I cannot access the desktop through Places. 

The system seems to have lost the connection between the desktop and the desktop directory in my home directory.  If anyone has any ideas on how to restore this connection it would be much appreciated.

NOTE: I am using Ubuntu 7.04 (Feisty) x86_64

---

### Post by ajgreeny on 2007-08-18
I think the folder **file:///Desktop** is a relic of other linux distros where the root account is still a valid one.  Ubuntu uses the sudo system instead so there is not a way to access the root desktop without activating the root user account.  The desktop you see is /home/username/desktop, quite a different place to **file:///Desktop**

---

### Post by sawjew on 2007-08-18
The issue seems to have fixed itself.  After I unmounted my flash drive it was fine.  I use PortableApps on my flash drive and I was running the PortableApps Menu using wine and I think it may have been something to do with wine using the desktop at the same time.  It's probably one of these wine/compiz conflict issues that crop up occasionally.

---

### Post by Madvil on 2007-10-20
I have about the same problem.
I tried to install the restricted drivers for ATI glfx support in order for ubuntu to recognize my X850XT properly and when I activated then, all of a sudden I lost the desktop icons, wallpaper and when I try to browse to any system location I get the same error as above.

Now, I tried to uninstall the glfx restricted drivers and reinstall them but that didn't worked...

Help please? :(

---

