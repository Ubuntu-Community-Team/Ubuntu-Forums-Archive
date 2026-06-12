---
title: "Change screen resolution"
date: 2013-11-25
forum: General Help
---

### Post by stephen-tredbear on 2013-11-25
Hi,

My Notebook's screen is smashed. When I plug-in an external monitor it tells me the resolution is not optimal. How would I change this working blindly? I'm able to get past GRUB and believe I login in but not sure what to do from there using key presses.

Fixing the screen is not an option is the cost is the same as getting a new notebook (money which I don't have).

Advise welcome, Stephen

---

### Post by papibe on 2013-11-25
Hi stephen-tredbear. Welcome to the forum ):P

If I understand correctly, you are not able to see anything on the external monitor?

Are you able to get a text mode prompt if you press Ctrl+Alt+F1? If so, try login and rename your Xorg config:
```
sudo mv -iv /etc/X11/xorg.conf /etc/X11/xorg.conf.old.back
```
And then restart:
```
sudo reboot
```
Let us know how it goes.
Regards.

---

