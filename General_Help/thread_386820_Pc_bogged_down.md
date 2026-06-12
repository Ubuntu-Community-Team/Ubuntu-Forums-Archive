---
title: "Pc bogged down"
date: 2007-03-17
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2007-03-17
I came back froma  vacation, and after my computer loaded I realised it was running noticeably slower. Is there any way to find ut what's slowing it down? It was shutoff for a weeke we usually leave it on 24/7:)

---

### Post by bernied on 2007-03-17
Does 'top' tell you anything?

---

### Post by bernied on 2007-03-17
What sort of machine is it? Laptop? What sort of processor?
Is wireless installed? Is dhcp used? Is it working?

Check the output from:
```
dmesg
```these are kernel startup messages.
You can also view messages in real time at startup, either (i) hit Ctrl-Alt-F1 (or F2?) during startup, or (ii) edit your /boot/grub/menu.lst file and create an entry identical to the one you normally boot, but with the 'quiet' and 'splash' options removed, then boot that option (maybe don't do this unless you are happy with messing with your boot configuration).

---

### Post by bernied on 2007-03-17
And [here](http://www.ubuntuforums.org/showthread.php?t=386829) is someone else having similar trouble, you might want to follow their thread as well.

---

