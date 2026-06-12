---
title: "Disabling a device?"
date: 2007-02-19
forum: General Help
---

### Post by bazar on 2007-02-19
I'm new to Linux and I did a search before posting here on this subject. I have a laptop 
that comes with a wireless card that's a pain to configure so I'm going to switch to a D-link usb wireless adapter I can set up easier.





Rather than having go into my laptop and yank out the wireless card, is there a way I can "disable" it (like in the Windows device manager) so it doesn't clash with the new wireless adapter I want to use?  The Device Manager in Ubuntu doesn't let me do it

---

### Post by taurus on 2007-02-19
See if you can disable it in the BIOS.

---

### Post by bazar on 2007-02-19
> **taurus said:**
> See if you can disable it in the BIOS.


I just looked in the laptop bios settings which are sparse compared to what is in my
desktop box bios.   I didn't see a way to disable it there   
I just have to hope that the two devices don't clash with each other

---

### Post by t341 on 2007-02-19
> **bazar said:**
> I just looked in the laptop bios settings which are sparse compared to what is in my
desktop box bios.   I didn't see a way to disable it there   
I just have to hope that the two devices don't clash with each other

Turn off the wireless switch in the front panel

---

### Post by bazar on 2007-02-19
> **t341 said:**
> Turn off the wireless switch in the front panel


Even if I turn off the wireless switch on front of the laptop Ubuntu would still see the 
wireless adapter there probably and having two wireless adapters present might
cause problems even if one of them was not active.

I wish there was a way I could just "blacklist" the broadcom wireless card.

---

### Post by t341 on 2007-02-19
> **bazar said:**
> Even if I turn off the wireless switch on front of the laptop Ubuntu would still see the 
wireless adapter there probably and having two wireless adapters present might
cause problems even if one of them was not active.

I wish there was a way I could just "blacklist" the broadcom wireless card.

Why don't you try echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

---

### Post by bazar on 2007-02-19
> **t341 said:**
> Why don't you try echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist


That just gets rid of the driver module not the device itself.

How do you know what broadcom card I have anyway?

---

### Post by t341 on 2007-02-19
> **bazar said:**
> That just gets rid of the driver module not the device itself.

How do you know what broadcom card I have anyway?


I saw you post this question in alt.os.linux.ubuntu earlier

---

### Post by bazar on 2007-02-20
bump

Can anyone tell me how to disable a hardware device in Ubuntu?

---

