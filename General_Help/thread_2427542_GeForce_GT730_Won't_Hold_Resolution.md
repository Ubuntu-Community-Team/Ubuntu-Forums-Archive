---
title: "GeForce GT730 Won't Hold Resolution"
date: 2019-09-23
forum: General Help
---

### Post by farlander762 on 2019-09-23
I put a Zotac/NVIDIA GT 730 Graphics card in my computer.  

[https://www.zotac.com/us/product/graphics_card/geforce%C2%AE-gt-730-4gb-zone-edition]("https://www.zotac.com/us/product/graphics_card/geforce%C2%AE-gt-730-4gb-zone-edition")

It has 3 outputs, DVI, HDMI, and VGA.  All 3 monitors are the same model.  On alternating starts/restarts it will only go to 1600x900 on the VGA monitor only.  It should do 1080p on all three.  On one start it works properly, the next it limits the VGA monitor, the third it's back to working properly.  Occasionally, it gets out of sequence, not often though.  I can still send the card back for the next couple of days and am seriously considering that option.  There are two driver options, I've tried both.  I've also swapped monitors to see if it is a bad monitor (the VGA connected one is brand new).   

Any thoughts?

Thanks!

---

### Post by CatKiller on 2019-09-23
If you check your log (/var/log/Xorg.0.log) you'll probably find that on the times that your VGA monitor isn't being set to the correct resolution that it's struggling to retrieve the EDID information.

It could be an iffy connection, an iffy cable, or just one of those things. It is possible to give the information that would normally be passed through EDID manually, by specifying it in your xorg.conf.

---

### Post by mastablasta on 2019-09-24
in my case  (GT 730 on Kubuntu 18.04)- i have TV od DVI and monitor on VGA. At boot, picture always first goes to TV (even though the display is set to be off and VGA monitor is primary monitor). only then when the loading screen launches and then display manager get the picture on monitor. sometimes resolution is off but it correct itself before getting to desktop (i have auto login set).

in your case i would try to set EDID manually in xorg.conf. if that fails, replace the card. 

on the other PC when i first used this card i couldn't get display in any output. i would get bad resolution with nouveau and propper resolution but only a blinking cursor after installing the drivers (that was on 14.04). all in all bad drivers, the card is kind of ok now. at least with proprietary drivers installed. wish i had newer motherboard (PC) and newer card. i would probably use AMD again.

---

### Post by Autodave on 2019-09-24
Start by trying another VGA cable.  They fail often and cheaper ones don't always have the extra wire needed to relay the monitor's info to the video card.

---

