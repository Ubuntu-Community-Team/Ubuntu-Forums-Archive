---
title: "Bluetooth Audio issue"
date: 2024-09-01
forum: General Help
---

### Post by paul921 on 2024-09-01
Hi all...

Really at the end of my tether here - and posting here as a last resort.

Been running Ubuntu for about 4 months after switching from Windows - Ubuntu (at least for me) is great with handing complex programming tasks, and better than Windows. But the basics - it seems to struggle with. Things like MTP, and transferring files from my phone (but I can live with that for now) my main frustration now is with Bluetooth. 


Bluetooth works fine with my Bluetooth headphones. but acquired an ex car head unit - with Bluetooth support, and tried to set it up for use for home audio, - and I cannot get it to work with my laptop running Ubuntu. At first it would fail pairing. The head unit would simply say "pairing failed" I figured out that it had something to do with the authentication Blueman wasn't letting me enter the pin (1234) upon connection, and this was leading the connection to fail.. I switched from Blueman to Bluedevil, and was able to connect fine, but upon selecting the A2DP profile, I just get silence, I don't get track info sent from the laptop. It just says "unknown track" and silence, even selecting HFP as a profile did not work.  


Running Ubuntu 24.04 and have a QCA9377 card. 

I have spent hours working with this today - and nothing...

Connectivity is fine between the radio and my cell phone. 


My gut tells me that laptop is probably sending a sample rate or something that the radio is unfamiliar with, and I get no sound. Or it's using a too late, or too early version of A2DP. 

If someone can please assist it would be most appreciated. 

Thanks

---

### Post by hifron on 2024-09-01
Try some help from [this]("https://discourse.ubuntu.com/c/ubuntu-core-docs/bluez-docs/70") and if successful, you could make a [tutorial]("https://discourse.ubuntu.com/c/tutorials/34"), but maybe there is driver issue, github is full of them on Linux.

---

