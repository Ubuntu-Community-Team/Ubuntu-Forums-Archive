---
title: "Need compiler for Lubuntu on a 32-bit machine."
date: 2014-07-31
forum: General Help
---

### Post by kameronshrum on 2014-07-31
I am learning about computers and programming, this is my first post in the forums as an Ubuntu user. I have Ubuntu 14.04 on my laptop. I recently received as a gift an old dell desktop that sported windows xp. I have just installed Lubuntu on it. It's a 32-bit machine. The desktop is not connected to the internet. I have a modem to connect to but it's about 20 feet away and it looks the only way to connect it would be to buy a long ethernet cable or to buy a device to connect to the desktop tower to wirelessly receive the signal. Earlier I attempted to download the GCC compiler on my laptop (which is connected to the internet wirelessly), save the download on a USB drive and then transfer to the desktop. The problem was that I had download a 64 bit compiler and when I transferred it to the 32-bit desktop, it gave me an error. What should I do? Thank you for reading.

---

### Post by monkeybrain20122 on 2014-07-31
gcc should already be installed. As for your desktop, either get a cable or buy a cheap usb wifi card.

---

### Post by Impavidus on 2014-07-31
synaptic can create a download script. Use synaptic on the Lubuntu box to select the packages you want to install, have it create a download script and store the script on a usb drive. Then move to the other computer, run the download script and the packages will be stored on the usb drive. Move back and synaptic will be able to install the packages from the usb drive. It's all quite straight forward. I'm not sure about refreshing the package lists, but I guess it can be done too.

Getting a network connection would be easier though. I use a 15m cable from my desk to the router.

---

