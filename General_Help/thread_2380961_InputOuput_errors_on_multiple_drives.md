---
title: "Input/Ouput errors on multiple drives"
date: 2017-12-24
forum: General Help
---

### Post by thompson-dayne on 2017-12-24
Hi All, go easy on me far from an expert.

For years been running an ubuntu media server. Recently upgraded hardware to a Ryzen using a fresh install of 16.04. Everything was working well but started getting input/output errors on a couple drives then refused to mount, both WD Red drives (not in raid). Updated motherboard bios and kernel but no effect. Updated to 17.10 just in case the new hardware needed the latest. No help and a third Red drive failed.

I installed a new WD Blue drive as I read somewhere it is possible to have hardware compatibility between a motherboard and Red drives, but in less than a week the Blue drive is not mounting and saying it cannot read superblock.

This is where I turn to people smarter than me for guidance ;)

Also not sure if related but usb backup drives unmount and remount randomly

General info:
Ryzen 1700
GA-AX370-K3 motherboard
32gb Corsair Vengence 2666 DDR4 ram
SSD drive for OS (never had any errors)
Ubuntu 17.10

Thanks

---

### Post by Autodave on 2017-12-24
Being more of a hardware than software guy, I would be looking at power supply issues first.

As for the superblock error, it could have happened while power supply was doing something weird or it could be a bad drive.  I would probably start by redoing the drive on another machine and checking its integrity if it seems to function properly afterwards. If you still cannot get past the superblock issue with it on another machine, then you have a bd drive. The next question would be why it went bad that quickly: either it was just bad or you power supply in the server killed it.

Usually when a PSU goes bad, it loses voltage output. But, you could have one where the voltage is spiking and thus killing the drive(s).

---

### Post by Autodave on 2017-12-24
How many drives are in this machine and what is the rating of the PSU?

---

### Post by thompson-dayne on 2017-12-24
Thanks Autodave.

5 standard drives and 1 SSD. PSU is 450w.

The drives have not changed in years, I just upgraded the motherboard, ram, and cpu. However I do like your idea of a failing PSU and will change it with another one I have to see if it makes any difference.

---

