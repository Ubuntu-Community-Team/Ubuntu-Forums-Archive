---
title: "Help me pick packages to install on a home server"
date: 2007-10-07
forum: General Help
---

### Post by bthessel on 2007-10-07
I am rebuilding my home server and looking for recommendations. I am going to start with Gutsy Alternate. I will leave the GUI since there are times I like to use it :). I have a athlon 2600+ with a gig of ram and 4 hard drives, 2 x 250 GB sata's and 2 x 200 pata's. In the past I had software mirrored 200 from the sata's as one volume and all of the pata's as a second volume. I had samba installed and was using Webmin for management. Should I set the drives up the same way again? What other packages would you recommend on a home server?

---

### Post by MetalMusicAddict on 2007-10-07
On my server I sometimes need a desktop. It runs headless and when needed I use VNC. My installed packages, on top of a CLI system install are:
[LIST]
[*]xfce4
[*]samba
[*]smbfs
[*]gdm
[*]xorg
[*]apache2
[*]x11vnc
[*]openssh-server
[*]bittornado-gui
[*]xfce4-systemload-plugin
[*]xfce4-terminal
[*]system-printer-config
[/LIST]
Some of those things are there "just in case". I will say X over SSH _RAWKS_. ;)

---

### Post by Elshadii on 2007-10-14
Why not just d/l the Ubuntu Server cd?

---

