---
title: "Video Card in Laptop help PLEEESE!"
date: 2008-06-19
forum: General Help
---

### Post by waapwoop1 on 2008-06-19
My laptop, according to specs i found in the manual, has an ATI Mobility Radeon 7500 4X AGP graphics controller with 32 MB DDR SDRAM.

I found this [http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500)

but i don't know what to do with it,  i did "sudo gedit /etc/xll/xorg.conf'  ad it came up with a blank file.

i am pretty new to this btw. I need help please :) i am running 8.04

---

### Post by issih on 2008-06-19
You are on the right track, I suspect you have just made a typing error:

you need to edit /etc/X11/xorg.conf.

Your line was perfect except I think you did Xwith two letter l's after it not x with two ones after it.

To be honest, its easiest to use tab completion to ensure you find the right file.

Make sure you backup your xorg.conf file first, and then replace the device section in yours with the one from that web page, and sdd the Extensions and DRI sections if they are not already present.

I'd leave the server layout section alone.

Hope that helps

---

### Post by waapwoop1 on 2008-06-19
I tried two 1s and still a blank file

---

### Post by waapwoop1 on 2008-06-19
I also tried envyng, but it did not recognise my card.

the screen works ok, but i can't use compiz, so i'm sure the driver isn't working for 3d.

---

### Post by ettercap on 2008-06-19
hey there
go to system>administration>hardware drivers
ur graphic will be detected there
enable it
and download the required driver

even i got a blank file wen i tried ....i hav nvidia 8400mgs

hope this helps

---

### Post by waapwoop1 on 2008-06-19
Ok, capital X helps.

---

### Post by waapwoop1 on 2008-06-19
> **waapwoop1 said:**
> Ok, capital X helps.

> **ettercap said:**
> hey there
go to system>administration>hardware drivers
ur graphic will be detected there
enable it
and download the required driver

even i got a blank file wen i tried ....i hav nvidia 8400mgs

hope this helps


It is not detected in there.

---

### Post by waapwoop1 on 2008-06-19
> **waapwoop1 said:**
> My laptop, according to specs i found in the manual, has an ATI Mobility Radeon 7500 4X AGP graphics controller with 32 MB DDR SDRAM.

I found this [http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500)



I followed these instructions... is there anything else i need to do, everything is exactly the same even after i edited the xorg.conf as this guy said.

---

### Post by phidia on 2008-06-19
What did you edit with and did you use sudo? Maybe you want to post your /etc/X11/xorg.conf not necessarily the whole file but from the device section down.

---

### Post by waapwoop1 on 2008-06-19
Ok, thanks everyone... i also hade to install xserver-xgl and it worked... the thing only has 32mb graphics card, so i had to turn the graphics options off anyway.... its way too slow.

---

