---
title: "[SOLVED] Segmentation error dump mem error cannot open anything requires root privela"
date: 2007-08-12
forum: General Help
---

### Post by nowshining on 2007-08-12
i now cannot open anything that requres any root priveleges such as user groups, cannot do a sudo gedit as it gives me a segmentation error, and such, cannot login into root account and says i've been logged into too short and logs me out, cannot check for updates gives me a diff. error... :( however out of all this only one good thing came about, I figured out how to increase the 82865g resolution to 1600x1200 and there is one more higher mode that this will go but for now this is right..lolz...supposedly u cannot go higher with the integrated graphics card, lolz but i did without 915resolution..okay here's the story..

Say in synaptic package manger 915resolution - read it..lolz
installed it - saw no icon in start menu, thought terminal, typed it it ran, well figured out how to do that, well anyway I really didn't go far but only to change the Bit/pixels or whatever in xorg.conf to 24 & added under 24 bits 1600x1200 - went into gconfig and changed the refresh rate to 90 both user and default and also changed the reso to 1600x1200, nothing at that time, everything worked fine, but then decided to open login manager - well the bottom where the okay, etc.. were was cut off by the taskbar, went into properties thinking somehow it got too big, did actually, but the small size only went down so far but not as far as it would go...anyway went into and edited xorg.conf removed 1600x1200 under 24. rebooted because of hosts issues - odd tho that it got bunched up and all the local address 127.0.0.1 was missing - have backup and since I have a MASSIVE hosts file the swap kicks in when opened and makes things slower even when exited - reboot and now am having these issues - lolz... well all-in all forgot to change the pix rage down to 16, copied it to desktop edited it and finally after some googling the sudo rm worked and so removed that and put it as before i even edited it, rebooted still no go, well to end the asking for help my last item i found googling was to let xorg.conf re-create itself, and this is after I edit gconf (registry like editor) back to the old 1600x1200 90 htz stuff and re-edited the xorg back like it was before i started getting the problems..lolz still no go and that's when i decided to let it re-create itself and now I got 1600x1200 90htz or so, when the xorg.conf is re-created but am having the issues and most root things just exit out..

sudo gedit gives me the following error (or anything about sudoed) even tried in safe terminal mode - still no go..

Segmentation fault (core dumped)


updates give me the following when trying to check for any:(reloading sources)::

E: Method http has died unexpectedly!


again however everything in normal user mode works fine :P i can dial out to the net like here, etc...just anything having to do with root.. :( that includes my firewall right now...

---

### Post by nowshining on 2007-08-12
Fixed - I believe, thought it out, did sudo rm /etc/hosts and now those things startup and i can log into root, i'll file a bug report :) it was the garbled up hosts file that kicked me out... which some how got that way itself..

---

