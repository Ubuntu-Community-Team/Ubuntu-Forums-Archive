---
title: "hdmi monitor does not wake up after suspend"
date: 2018-01-25
forum: General Help
---

### Post by hodgsonsam78-u on 2018-01-25
Hi,

This appears to be specific to hdmi, I have a laptop with 2 external monitors and whichever one is using the hdmi port does not wake up when I come out of power saving mode.  If I open display settings, disable the non-working monitor then re-enable it comes back to life.  I was running 16.04 but have just upgraded to 17.10 and seeing exactly the same issue.

Dell website advises I have the following integrated vga card:

[COLOR=#444444][FONT=Roboto-Regular]Intel HD Graphics 530 (quad core)[/FONT][/COLOR][COLOR=#444444][FONT=Roboto-Regular]AMD Radeon R7M370

lspci shows:

00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06)

There is a propitiatory driver on the amd site however it only confirms compatibility upto ubuntu 15.10.

Anyone experienced the same thing or know of any fix?

Cheers

Sam[/FONT][/COLOR]

---

