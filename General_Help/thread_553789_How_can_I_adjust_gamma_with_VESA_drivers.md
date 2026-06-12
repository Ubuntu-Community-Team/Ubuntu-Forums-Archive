---
title: "How can I adjust gamma with VESA drivers?"
date: 2007-09-18
forum: General Help
---

### Post by ropers on 2007-09-18
Hi, 
I'm trying to adjust gamma / correct gamma in Ubuntu 7.04.
I am using the VESA video drivers.
I have tried "sudo xgamma -gamma 1.700", but that doesn't work; not even if I restart the X Window server afterwards (pkill -HUP gdm). I have also tried putting a Gamma option into the Monitor section of xorg.conf, to no avail.

I have googled, but all I seem to be able to find is instructions to adjust gamma with other video drivers, not with VESA drivers.

Can anyone help?

---

### Post by ropers on 2007-09-18
After some extensive further googling it seems to me as if maybe the VESA driver doesn't support adjusting gamma. I need to find out if this is indeed the case, or if I just haven't found the solution yet. 

If there are people out there who **know for definite** that gamma correction is unimplemented with the VESA driver, I would be really grateful about a quick reply, because even knowing that a solution doesn't exist would help me.

---

