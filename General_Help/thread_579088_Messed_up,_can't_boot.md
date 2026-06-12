---
title: "Messed up, can't boot"
date: 2007-10-17
forum: General Help
---

### Post by ddcollins4 on 2007-10-17
I goofed by making some changes to /etc/X11/xorg.conf that the system didn't like. I booted to Recovery mode, used ed to undo the changes, but when I tried to save the file it said Permission Denied. I thought (from reading many posts here) that in Recovery mode I didn't need to log in and I would have all required priveleges to edit and copy files. Can anybody tell what I'm doing wrong?

---

### Post by ddcollins4 on 2007-10-18
Oops I figured it out. When I boot to the normal system, and it fails to load X11, then I log in, but it won't let me save any chages I make to xorg.conf (WHY??). When I boot to Recovery Mode, I can change the file and save the changes. And thus I was able to repair the damage.
Thanks anyway.

---

