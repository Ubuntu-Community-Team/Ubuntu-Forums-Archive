---
title: "&quot;@&quot; key problem"
date: 2005-10-18
forum: General Help
---

### Post by lonmyown on 2005-10-18
I have a silly problem with the Turkish keyboard on my Packard bell b3650 laptop. Every other single thing is working perfect but I just cant use the "@" character:???: . Normaly it should be working by pressing alt+q. the "alt" and the "q" key works seperatly. 

somebody please help me, I am really eager to use ubuntu 5.10 on my computer.

---

### Post by kairu0 on 2005-10-19
Check /etc/X11/xkb/symbols/(your layout file) to see if your layout agrees that "@" should be that key combination.

---

### Post by fallencan on 2005-11-08
edit xorg.conf file. at device input section delete the line with
Option     "XkbVariant" "q"

after deleting this restart xorg. this will help u with the keyboard problem

---

