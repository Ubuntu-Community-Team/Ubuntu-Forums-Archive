---
title: "Nvidia Graphic Driver GPU Fan Speed not working"
date: 2015-05-15
forum: General Help
---

### Post by squirrel2003 on 2015-05-15
I have Nvidia Driver 331.113 open source driver installed on my system and can't seem to get the fan speed setting to work.

I created an xorg.conf file and added the Coolbits 4 Option until then i had no fan speed regulation option in my graphical driver interface.

Now it exists but everytime i am trying to press apply after moving the stick it jumps right back to 40.

Also none of the driver settings like brightness and so on are saved after a reboot they all back to standard.

Would be happy if someone could help. 
Regards squirrel2003

---

### Post by efflandt on 2015-05-16
Recent coolbits support added back in (for overclock and manual fan control) requires at least a 337 nvidia driver. You can get newer driver packages than 331 from xorg-edgers ppa. I have a relatively new card with new Maxwell chip, which did not seem to work with nvidia-current in 14.04.1, nvidia-331 (or -updates) works, but I am using a newer version (currently **nvidia-349**) on my desktop to play around with overclocking (nvidia-331-updates from regular repos on my laptop which I don't OC).

But my GTX 750 Ti runs so efficiently at its forced 60 watt limit that its twin fans silently bump only a few percent automatically from their 33% base with temperature peak of 53-54 C doing graphic benchmarks at max overclock. So manual fan control is unnecessary for me.

Note that if you manually set a fan speed, it will hold that speed regardless of temperature until you clear that "Enable GPU Fan Settings" checkbox. So if that is checked, your fan(s) will NOT automatically speed up if your card gets hot.

---

### Post by squirrel2003 on 2015-05-16
Thanks with the 337 driver GPU fan speed controll works after entering the Coolbits line in the xorg.config.

The graphical interface of the driver is just a bit buggy it does not show the actual speed after changing it but one notices that the fan goes much louder or more silent when changing the value.

My only problem is that the speed will not go under 40 percent, is this normal for a gforce gtx 570?

---

