---
title: "The entire touchpad on my laptop does edge scrolling only."
date: 2019-10-24
forum: General Help
---

### Post by unboltingtoe on 2019-10-24
I updated my OS from the previous version 19.04 to the newest version 19.10 and now my touchpad is messed up. It worked fine previously. The edge scrolling area is supposed to be just a small rectangular piece on the right side of my touchpad but instead, the entire touchpad now does edge scrolling **only** and so I cannot move my cursor with my touchpad unless I disable edge scrolling. I used my keyboard to navigate to "mouse and keyboard" and disabled edge  scrolling. I can now move my mouse around which is great but I also can't edge scroll at all. I want to be able to move my cursor and edge scroll simultaneously, like before. I have a Lenovo G580 laptop.

---

### Post by kansasnoob on 2019-10-24
I encountered a totally different "glitch" with the touchpad on an old Dell Latitude E6400 and had to install 'xserver-xorg-input-synaptics', then reboot to get things working right. A reboot was required. Oh and it's in the "partners" repo. It might be worth a try and if it doesn't help that package could easily be purged.

---

