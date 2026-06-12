---
title: "[SOLVED] Dell Inspiron 6000 - INtel PRO 2200 wireless"
date: 2007-08-06
forum: General Help
---

### Post by mykrob on 2007-08-06
Hey-

I have read that the Intel PRO 2200BG wireless should work out of the box. I just did a clean install of Kubuntu Feisty ona friend's Dell Inspiron 6000 series laptop, and the wifi is not working.it is apparently detected, though.. How do i make it work? When i pressthe wireless button, it turns on the Bluetooth instead of the wifi.

Thanks,
-myk

---

### Post by moore.bryan on 2007-08-06
*try using* *[wicd]("http://wicd.sourceforge.net/") for the network settings...*

---

### Post by mykrob on 2007-08-06
i can do that, but here's the deal.. In the terminal now, thedevice shows, but cannot detect any networks. I have two routers sitting less than one foot in front of the laptop. This says to me the device is definitely detected and possibly working, but not turned on.

SHould i go ahead with Wicd, or does something lese need to be done first?

Thanks,
-myk

PS - all updates have not been run yet.

---

### Post by strabes on 2007-08-06
That's strange because the kernel module ipw2200 should take care of that card no problem. Have you tried checking if that module is loaded?

---

### Post by moore.bryan on 2007-08-06
*make sure to have all your updates and try-out wicd... if it doesn't work and someone else suggests a good way to use network-manager, you can just uninstall and go with that.*

---

### Post by aysiu on 2007-08-06
I had issues with wireless in Kubuntu on my Inspiron 500m Dell laptop. But the IP 2200 works flawlessly out of the box with the same laptop using Ubuntu or Xubuntu.

---

### Post by mykrob on 2007-08-06
thanks. I have the repository for wicd loaded. I will runn all the updates, install wicd, reboot, andreport back. I will also check for the module..

*EDIT: The module ipw2200 is loaded.. I will report back soon.

---

### Post by mykrob on 2007-08-06
looks like it is working, just the correct lights are not lighting up.. Iturned the bluetooth back on, and now my wirelss networks are showing up...

Will report back again after updates,rebooting and testing with Network Manager.

Thanks,

---

### Post by mykrob on 2007-08-07
everything works fine, thanks for the help!

---

