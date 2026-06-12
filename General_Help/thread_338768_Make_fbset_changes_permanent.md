---
title: "Make fbset changes permanent"
date: 2007-01-14
forum: General Help
---

### Post by szim90 on 2007-01-14
Hello.

I noticed that the the screen geometry is off during startup and when I switch to a virtual terminal (the text starts about an inch from the left side of the screen and ends off screen to the right). I was able to fix the problem using fbset, but when I reboot, the computer switches back to the original settings. I have tried altering what appears to be the corresponding entry in /etc/fb.modes, but that did not help. How can I make the changes with fbset permanent so that when I start the system, the text lines up with the screen?

I have both vga and riva frame buffers compiled into the kernel, but I am not sure which one the system is using. I am using a Powermac G4 Quicksilver running Ubuntu Edgy.

Thank you for any help.

Sean

---

