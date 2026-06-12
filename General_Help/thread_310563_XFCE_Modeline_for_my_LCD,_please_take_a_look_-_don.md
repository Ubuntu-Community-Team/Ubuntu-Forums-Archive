---
title: "XFCE: Modeline for my LCD, please take a look - don't want to kill my LCD..."
date: 2006-12-01
forum: General Help
---

### Post by brjoon1021 on 2006-12-01
XFCE sets up my display incorrectly at 1024x768 or 1280 x something. So, to get the display of 1600x1200 - as it should be I run  "gtf 1600 1200 60 -v" to get a modeline. the resulting modeline is:

# 1600x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 160.96 MHz
  Modeline "1600x1200_60.00"  160.96  1600 1704 1880 2160  1200 1201 1204 1242  -HSync +Vsync

- what is the vertical frequency in there ?  I think that it is the "160.96". My monitor is a Viewsonic 20 inch LCD using the DVI connection. When I look at its specs on the Viewsonic site the vertical refresh rate of 160.96 (assuming that this is what the number from the modeline is - the V refresh rate) is too high for my monitor and pretty much any LCD, I think.

Here is the way the Viewsonic site details the refresh range:
 "VIDEO INPUT     Analog     RGB Analog (75 ohms, 0.7/1.0 Vp-p)
Digital    DVI-D (TMDS, 100 ohms, or analog capable)
Frequency    Fh: 30~92kHz, Fv: 50~85Hz
Sync    H/V separated, composite, sync-on-green (TTL)"

Isn't that saying that the monitor should run somewhere in the range of 50 to 85 Hz for the Vertical refresh rate and not 160.96 ?!?!?   The display looks good but I don't want to damage my monitor. I could use some advice, please.

Thanks
B.

---

### Post by yopnono on 2006-12-01
No it will run @ 60
160.96 is. 
21: [PIXEL FREQ]:160.963196
Don't know what this is. but I use modeline on my LCD @ 60 and my pixel freq is. (1280x1026@60)
21: [PIXEL FREQ]:108.883202

---

### Post by princemackenzie on 2006-12-01
brjoon,

Do you have the viewsonic VX2025WM?  I have that same 20" widescreen ViewSonic i think.

Mine runs fine, it will stay at 60.

---

### Post by brjoon1021 on 2006-12-03
It is a Viewsonic VP2000s

Thanks guys.

---

