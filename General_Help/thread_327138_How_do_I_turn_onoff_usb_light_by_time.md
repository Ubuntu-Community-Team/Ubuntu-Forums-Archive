---
title: "How do I turn on/off usb light by time?"
date: 2006-12-28
forum: General Help
---

### Post by mjrclark on 2006-12-28
I have a usb 'lava lamp,' and I am wondering if there is any software that would help turning it on/off at specific times (eg as a wake up thing, for very light sleepers).  Is there?

If not, is it possible to make one, one obstacle is if it is impossible to stop a usb port letting a device draw power (I read that lamps are likely not to contain any digital circuitry at all, just draw power). If this is a case, what sort of programming language would be required, and where could I find references for the usb-interfacing part/api/whatever for this language. (Only done vb <cower> before, but I would aim to start simple.)

 Failing that, any pointers to wonderful corners of the internet where I could find this info out?

---

### Post by mjrclark on 2006-12-29
Right, no responses. Frustrating. Looking at even more spuriously connected web sites, I still have no idea of an already written programme that would solve my problem....
The following is a link to the source for a programme that searches for blackberries and then sets their power level for USB.

[http://ovh.dl.sourceforge.net/sourceforge/barry/bcharge.cc](http://ovh.dl.sourceforge.net/sourceforge/barry/bcharge.cc)
I think it is in Java-
 My idea is to change the search for Blackberry manufacturer string to those with the usb  port manufacturer string, as this is what the port with the lamp attached looks like under usbview from;
sudo apt-get install usbview

**or** with similar output (though no nice names)
cat /dev/bus/usb/devices
Shows that the port has the same driver as all the other unattached ports ie drive=hub , so I could change the source to look for that.

BUT I have very little knowledge of how this is written, so I will be bumbling along, can anybody offer any help or advice?

Update
Reading through the java file, it does not work the way I thought it did, and merely tells the blackberry to change the power setting itself. This disappointment apart, it does reveal some interesting functions using "libusb", specifically; 
#include <usb.h>
#include <stdio.h>
#include <unistd.h>
Is that right? then the following line is using this;
dev->config[0].MaxPower < 250 
to read the property of whether the blackberry is on high power already as part of an if statement.
So... where can I find the other available 'functiony api call thingys' for libusb, or does somebody already know that there is no dev->config[0].Power = 500 type one (writeable)?

**Update 2**
[http://libusb.sourceforge.net/doc/functions.html](http://libusb.sourceforge.net/doc/functions.html)
That seems to be what I was looking for, but it does not contain the function I want. It does mention that it is out of date though... any offers on whether the newer version has what I want?
I do not expect the newer version to be of any help however. Any hints on alternatives?
I thought up a radical solution- not sure if it would work. Unload the usb modules from the kernel. Possibly out of my depth there, not going to attempt on my own.

---

### Post by mjrclark on 2006-12-30
Via the very useful irc help channel (the user harrisony1) and looking at several spec documents and api function lists, I have come to the conclusion that this is literally impossible through software. That is very frustrating- it shows these usb powered gizmos are completely pointless!

---

### Post by Ramses de Norre on 2006-12-30
I also don't think this is possible, as far as I know usb ports are always powered.

What you could do maybe when you aren't using other usb ports similarly is unloading the driver, it may (probably not though but you can try) stop the ports from being powered.

Just a thought for a very dirty way to obtain what you want.

---

### Post by fragos on 2006-12-30
The USB ports remain powered when the PC is turned off so that devices plugged into them can still charge.  Might I suggest that you use a surge suppressor power strip with a power switch.  That switch will cut all power to your PC.

---

### Post by mjrclark on 2007-01-01
Thank you for your suggestions. As for unloading the driver, I have not yet worked out how to do this. I did try forcing the usb-core kernel module to unload, but only got complaints of bieng in use. I do not think this is what you meant anyway.
The suggestion-of stopping power to the pc, would probably work. However, my pc is not very good at turning back on.

---

### Post by fragos on 2007-01-01
Depending how determined you are to this there is another option.  You could buy a cheap USB hub and put a power switch in it so you only turn off USB power.  PC stays powered up.

---

### Post by nexus_2006 on 2007-01-01
If you were really determined you could get another USB device containing logic circuits and a relay which you could program to use its relay to shut your other light off and on, that could at least be controlled by software, though it would be a hellatious project.

---

### Post by mjrclark on 2007-01-01
Again, thank you all for your suggestions. School is starting again, and I have exams and a birthday upcoming. This means I am probably going to beunable to tackle any of the projects you have so kindly outlined.

---

### Post by fragos on 2007-01-01
Happy Birthday and good luck with the upcoming school year.

---

### Post by nexus_2006 on 2007-01-01
I know how you feel, I start classes again in less than a week, and this semester is going to be a bear.

---

