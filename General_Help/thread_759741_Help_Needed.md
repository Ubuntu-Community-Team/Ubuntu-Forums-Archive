---
title: "Help Needed"
date: 2008-04-19
forum: General Help
---

### Post by scouser73 on 2008-04-19
I'm not sure if this topic has already been made aware, or if it is just my PC.

I have Ubuntu Gutsy Gibbon running, and I've not switched the pc off for about 1 week now. When I last switched it off and left it for a few hours and I went to restart it, the monitor came up with a message similar to "no signal found".

My graphics card is an nVidia Geforce 6200. I plan to switch to Hardy Heron when the disc arrives and would really like to have this issue resolved.

---

### Post by schauerlich on 2008-04-19
Deleted.

---

### Post by prshah on 2008-04-19
> **scouser73 said:**
> 
 the monitor came up with a message similar to "no signal found".
My graphics card is an nVidia Geforce 6200. I plan to switch to Hardy Heron when the disc arrives and would really like to have this issue resolved.

Press Ctrl+Alt+F1; within a few seconds your screen should appear in text mode. If it does then it's a refresh rate issue. You can fix it by using the command```
sudo dpkg-reconfigure xserver-xorg
```, but before this, make a copy of your original config file with ```
cp /etc/X11/xorg.conf ~
```.

If you don't get a text mode screen on pressing ctrl+alt+f1, then there is some other problem; what is the last thing you see on the screen before the "no signal found" type message appears?

---

### Post by scouser73 on 2008-07-13
[SOLVED] Help Needed

---

