---
title: "what commands to uninstall duplicate sources lists in repositories"
date: 2008-01-10
forum: General Help
---

### Post by streamsanddragonflies on 2008-01-10
HI!
I just want to be clear on the procedure to remove these lists that I duplicated because I was figuring out how to install them properly in the first place. 

 Note: they are related to cinelerra, and I am still baffled by the procedure to install it in gutsy!


W: Duplicate sources.list entry cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/main Packages (/var/lib/apt/lists/Ubuntu-Studio%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20i386%20(20071015)_dists_gutsy_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/multiverse Packages (/var/lib/apt/lists/Ubuntu-Studio%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20i386%20(20071015)_dists_gutsy_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/restricted Packages (/var/lib/apt/lists/Ubuntu-Studio%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20i386%20(20071015)_dists_gutsy_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu-Studio 7.10 _Gutsy Gibbon_ - Release i386 (20071015) gutsy/universe Packages (/var/lib/apt/lists/Ubuntu-Studio%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20i386%20(20071015)_dists_gutsy_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://repository.akirad.net](http://repository.akirad.net) akirad-gutsy/main Packages (/var/lib/apt/lists/repository.akirad.net_dists_akirad-gutsy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by forestpixie on 2008-01-10
edit the sources.list - to comment a line use # or alternatively delete it, to uncomment a line remove the #

I'd do a backup if you're not sure 
you coudl use nano or the text editor of your choice

open it with root rights

sudo nano /etc/apt/sources.list
gksudo gedit/etc/apt/sources.list

---

