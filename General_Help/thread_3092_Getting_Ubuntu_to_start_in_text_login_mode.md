---
title: "Getting Ubuntu to start in text login mode"
date: 2004-11-03
forum: General Help
---

### Post by bd1308 on 2004-11-03
I dont like the GUI thing....I just like the ol' text mode and I want to do that. In the past it's been easier so I didnt have to go through files, but I am stumped. what I want is text all the way through...unless i want to start X with the startx command.

---

### Post by Rancoras on 2004-11-03
This forum is a place to post HOWTOS and FAQs, not requests for support.  Please post support requests in the appropriate forum.  Mod, please move this to General Support.

---

### Post by spoetnik on 2004-11-03
The easiest way is to install rcconf (apt-get install rcconf) and the run rcconf. Remove the asterix in front of GDM. Reboot et viola.

---

### Post by jdodson on 2004-11-03
Please post all general questions or comments to General Support.  

and by the way, you want to edit /etc/inittab and change the runlevel to 3 :smile: that will make your machine boot only into text mode and if you want to start gnome you can just type 'startx'.

---

### Post by az on 2004-11-03
You could also just remove gdm sith synaptic.

---

### Post by clauD on 2004-11-05
/etc/inittab 
id:3 
not worcking :((

---

### Post by eitch on 2004-11-05
Ubuntu starts normally in runlevel 2 and gdm is activated already. Just delete the link  link in /etc/rc2.d/S99gdm and then it won't start. To start the gui type init 3 or /etc/init.d/gdm start or startx

---

