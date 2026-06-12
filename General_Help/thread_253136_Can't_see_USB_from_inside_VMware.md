---
title: "Can't see USB from inside VMware"
date: 2006-09-07
forum: General Help
---

### Post by BoyGenius on 2006-09-07
I have windows XP running on Dapper through VMware.  Most of it works very well, but I can't seem to see my USB devices.  Well, specifically my iTunes phone, which usually works like an iPod; plug it in and iTunes starts up.   That's how it works on my regular version of windows anyway.  How can I make my VMware version of windows see the phone.

---

### Post by reacocard on 2006-09-07
Give your XP VM a virtual USB port, then tell vmware to connect the phone to that port.

---

### Post by BoyGenius on 2006-09-07
> **reacocard said:**
> Give your XP VM a virtual USB port, then tell vmware to connect the phone to that port.

Easy for you to say.  How exactly would I do that?

---

### Post by andy_cowman on 2006-09-08
yes how do you do that?! it may be exactly what i need to do to get my roadangel compact working. I can see it in VMPlayer XP but its doesnt function well enough for updating. 

Thanks

---

### Post by reacocard on 2006-09-08
> Easy for you to say. How exactly would I do that?
In vmware server, you open the VM, click 'Edit', then 'add' and choose USB. step through the wizard and your VM now has a USB port. Boot the VM, and under VM -> Removable devices there's a list of USB devices you can connect to the VM. That's it.

---

### Post by smoothcne on 2006-09-08
> **reacocard said:**
> In vmware server, you open the VM, click 'Edit', then 'add' and choose USB. step through the wizard and your VM now has a USB port. Boot the VM, and under VM -> Removable devices there's a list of USB devices you can connect to the VM. That's it.

I'm using the Player, with Win2k. I can plug in a USB drive, Dapper see's it fine, I can click on the device at the top of the Player window and it loads it perfect. THEN, I can remove it, plug in a Olympus DS4000 Digital Recorder that also works like a Removable Drive on Winblows, and it just sits there... never see's it. Anyone ever use one or seen this issue? I can't get it to work at all. 
Smooth

---

