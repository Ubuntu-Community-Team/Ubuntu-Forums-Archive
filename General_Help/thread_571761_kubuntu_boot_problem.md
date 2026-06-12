---
title: "kubuntu boot problem"
date: 2007-10-09
forum: General Help
---

### Post by tomar on 2007-10-09
Hi
I am getting the following message at boot:
kinit:trying to resume from /dev/disk/by-uuid/1fd23d31-ef13-4d82-89a9-530c6d451944
kinit: No resume image, doing normal boot 
Ubuntu 7.04 tomar-desktop tty1
tomar-desktop login:

How do I get to boot

Tom

---

### Post by dabl on 2007-10-09
[QUOTE=tomar;3504873]Hi

tomar-desktop login:

/QUOTE]

Hmmmmmm -- that kinda resembles a CLI login prompt -- is there a "~$" sign beside it?

---

### Post by tomar on 2007-10-11
No.
last line just reads tomar-desktop login:

---

### Post by kellemes on 2007-10-11
Yes, seems like a console login..
Type your username and password and see what happens.

---

### Post by perlluver on 2007-10-11
You will also probably have to type startx, if that doesn't work you will probably have to rebuild the kernel from the grub loader.  I had that problem after I installed the Nvidia drivers.

---

### Post by tomar on 2007-10-12
Username and password bring me to
tomar@tomar-desktop:~$

I tried startx also but this also brings me to
tomar@tomar-desktop:~$

I'm afraod I dont even know what 'to rebuild the kernel from the grub loader' means
dont mind rebuilding it.

---

