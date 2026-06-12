---
title: "serial-to-usb adapters that work in Ubuntu"
date: 2007-10-12
forum: General Help
---

### Post by Bartender on 2007-10-12
I was going to buy a Keyspan serial-to-usb adapter cable but Keyspan says that Ubuntu does not include their drivers.  Has anyone found a usb-to-serial adapter cable that "just works" in Ubuntu?  
I want to connect a US Robotics serial external modem.

Thanks!

---

### Post by SnackySmores on 2007-10-12
I used a targus converter, to monitor a microcontroller. no installation problems with that converter just plug & play. you might want to look in to that brand.

take care

---

### Post by Bartender on 2007-10-13
Thanks -

I ordered a Sabrent from newegg this morning.  
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812156008](http://www.newegg.com/Product/Product.aspx?Item=N82E16812156008)

The most recent reviewer claims it worked in Ub 7.4 without any difficulties.

---

### Post by Bartender on 2007-10-17
The Sabrent worked like a champ.  I plugged it into a USB port on the PC, plugged the serial end into a US Robotics 5686 external modem, and energized the modem before starting the PC.  Started the PC, asked GnomePPP to "Detect" the modem, it was recognized at /dev/ttyACMO.  Whoohoo

---

