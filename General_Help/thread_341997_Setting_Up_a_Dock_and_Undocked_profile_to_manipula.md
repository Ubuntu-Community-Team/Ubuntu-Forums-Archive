---
title: "Setting Up a Dock and Undocked profile to manipulate Xorg"
date: 2007-01-19
forum: General Help
---

### Post by Joseph Brown on 2007-01-19
Running Ubuntu 6.10 I am trying to get a laptop to have a Docked and Undocked profile. Basically I would like my docked profile to use a dual monitor xorg file and by undocked to use a single LCD xorg file. Searching the web one solution was to edit /boot/grub/menu.lst to allow for the passing of different runlevel variables into a script that would copying a defined xorg file to the current xorg file. However, I am having issues with my menu.lst file and getting the PC to boot into a different runlevel other than 2. Since Ubuntu 6.10 has changed from /etc/inittab to this new Upstart I am not sure if I can change the runlevel. Finally, if anyone know how I can setup ubuntu to ask for a profile and I can take that input and script it to run the correct xorg file before xorg loads let me know.

---

### Post by Joseph Brown on 2007-01-26
Solution found. I wrote a script to use ddcprobe to determine the settings of the active monitor. Then based on the results I copied the correct xorg.conf into /etc/X11/. For this to work I need the xorg.conf file to be copied before the gdm loaded x server and started x. To do this I called my script from /etc/init.d/gdm.

---

