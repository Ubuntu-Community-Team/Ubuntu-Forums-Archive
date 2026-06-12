---
title: "Ubuntu only starts through recovery mode followed by resume"
date: 2021-03-03
forum: General Help
---

### Post by vivekroy2991 on 2021-03-03
Hello everyone, 
I have a dual boot laptop (ASUS K501UW) running Windows 10 and Ubuntu 20.04. I cannot directly boot into Ubuntu. I have to go into recovery mode followed by resume to boot. 
If I do a journalctl -b I see some errors with respect to TPM and multiple times, 'firmware bug'. 

Any help would be greatly appreciated. 
Thanks!

---

### Post by blackbird34 on 2021-03-03
TPM as in Trusted Platform Module? Have you looked at the BIOS to see if there's anything misconfigured? Is there a list of which systems boot in which order, somewhere in the BIOS settings?

---

### Post by grahammechanical on 2021-03-03
> I cannot directly boot into Ubuntu. I have to go into recovery mode followed by resume to boot.

I am assuming that you see a Grub boot menu and select Advanced Options for Ubuntu. What happens when you try to boot Ubuntu directly? Booting from the recovery menu>Resume option loads Ubuntu with a low resolution open source video driver. May be your problem is with the video driver.

Open Software & Updates>Additional Drivers tab. If connected to the internet the system will search for proprietary video drivers. If a proprietary video driver is activated try de-activating it and use the high resolution open source video driver instead. Which will be loaded when you reboot. There maybe more than one proprietary video driver available. You could try with one of the alternative.

Knowing what your graphic hardware is would also be helpful.

Regards

---

### Post by vivekroy2991 on 2021-03-04
> **grahammechanical said:**
> I am assuming that you see a Grub boot menu and select Advanced Options for Ubuntu. What happens when you try to boot Ubuntu directly? Booting from the recovery menu>Resume option loads Ubuntu with a low resolution open source video driver. May be your problem is with the video driver.

When I try booting normally, I get a blank screen with no cursor or mouse pointer. Just a black screen staring at me.
> **grahammechanical said:**
> 
Open Software & Updates>Additional Drivers tab. If connected to the internet the system will search for proprietary video drivers. If a proprietary video driver is activated try de-activating it and use the high resolution open source video driver instead. Which will be loaded when you reboot. There maybe more than one proprietary video driver available. You could try with one of the alternative.

I am already using the open source one. I have blacklisted the nvidia graphics card driver by adding the following line to /etc/modprobe.d/blacklist.conf 
blacklist nvidiafb

> **grahammechanical said:**
> 
Knowing what your graphic hardware is would also be helpful.

Its a Nvidia 960M graphics card.

---

### Post by vivekroy2991 on 2021-03-04
> **blackbird34 said:**
> TPM as in Trusted Platform Module? Have you looked at the BIOS to see if there's anything misconfigured? Is there a list of which systems boot in which order, somewhere in the BIOS settings?

I checked the boot order. It seems to be fine or atleast I cannot see anything wrong with it.

---

### Post by vivekroy2991 on 2021-03-04
Update: I went and chose a proprietary driver and it worked! 
But I am surprised that it should given that I have still the blacklist nvidiafb line in /etc/modprobe.d/blacklist.conf

---

