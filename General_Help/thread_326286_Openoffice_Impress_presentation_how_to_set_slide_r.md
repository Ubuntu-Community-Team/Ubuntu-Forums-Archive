---
title: "Openoffice Impress presentation: how to set slide resolution / aspect ratio?"
date: 2006-12-27
forum: General Help
---

### Post by ariel on 2006-12-27
Hi, I am in the process of switching my office laptop from Win to Ubuntu Edgy. I am using openoffice 2.1.  

My laptop has an XGA display, with 1680x1050 native resolution. 

I am preparing some new presentations, and Openoffice / impress displays all my presentations in the laptop display aspect ratio (xga). However these presentations are meant for a projector that works in the standard VGA 1024x768.

I'm a newbie in openoffice and I can't seem to find nowhere in the settings and docs how to force Impress to show my slides with the normal aspect ratio, so my slide designs will show properly in the projector.

I tried changing my laptop's resolution using Edgy's System > Preferences > Screen Resolution, but this only shows 1280x1024 as the only option, which is obviously wrong, and does not let me change anything.

I'm sure other people run into this already but I don't seem to be finding other posts or references... any help or hint would be really appreciated !!

Thanks

---

### Post by sgbeamer on 2006-12-27
This sounds like a hardware vs a software problem.  The laptop outputs the screen to the projector.  You should be able to set your laptop resolution to that of the projector for making the presentation and solve your problem.  It might not look great on your laptop screen because it's not the native resoution of your lcd but should look okay on the projector.  If the menu's aren't doing it for you you may need to check your /etc/X11/xorg.conf file to make sure the display mode you want is set up there, then try the menus to select it.  You may also be able to set up the laptop video output as a second screen at a different resolution and solve the problem that way but that depends on your hardware.

---

