---
title: "Resuming from Sleep mode"
date: 2007-07-08
forum: General Help
---

### Post by bobshowrocks on 2007-07-08
I have an old Abit IS7 motherboard (865PE chipset) with a 3.2GHzP4, nVidia FX5200 video card, 1 GB of generic RAM, and a D-Link DWL-G520 wireless card. The problem is when I resume from S3 sleep mode (suspend to RAM). The screen turns on and shows the several lines of things, but then instead of showing the login box, the screen is filled with white triangles. The are the same general size and shape as the command line, (not the terminal in a desktop environment). Is there some fix for this?

---

### Post by bobshowrocks on 2007-07-09
Anyone?

---

### Post by hardyn on 2007-07-09
are you using desktop effects? disable desktop effects and try again
add vga=791 to grub boot command.
its a fairly old machine, firmware update?

---

### Post by bobshowrocks on 2007-07-10
Well, by adding the vga-791 to the grub menu.lst that has changed the triangles into grey rectangles with black dots in the center of each.Does that tell anyone anything?

---

### Post by bobshowrocks on 2007-07-10
I've also tried update the BIOS, but the same thing is happening. I'm certain that its something in Ubuntu, sleep mode works fine in other OSes. can anyone help?

---

