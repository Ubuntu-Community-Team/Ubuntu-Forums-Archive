---
title: "[SOLVED] ati radeon 9800 pro and component cables OR adding more options for screen r"
date: 2007-04-13
forum: General Help
---

### Post by unebaguettesvp on 2007-04-13
hi!

so, i have an "ATI Radeon 9800PRO 128MB DDR AGP 4X/8X All-In-Wonder Video Card" and it works perfectly with ubuntu using a 19" LCD monitor. for that setup, i used the dvi-to-vga converter and it's cool.

now, i want to connect my computer to my receiver using component cables. my receiver is connected to a projector by component cables. but when i use the red component cable hook up thing (that came with the card) to my receiver, it works, but the resolution is incredibly small!!!!

is it possible to send a computer resolution through component cables? i would think so because my projector can support 1080p with component cables.

so, when i try to change the screen resolution, i have three choices:

800x600 @ 60 Hz
800x600 @ 56 Hz
640x480 @ 60 Hz

Only the 800x600 @ 60 Hz doesn't work.

How do I create more options for screen resolutions? The native resolution of my projector is 720p. I would like to use that. How do I do that?

---

### Post by unebaguettesvp on 2007-11-02
i solved this problem by creating a new modeline with one of the many online modeline configuration tools. and then i added the new modeline to the relevant section in the xorg.conf.

---

