---
title: "external hd between untunbu and xp (on vmware)"
date: 2007-04-28
forum: General Help
---

### Post by delar0cha on 2007-04-28
ok so this is the situation-

i've installed xp on vmware cuz i have to use a windows program to download stuff from this site.
(usually movies and music) so what i do is

-unmount my external hd (if i don't xp in vmware don't recognise it)
-use the windows program to down to my external hd
-remove the external hd in windows after finishing the download (by unchecking the device under vmware->vm->removeable devices.)
-then mounted it back on in ubuntu :(

so my question is, is there a way to use my external hd simultaneously by both ubuntu and xp (under vmware) so i don't have to go thru the steps written above? :(

for example what i want to be able to do is
download to my external hd thru xp,
and watch/listen to it in ubuntu while it's downloading

wow that was one long question;; i'm sure there's an easier way to ask but i don't know how :)

anywayz newb needs help!!

thanx in advance-

p.s - the external hd uses usb connection btw

---

### Post by PilotJLR on 2007-04-28
It's much easier to use Samba.
Just keep the drive mounted in the Ubuntu host, and share it via Samba.

---

