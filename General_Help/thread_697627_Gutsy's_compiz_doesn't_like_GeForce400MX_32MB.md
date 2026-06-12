---
title: "Gutsy's compiz doesn't like GeForce400MX 32MB"
date: 2008-02-15
forum: General Help
---

### Post by pandamonium54 on 2008-02-15
Backstory: I want my GUI to mimic OS X.

Compiz worked fine with Feisty, (most of the time, sometimes I got the black window effect) but one of the guides I'm using for for mimicry of OS X's GUI starts with Gutsy. I upgraded to Gutsy, and now I can't enable desktop effects. I need to get AWN started, but I gather that AWN requires compiz. So what can I do? I've tried installing Metacity, but it doesn't seem to be doing anything. I'm not sure if I'm installing Metacity correctly, but I followed the steps here: [http://dagus.org/2007/11/28/metacity-beats-compiz-fusion-p/](http://dagus.org/2007/11/28/metacity-beats-compiz-fusion-p/)

I manually added "/home/administrator/metacity/src/metacity --replace" to my session/startup.

Relevant hardware: GeForce MX400 32MB

Output from $ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 10de:0110 (rev b2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

