---
title: "xorg.conf does not save after reboot"
date: 2007-02-27
forum: General Help
---

### Post by octopuskevin on 2007-02-27
Hi, just a quick problem

my synaptics driver during installation didnt load property, because scrolling support does not work. I did some work arounds and found i had to add "option SHMConfig "on" to my xorg.conf under input devices.

this fixes the problem during the session after a quick 'ctrl''alt'backspace' however after reboot, xorg.conf deletes what i added. anything i'm missing here thats important?

and yes, i edited it via sudo :P

thanks!

Kevin

---

