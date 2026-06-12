---
title: "Changing wireless mac keyboard hash key from alt+3"
date: 2014-01-22
forum: General Help
---

### Post by samwillc on 2014-01-22
Hi,

Firstly, I'd like to mention a bluetooth USB dongle that has worked for me out the box (so far) on a desktop pc (using elementaryos based on ubuntu 12.04). Although I've not tested with a restart, the device was found and pairing took a couple of minutes. Perhaps this will help someone else choose a bluetooth dongle:

[www.maplin.co.uk/p/bluetooth-40-usb-dongle-n81lj]("http://www.maplin.co.uk/pa/bluetooth-40-usb-dongle-n81lj")

All good so far. I am using a wireless mac keyboard (UK version) as I methodically make the possible switch to linux for good, just testing a few programs I usually use etc. Really enjoying the experience so far, so much freedom and the big terminal usage makes long winded crap so quick and easy once you get the hang of a few things.

However, on a mac keyboard, the most absurd combination is required to get a hash symbol which as you know is used ALL the time in sass (and for programming comments etc...). Right now I have to press alt+3 which is just stupid and awkward. On the mac, I had a custom keyboard layout file which remapped the hash to the key that has a plus/minus sign and a section symbol (the double 's' thing). It's just to the left of the '1' key directly under esc. Very handy to have the hash there seeing as I never use that key anyway.

Does anyone know how I do similar in ubuntu? Thanks for any advice.

Sam.

**EDIT**

And it would probably be handy to use the mac keyboard (UK) at the login screen too seeing as my password has a '@' sign in it! It reverts to pc layout so I have to press the " sign to get an @.

---

### Post by samwillc on 2014-01-22
Ok, so solved one problem thanks to:

[http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys](http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys)

[CODE]xmodmap -e "keycode 49 = numbersign"[CODE]

This makes that key a hash sign. Still got the login problem though with the swapped " and @.

Sam.

---

