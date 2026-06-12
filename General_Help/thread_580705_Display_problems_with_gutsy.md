---
title: "Display problems with gutsy"
date: 2007-10-19
forum: General Help
---

### Post by Hybrid86 on 2007-10-19
After upgrading and and restarting, I received an error message that the screen could not output to its normal dimensions (1280x800) and was forced to select from a giant list of monitors and graphics cards. Unfortunately, my choices were only limited to 640x480 and 800x600. since this was about the 100th problem since my upgrade, I decided to just back up my files and try for a clean install. sure enough, the live cd displayed fine, so I formatted/reinstalled. however, after restarting, the exact same display issue occurred!

Confused, I (stupidly) tried to change the selected graphics card, and now the display is unreadable.
Has anyone else had this problem? How do I fix this?

---

### Post by Hybrid86 on 2007-10-20
Sorry for the double post but please, can anyone help me?

---

### Post by dietrying on 2007-10-20
hi,
please try to configure your graphicscard and screen via terminal by typing:

sudo dpkg-reconfigure xserver-xorg. 

It's the more save way, and there you can choose the resolutions you need. I had also much trouble with the graphic screen configuration tool. It remembers me on buggy yast2 times with suse 7.3.......hope for very much bugfixes till hardy heron ;-))
good luck

---

