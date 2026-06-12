---
title: "Xubuntu Help"
date: 2008-05-27
forum: General Help
---

### Post by deamon_knight on 2008-05-27
I'm trying to get some help with configuring Xubuntu. I've setup a dual-boot on a powerbook G3, but the PPC version is in a rough state. I want to add to my desktop a link to the Mac partiton, just like a link shows up when a USB hard drive is connected. The Mac partition is mounted and I can explore it in the file manager, but I'd like a desktop shortcut.

I've also got a broken dependency after installing open office:

E: openoffice.org-writer2latex: subprocess post-installation script returned error exit status 1
E: openoffice.org: dependency problems - leaving unconfigured


 Any advice?
Thanks

---

### Post by morgengenuss on 2008-05-27
for the broken dependency: go to synaptic -> edit -> fix broken packages
that should help.

for the desktop-shortcut you could either create a launcher (right-click on the desktop) and for the command use "thunar /path/to/your/partition". that would be about it.

---

### Post by deamon_knight on 2008-05-27
OK, but I'm not entirely sure what my path should be. Is the Moint point?

/media/OSX

or 

/Dev/hda4

?

---

### Post by morgengenuss on 2008-05-27
it's the mount-point (/media/OSX). tbh you could have simply tried both options...

---

