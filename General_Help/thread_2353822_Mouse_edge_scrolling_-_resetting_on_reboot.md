---
title: "Mouse edge scrolling - resetting on reboot"
date: 2017-02-25
forum: General Help
---

### Post by amtrakuk on 2017-02-25
Hi.

I'm using 16.04 / 64 bit Ubuntu on my Fujitsu Laptop

I am having issues with the mousepad.  I disable the horizontal and vertical edge scrolling with synclient VertEdgeScroll=0 and the horizontal scroll.  Everything is OK until reboot when all the changes are undone and I have to set the values again.  How can I permanently disable mousepad scrolling - its a pain in the neck!

Thanks

---

### Post by vasa1 on 2017-02-25
I put synclient stuff like```
synclient VertEdgeScroll=0
```in my autostart.

---

### Post by amtrakuk on 2017-02-25
Adding to "Start Up Applications" - fantastic idea.  Will give it a go - thanks ;)

---

### Post by vasa1 on 2017-02-25
A similar route is taken in the last post in this thread: [https://ubuntuforums.org/showthread.php?t=1855689](https://ubuntuforums.org/showthread.php?t=1855689)

While editing a system file, */usr/share/X11/xorg.conf.d/50-synaptics.conf*(?), may also work, it may need tending whenever an update changes the relevant file.

---

