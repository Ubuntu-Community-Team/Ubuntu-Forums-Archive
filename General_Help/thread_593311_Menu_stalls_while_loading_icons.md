---
title: "Menu stalls while loading icons"
date: 2007-10-27
forum: General Help
---

### Post by Nexus Delta on 2007-10-27
I just upgraded to Gutsy. After installing I noticed that when I navigate to the "Accessories" menu listing of the gnome panel the menu stalls and I can't select anything for a good 15 seconds. During this time there are no small icons next to the programs. This only happens the "first" time I navigate there and only at that listing. After it stalls for about 15-20 seconds the icons appear and I can then select programs or do whatever. It never happens again unless I reboot, logout and back in, or switch users. I have an nvidia 7600. I am using the restricted driver manager for the driver and I have desktop effect enabled. Any ideas?

---

### Post by julianramon on 2007-11-07
I have the same problem in Gutsy. The same behaviour. However, I have found out it happens only with the accessories sub-menu

---

### Post by julianramon on 2008-02-06
Solved! The problem was a menu element had a big, big image. In my case the element was to open LaCie Lightscribe Labeler for Linux. The default icon was in fact an one of the high resolution image the software used as a template to print CD Labels. The solution was to change the icon for one of the gnome default icons in /usr/share/icons.

---

