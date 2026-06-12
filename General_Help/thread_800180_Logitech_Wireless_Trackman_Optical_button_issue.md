---
title: "Logitech Wireless Trackman Optical button issue"
date: 2008-05-19
forum: General Help
---

### Post by FokkerCharlie on 2008-05-19
Hi All

I wonder if anyone can point me in the right direction? I have a Logitech Trackman Wireless, which worked out of the box in Hardy, with the following exception:

The 'scroll up' button (not moving the wheel, the button above it) scrolls up in Firefox and ALSO causes the browser to go back a page.

In other nautilus, the scroll up button works as expected, up until I installed xbindkeys to get fwb/back buttons working there.  It is also an issue in XP running under VirtualBox, but not when I boot natively into Vista- so it looks like a Gnome/Ubuntu/X problem of some sort.

Another big clue- running xev returns two press/release events, on buttons 4 and 9, when I press the scroll button.  When using the wheel, only button 4 is returned.

My xorg.conf:
[http://www.pastebin.ca/1021083](http://www.pastebin.ca/1021083)

cat /proc/bus/input/devices:
[http://www.pastebin.ca/1021085](http://www.pastebin.ca/1021085)

Any ideas? I have tried all sorts of shenanigans, but am stuck with this irritation!  I have been fiddling with button mapping in xorg.conf, to no avail.  Am I barking up the wrong tree?

Thanks in advance
Charlie

---

### Post by FokkerCharlie on 2008-05-27
OK, I have solved the problem, with a little help from IdoMcFly

Here is the relevant part of my amended xorg.conf:

Section		"InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"Device"	"/dev/input/by-id/usb-Logitech_USB_Receiver-event-mouse"
EndSection

It now work perfectly with the evdev driver.  It seems to me that the "mouse" driver that I had previously been using could not cope with the number of buttons.

I hope that the automatic setup for a new installation can include evdev in future!

Cheerio
Charlie

---

