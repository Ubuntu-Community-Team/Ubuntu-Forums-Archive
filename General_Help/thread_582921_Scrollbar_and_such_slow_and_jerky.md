---
title: "Scrollbar and such slow and jerky"
date: 2007-10-20
forum: General Help
---

### Post by tijmz on 2007-10-20
Hi all,

I recently returned to Ubuntu and upgraded a fresh 7.04 install to 7.10. It works like a charm, except for one thing. Scrolling through an Amarok playlist or maximizing its windows leads to very slow, jerky responses. All the buttons work perfectly, I can quickly switch from song to song, but all things related to the Amarok windows leave me mostly staring at blank spaces throughout my screen.

Disabling the restricted ATI driver (i.e. booting in 'safe mode') solves the problem, so I figure something is wrong with the setup of my video card, but I am clueless as how to fix it. Other applications (e.g. Mozilla Firefox) show no problems with the scrollbar or maximizations, though moving the windows around seems somewhat jerky. Maybe it also has something to do with running a KDE app outside its native environment?

Any help would be greatly appreciated :D

The video card I use is an ATI Sapphire X1950GT.

---

### Post by GSF on 2007-10-20
i have a similar problem...... although im really new in linux (its my first distribution that actually works even with minor problems) ..  i have an ATI X1600 pro 512... scrolling in firefox or in amarok or in opera..... is REALLY slow.....and seems to use a lot of cpu, when desktop effects is active. 

but if i turn them off, other things are slow.... like keyboard typing.. or the menu loading (on top left) .. at some point, with specific desktop effects configuration, i managed to fix it.... when firefox was open in full screen. but then it broke again (maybe i changed something) Now the only way to visit web sites is when im using firefox in a little window about 400x300....and it scrolls fine. other than that, gutsy is the ultimate linux distro so far :D :D everything works sooooo fine

---

### Post by tijmz on 2007-10-21
I installed Konqueror and checked how that worked. The problem is basically the same. My question boils down to this then I think: how can I get KDE applications to run smoothly in GNOME with my video card? I used to have things running smoothly (in 6.06) but at that time I had a different video card.

Help!

**EDIT:***sudo apt-get remove xserver-xgl*, as per [this thread](http://ubuntuforums.org/showthread.php?t=579762), worked pretty well for me. There is still some trailing from window dragging, and sometimes the scrolling is jerky, but it's nowhere near as bothersome as it was.

---

