---
title: "Gusty gone mad a day after installation"
date: 2007-12-29
forum: General Help
---

### Post by zarnivop2 on 2007-12-29
The 1st batch of updates required restart.
After restart
1. Screen resolution dropped to 640x480 and will not change - no other resolution appears in "screen resolution" 
2. Wireless stopped working, though it seems the ESSID is correctly identified.

Hardware: IBM r40 laptop. 

Any help will be appreciated before reformatting and reinstalling.
-Z

---

### Post by taurus on 2007-12-29
1.  Have you tried to reconfigure your X server again with

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, restart X again with <Ctrl><Alt>Backspace.

---

### Post by zarnivop2 on 2007-12-30
:) Thanks. It worked.

---

