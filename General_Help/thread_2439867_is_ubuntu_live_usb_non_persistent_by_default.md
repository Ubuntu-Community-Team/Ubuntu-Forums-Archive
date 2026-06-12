---
title: "is ubuntu live usb non persistent by default ?"
date: 2020-04-02
forum: General Help
---

### Post by empleat on 2020-04-02
When i create bootable usb, using program included in ubuntu live system, i forget how it calls. Is it non persistent by default ? Btw does it mean, if i put some file there, it will get deleted after restart too ? 
Thanks for an answer.

---

### Post by ajgreeny on 2020-04-02
Yes and yes.

If you want or need persistence you have to make sure that you create a USB live system that has it; how exactly you do that depends on which software you use to create the USB.

I would suggest that if you already are running a *ubuntu OS of some kind you should use [mkusb]("https://help.ubuntu.com/community/mkusb") to create the USB.

---

### Post by sudodus on 2020-04-02
Ubuntu live is **not** persistent by default. Things are somewhat different depending on the version (18.04.x LTS and older or 19.10 and newer).

The following link and links from it can help you with more details.

[How is it easier to make a persistent live drive with Ubuntu 19.10?](https://askubuntu.com/questions/1181854/how-is-it-easier-to-make-a-persistent-live-drive-with-ubuntu-19-10)

---

### Post by empleat on 2020-04-02
Okay thanks much ! Couldn't find it anywhere for some reason.

---

### Post by Bashing-om on 2020-04-02
empleatl additional info :)

Per standard protocol the .ISO medium is read-only:
[https://en.wikipedia.org/wiki/ISO_9660](https://en.wikipedia.org/wiki/ISO_9660)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by C.S.Cameron on 2020-04-03
Ubuntu 9.10 and later are Persistent on demand by default.

If you want a persistent boot

- For a drive made with Startup Disk Creator, Etcher or dd press Shift when booting *

- Press Esc at the Language screen

- Press F6

- Press Esc at the pop up

- Type a space and then "persistent"

Every thing in that session will be persistent

- If you want the next session to use the downloaded programs, data and settings from the persistent session repeat the boot proceedure.
 
- If you want the next session to be a standard Live session boot normally.
 

* For a non persistent drive made with UNetbootin press Tab at the menu screen.

---

