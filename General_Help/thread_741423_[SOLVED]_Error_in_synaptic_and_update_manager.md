---
title: "[SOLVED] Error in synaptic and update manager"
date: 2008-03-31
forum: General Help
---

### Post by eduren on 2008-03-31
Whenever i open Synaptic and/or try to download updates thru update manager i get an error message that says

E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)

Synaptic never opens and update manager refuses to DL updates. it still shows the updates but i cannot download, when i try i get that message.

This is on 8.04 beta but i didnt think it mattered. if it does, sorry for posting in the wrong forum

---

### Post by sancho panza on 2008-03-31
Is your username root? Else, there should be not folder /home/root. Having a user with username root might create problems, as the name root is reserved for the sys admin.

---

### Post by eduren on 2008-03-31
i have not messed with root in any way and there is no /Home/root directory

---

### Post by eduren on 2008-03-31
help please

---

### Post by gsmanners on 2008-03-31
Try doing the following in a console:

ls /home -o

---

### Post by eduren on 2008-03-31
i did

total 20
drwx------  2 root 16384 2008-03-29 14:45 lost+found
drwxr-xr-x 51 ryan  4096 2008-03-31 16:36 ryan

---

### Post by gsmanners on 2008-03-31
Okay. Maybe it's related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/198172](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/198172)

---

### Post by eduren on 2008-03-31
Ok i lied i did mess with root i changed its password. could that be it?

---

### Post by eduren on 2008-03-31
thank you so much, it worked

---

