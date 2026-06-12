---
title: "dpkg"
date: 2004-11-02
forum: General Help
---

### Post by ToWAH on 2004-11-02
what is the command for dpkg gnome packet manager or what name is ?
coz  now its evaporate from system configurator menus 
plenty of bugs humm

---

### Post by ynef on 2004-11-02
You're talking about synaptic.

---

### Post by ToWAH on 2004-11-02
sure lol
its evaporate no more no nothing 
no ati radeon drivers 
need unnistall Stupid Mesa 3D for replace it to install ati fglrx driver 
think time to change this linux for other that work, coz this linux is madness
 [-(

---

### Post by mercurus on 2004-11-02
[QUOTE=ToWAH]sure lol
its evaporate no more no nothing 
no ati radeon drivers 
need unnistall Stupid Mesa 3D for replace it to install ati fglrx driver 
think time to change this linux for other that work, coz this linux is madness
 [-([/QUOTE]

*cough*

Use synaptic to remove the mesa 3d drivers you've installed, and then use synaptic  to install the correct ATI driver for your card.

If synaptic has vanished, you can use the command line and apt-get to install what you're looking for. Try the Wiki for detailed instructions and documentation.

Cheers
David

---

### Post by ToWAH on 2004-11-02
[QUOTE=mercurus]*cough*

Use synaptic to remove the mesa 3d drivers you've installed, and then use synaptic  to install the correct ATI driver for your card.

If synaptic has vanished, you can use the command line and apt-get to install what you're looking for. Try the Wiki for detailed instructions and documentation.

Cheers
David[/QUOTE]
lol David , im David  :D
well synaptic has vanished and i understand u but my question its How to synaptic comeback in gnome menus
lol

ok Mesa3D unistall command is ?
rolf

---

### Post by fng on 2004-11-02
- Open the computer menu -> system configuration -> right click on the submenu -> Entire Menu -> Add a new entry to this menu.

Name : Synaptic Package Manager
Generic Name : Package Manager
Comment : Install, remove and upgrade software packages
Command : gksudo /usr/sbin/synaptic
Type : Application
Icon : /usr/share/pixmaps/synaptic.png

---

### Post by jdusablon on 2004-11-02
That has got to be the shortest, most precise and correct forum answer ever.

Nice work!

---

