---
title: "Overlay Scrollbars Disappear"
date: 2013-05-10
forum: General Help
---

### Post by jim_deadlock on 2013-05-10
I'm running 13.04 + Gnome Shell 3.8.1 (the same problem applies if I switch to Unity)


With apps that have the overlay scrollbars (eg Nautilus, Gedit) the overlay appears the first time I mouse over it and works fine, but then if I try it again it doesn't appear at all. Restarting the app resets it so that it works again the first time. Any ideas?

---

### Post by dino99 on 2013-05-10
are you using some ppas ? maybe a libcairo issue
how many overlay-scrollbar package installed ?

---

### Post by jim_deadlock on 2013-05-10
The only PPAs I have are: Google Earth; Grub Customizer; Medibuntu; Gnome3

I don't think any of those are relevant but I could be wrong.

---

### Post by mc4man on 2013-05-10
> **jim_deadlock said:**
> The only PPAs I have are: Google Earth; Grub Customizer; Medibuntu; Gnome3

I don't think any of those are relevant but I could be wrong.
gnome3 ppa is certainly relevant, overlay scrollbars are broken with it.

---

### Post by jim_deadlock on 2013-05-10
:lolflag: fair enough!

I found the bug report thanks - [https://bugs.launchpad.net/overlay-scrollbar/+bug/1174927](https://bugs.launchpad.net/overlay-scrollbar/+bug/1174927)

---

### Post by mc4man on 2013-05-10
Hopefully they'll find a fix that doesn't need re-repair down the road (with Ubuntu now staying 1 release behind gnome

With the latest gtk/gnome the scrollbars work but are huge (only tested with a unity session

---

