---
title: "BOOT ERROR drm:intel_enable_lvds [i915] *ERROR* timed out waiting for panel to power"
date: 2018-04-26
forum: General Help
---

### Post by dherevo on 2018-04-26
Hi, I'm trying to install Lubuntu 16.04 on an old laptop (Vaio VPCW12J1E) but everytime when i'm trying to boot the USB Stick and select the option Try Lubuntu before install or install directly, it loads an i915 error.


I tried with a bootloader like Plop Boot manager but it's the same.


On the other hand the laptop has a Windows 7 installed and I'm thinking if its the MBR the problem and I will need to reset the hard drive with the system.

Thanks for the help.

[IMG]https://i.imgur.com/PT8VVFP.jpg[/IMG]

---

### Post by oldfred on 2018-04-26
You could try one of these, but I have not seen any boot parameters needed on older Intel. Some very new Intel have needed boot parameters. My middle aged systems have just worked.

 [http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)
 Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1

---

### Post by dherevo on 2018-07-02
> **oldfred said:**
> You could try one of these, but I have not seen any boot parameters needed on older Intel. Some very new Intel have needed boot parameters. My middle aged systems have just worked.

 [http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)
 Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1


I tried another system and I tried to boot Ubuntu with an external drive with a custom boot loader (Plop Boot manager) but the system didn't read the partition. I think this VAIO laptops are very problematic with the custom install, it's very frustrating.

---

### Post by dherevo on 2018-07-02
I'm thinking if i install an Ubuntu Server first and then the Lubuntu desktop inside the server is gonna work. This laptop it's full of problems when i'm trying to make something with him.

---

