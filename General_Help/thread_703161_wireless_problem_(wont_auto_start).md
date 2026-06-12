---
title: "wireless problem (wont auto start)"
date: 2008-02-21
forum: General Help
---

### Post by jareddlc on 2008-02-21
i have a compaq c714nr it is known to have a couple issues with drivers 
k first off my firmware for my wireless button is no under restricted drivers got it fixed with firmware download, my wireless works everytime i uninstall drivers and reinstall them. this is the command i copied and pasted, im a n00b so i need some help

sudo bash

rmmod bcm43xx

echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist

apt-get install ndisgtk ndiswrapper-utils-1.9 ndiswrapper-common

ndisgtk

then i installed my new drivers and works fine, but i need to repeat this each time i restart ubuntu? is there a workaround or could i possibly make a command that will automatically uninstall wireless driver and install same drivers again so that i wont have to manually do it?

any help would be great

---

### Post by patrickfromspain on 2008-02-21
maybe the module isn't autoloading? 

sudo bash
echo "ndiswrapper" >> /etc/modules

and restart to try.

---

### Post by stoodleysnow on 2008-02-21
You could also try installing a wifi-manager program if you haven't already, to see if it can pick up the card...?

---

