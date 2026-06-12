---
title: "The keyboard does not work at all"
date: 2013-09-10
forum: General Help
---

### Post by nijunge on 2013-09-10
Yes Im new to linux and ubuntu 

I have installed ubuntu 13.10 on a USB and booted fine 

(computer is a LG E200 laptop) 

BUT the keyboard does not work at all, the build in mouse pad and external mouse works fine.

I have googled it but only found old or not semilar problems, could anyone give a hint on what to try, I have a feeling that it could be simple ;-) 

N

---

### Post by Kirboosy on 2013-09-10
Hi Nijunge! Welcome to the forums! :D

I found on launchpad a bug report about your exact laptop. They did post a solution about it as well. I'm not sure if this will solve your problems but its worth a shot. Post number 8 contains the fix.
[URL="https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/292954"]
Bug #292954 Keyboard Doesn't Work[/URL]


EDIT: Also there is a wiki entry on how to permanently set your boot options on your installation.

[BootOptions -Community Documentation]("https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation")

Hope that helps!
~Caboose

---

### Post by nijunge on 2013-09-11
Thanks for the answer, belive that will help BUT it seems that as I use a USB test without real install there is no grub or grub2 for that matter the only files that are in the 2 grub folders are loopback files whatever that is.

should I simply try another version of Ubuntu to test or go for the install from the start ? 

N

---

### Post by nijunge on 2013-09-12
OK so I installed it instead 

found the sneaky "e" keystroke to get into the grub file, typed the line in in as the last line now it actually make an error message in the start instead.

Wanted to remove the line from grub but its actually gone.

Im really get in over my head here. 

By the way the external keybord works fine and the internal key board works up to start of ubuntu

---

### Post by Kirboosy on 2013-09-12
Any time you make a change to grub like that (using the 'e' key) its only temporary. Meaning for that boot only. Upon rebooting the computer it should go back to the default configuration of GRUB

---

