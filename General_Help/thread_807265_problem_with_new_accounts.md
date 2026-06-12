---
title: "problem with new accounts"
date: 2008-05-25
forum: General Help
---

### Post by vanadan on 2008-05-25
hi people, so what happend basicly..
when i loged in into my sisters account, it just showed an outline (shadow) of an error massage in the corner and did nothing.. what was wierd is that thare werent made any changes to the configuration of that accout.. 

i tried to solve it by deleting the account and making a new one.. almost the same thing, just that it wouldnt die on the startup but later, after an application or two were lounched.. (firefox and pidgin)

and it keeps doing this when i try adding new users.. :confused:

 (i use heron with gnome.. almost no changes into configuration made, the last things i installed before this happened was apache, php, mysql and the mp3 previewing thing, all of it just copy and paste into the terminal from the unofficial guide, and i fixed the [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/212648](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/212648) - the first workaround listed there) 

the other user accounts (made earlier) are all fine (so far)..

any suggestions what may be causing it?

---

### Post by vanadan on 2008-05-26
ok, found a solution.. used useradd instead of adduser and copied the files manually.. :lolflag:

update: at appears that it was caused by the upped bar(with menus, applications and clock) being moved to the bottom of the desktop..

---

