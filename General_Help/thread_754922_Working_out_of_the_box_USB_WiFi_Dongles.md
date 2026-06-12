---
title: "Working out of the box USB WiFi Dongles?"
date: 2008-04-14
forum: General Help
---

### Post by Wally_dog on 2008-04-14
Yeap, like the title says, I'm looking for a USB WiFi Dongle that will work "out-of-the-box" with an Ubuntu 7.10 installation from Dell. My dad is already a little cautious about me buying a desktop with Linux on it, so I'd like to have everything known to work right when I use it. I found this website "https://www.fsf.org/resources/hw/net/wireless/cards.html" and they recommended this: "Linksys WUSB54G USB 2.0 802.11g/b 54Mbps". According to them, it is fully supported in Linux because it uses a "RT2500/RT2400" chipset. If anyone can confirm this, or suggest a better product that will work out of the box (it needs to be a USB WiFi Dongle, not a PCI card), that would be great :)

Wally

---

### Post by ibutho on 2008-04-14
I've had good luck with ralink (rt2xxx) based cards and usb dongles. Ubuntu (and most Linux distros for that matter) support them out of the box. Most Edimax branded 802.11g wireless devices use ralink chipsets, so check if they are available in any of your local stores or online shops.

---

### Post by mehtdosa11 on 2008-04-14
hi,i am only a newbie myself, but that should work, because the rt or ralink chipset should be immediately recognised by your system.i believe the rt chipsets work in most linux distros.

i have a rt2500 chip in a comtrend pcmia wireless card in my old acer laptop that runs linuxmint, and that works also with simply mepis/puppy that i have tried. 

as soon as you boot up it works straight away, no drivers to load or anything!!
 [or it does for me!!]

---

### Post by Wally_dog on 2008-04-14
Wow, thanks for the quick response guys! I feel much better now knowing it will work. Are the drivers packaged with Ubuntu so I won't need to install any? A website that offered drivers (non-official Linksys drivers) offered 2400 and 2500 drivers, but they were for PCI/PCIA, so I don't know if those work with a USB Dongle using 2400/2500. Well, thanks for the quick and to the point responses :)

Wally

---

### Post by ibutho on 2008-04-15
The drivers are included in most Linux distros (Ubuntu included), so you don't have to install them yourself. I have a built in ralink rt73 (also known as rt2573) on my laptop and it just worked out of the box with Ubuntu 8.04 pre releases.

---

