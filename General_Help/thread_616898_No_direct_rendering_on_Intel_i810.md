---
title: "No direct rendering on Intel i810"
date: 2007-11-18
forum: General Help
---

### Post by Z_o-s-o on 2007-11-18
Hey I'm having some trouble getting direct rendering enabled on an Intel i810 chipset.

Specs are:

500mhz Celeron
512mb ram
80 gig HDD
Integrated sound
i810 graphics

I'm not sure what I'm missing. The event logs look clean, and Ive done a fresh install.  None of the suggestions Ive found have done it for me (16 bit color, at least 16 megs of Vram).

Any help is appreciated!

- Z_o-s-o

---

### Post by atlfalcons866 on 2007-11-18
you need to have the color bit on 16 bit.

---

### Post by Z_o-s-o on 2007-11-18
I've got it set in 16bit color with 16mb of Vram, and direct rendering is still not enabled.

---

### Post by atlfalcons866 on 2007-11-18
do
glxinfo | grep render

---

### Post by Z_o-s-o on 2007-11-18
Well the first time I did glxinfo | grep render it said no.

I reinstalled the i810 driver package, and reconfigured the display through "Screen and graphics" or whatever its called.

Now glxinfo | grep render shows:

Direct Rendering: Yes

and something about mesa string.

The display is still horribly choppy at 1024X768 with 16bit color, and videos are bad as well.

---

### Post by atlfalcons866 on 2007-11-19
well you do have direct rendering enabled. How old is your monitor?

---

### Post by Craigus on 2007-11-19
have you tried using the newer intel driver instead of the i810 one?

> 	Driver		"intel"

---

