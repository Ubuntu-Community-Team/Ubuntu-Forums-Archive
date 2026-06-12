---
title: "What's the best way to know what USB WiFi adapter to buy that will work?"
date: 2017-06-18
forum: General Help
---

### Post by ahawkua on 2017-06-18
What's the best way to know what USB WiFi adapter to buy that will work?

---

### Post by him610 on 2017-06-18
hello ahawkua,,

What you are doing is actually the fun part of resolving an issue by improving or re-engineering your system. I usually go through a similar exercise at least monthly.

Follow the posts over in the Networking & Wireless forum [https://ubuntuforums.org/forumdisplay.php?f=336]("https://ubuntuforums.org/forumdisplay.php?f=336")
You may discover which  wireless usb adapters to avoid just from how many issues have been resolved for various adapters.

You might consider defining your requirements more completely -
What is your budget?
What is your wireless router capable of? 
How far away is your wireless router from your preferred location? Are there any intervening walls, metal ductwork, etc?
What kind of broadband connection (fios, cable, dialup) do you have?
What connection speed is your best and worst case scenario?
Do you want to buy for the future?  

You can always go to Amazon or Newegg to glean some information from reading reviews of their best selling, or highest rated scores while paying particular if any of the reviewers were using a Linux distribution.

I can definitely recommend a couple of older, inexpensive wireless usb adapters that I occasionally use without any issues whatsoever. Your mileage may vary though. 
TP-Link TL-822N [https://www.newegg.com/Product/Product.aspx?Item=N82E16833704053]("https://www.newegg.com/Product/Product.aspx?Item=N82E16833704053")

Rosewill RNX-180BE [https://www.newegg.com/Product/Product.aspx?Item=N82E16833166056]("https://www.newegg.com/Product/Product.aspx?Item=N82E16833166056") (Newegg appears to be out of stock on this model, but there are similar models in stock)

Good luck,

---

### Post by SeijiSensei on 2017-06-19
Support for "N" adapters is pretty solid in Linux, but adapters that can work with the "AC" standard are not yet well supported.  My TP-Link WN722N ([https://www.newegg.com/Product/Product.aspx?Item=9SIA3AR5N37432](https://www.newegg.com/Product/Product.aspx?Item=9SIA3AR5N37432)) worked out of the box.  When I upgraded to an AC1200 adapter ([https://www.newegg.com/Product/Product.aspx?Item=N82E16833704364](https://www.newegg.com/Product/Product.aspx?Item=N82E16833704364)), I had to compile the driver myself from source code.  The newest Ubuntu kernels have better support for these devices, but on my 14.04 system I had to [compile the driver]("https://ubuntuforums.org/showthread.php?t=2363533&p=13655727&viewfull=1#post13655727").

If your wifi router doesn't support the AC standard, then I'd go with a cheap N device like the TP-Link items mentioned so far.  I upgraded my router to this AC 1750 device: [https://www.newegg.com/Product/Product.aspx?Item=N82E16833704177](https://www.newegg.com/Product/Product.aspx?Item=N82E16833704177)

---

### Post by efflandt on 2017-06-19
Your best bet is to get one that says on the package that it works with Linux. Even if that lists an old kernel version, newer kernels should support it. Or at least if it mentions Windows and Mac, you are closer than one that only mentions Windows. When I was looking for one for a Raspberry Pi (which runs a special Debian version) at Fry's Electonics I got a Sabrent USB WiFi which specifically mentioned Linux on its package (a 2.6 kernel I think) and it worked fine.

---

