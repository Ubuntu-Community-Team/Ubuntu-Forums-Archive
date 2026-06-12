---
title: ".Xauthority changed ownership"
date: 2004-11-24
forum: General Help
---

### Post by ubuntu_demon on 2004-11-24
Hi,

Problem already solved. But I'm curious what happened exactly.

I installed vtk : python-vtk , libvtk4, vtk-data, vtk-doc,vtk-examples. This broke ubuntu-desktop and removed nvidia-glrx. I changed back to my old XF86config-4 file and tried sudo startx / sudo gdm and suddenly I was in gnome as root(don't remember what I tried exactly). I couldn't get into my user account anymore (gnome worked). I discovered .Xauthority was owned by root instead of my user. I chowned it back to my user and I still couldn't get in. I discovered my harddrive was full. I removed some packages and could get in again.

Why is there no warning system / protection system for "full /"enabled ?

Did .Xauthority change ownership because I did startx ?

---

### Post by daniels on 2004-11-25
[QUOTE=demon666_nl]I installed vtk : python-vtk , libvtk4, vtk-data, vtk-doc,vtk-examples. This broke ubuntu-desktop and removed nvidia-glrx. I changed back to my old XF86config-4 file and tried [BOLD]sudo[/BOLD] startx / sudo gdm and suddenly I was in gnome as root(don't remember what I tried exactly). I couldn't get into my user account anymore (gnome worked). I discovered .Xauthority was owned by root instead of my user. I chowned it back to my user and I still couldn't get in. I discovered my harddrive was full. I removed some packages and could get in again.[/QUOTE]When you type 'sudo startx', what you are doing is starting X and all its applications as root, but with your home directory.  This is why .Xauthority changed ownership, and why you shouldn't do sudo startx.

---

### Post by ubuntu_demon on 2004-11-25
Yeah so I discovered :)

---

