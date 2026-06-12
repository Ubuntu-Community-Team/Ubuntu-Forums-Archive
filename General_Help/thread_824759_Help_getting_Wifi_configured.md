---
title: "Help getting Wifi configured"
date: 2008-06-10
forum: General Help
---

### Post by squeakysystem on 2008-06-10
Hi,

Ubuntu 8.04 LTS Desktop freshly installed on a x86 machine. I want to set up a web/file server, configured to start up Apache and Samba automatically on boot.

Unfortunately, Ubuntu has terrible issues with both the onboard graphics and Buffalo WLI2-PCI-G54S wireless card, neither of which have worked without hours and hours of twiddling. I'm new to Linux and due to these configuration problems, I decided to install the Desktop version of Ubuntu so that I could have X to help poke around and get the machine configured properly. Due to support issues with the VIA P4M900 chipset, that, too, was a huge hassle, and finally I had to buy a separate graphics card just to get a working GUI. At this point, I am still trying to get the wifi card going.

Since Ubuntu is incapable of using the card "out of the box", I have followed various instructions for ndiswrapper, which uses the Windows drivers. The problem is that it only seems to work after X is running and I am logged in. I've got the wireless working okay inside X, but for a headless server, obviously it is not practical to connect a monitor and keyboard to login every time the machine needs to reboot. If the wifi is really working properly, I don't see why I should need to log in to get basic networking services running. Also, I don't want the overhead of X running at all times. Ultimately, I want to disable gdm on runlevel 2, but leave it on runlevel 3 so that I can start X on demand.

For the moment, though, the wifi card doesn't work unless I start X.

Observations:

If I type "ndiswrapper -l", I get:

	netg54s : driver installed
		device (14E4:4318) present (alternate driver: ssb)

This suggests that the driver is correctly installed, though I am suspicious about the "alternate driver: ssb". The ndiswrapper documentation suggests that I should try to unload the alternative driver using "rmmod ssb" or "modprobe -r ssb" but neither seem to have any effect. The ndiswrapper documentation is too vague and, sorry, poorly written to be helpful here.

If I type "dmesg | grep ndiswrapper", I get:

	ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
	ndiswrapper: driver netg54s (BUFFALO, INC.,11/01/2005, 3.104.64.52) loaded
	ndiswrapper: using IRQ 23
	usbcore: registered new interface driver ndiswrapper

Again, the bit about "usbcore" looks sort of suspicious, but I don't know if that's an issue or not. I've tried a bunch of different things from a bunch of different pages on the Internet, but nothing really seems to work.

Both "ifconfig" and "iwconfig" find wlan0, but they report that 0 packets have been transferred, which seems wrong to me.

I've tried "sudo ifconfig wlan0 up" to no avail.

The file /etc/modules has "ndiswrapper" as the last line.

The file /etc/modprobe.d/blacklist has the following lines at the end:

	blacklist bcm43xx
	blacklist b43
	blacklist b43legacy
	blacklist ssb

The installation and troubleshooting information I've found doesn't seem to get me anywhere, and I don't know what else to try. It seems like it just shouldn't be this complicated.

Any suggestions?

N. C.

---

### Post by squeakysystem on 2008-06-12
I've spent another day trying to figure that out.

I must say that I'm now totally unimpressed with Ubuntu. What a freaking mess.

It should not be so difficult to get a wireless card going.

If I can't figure this out in another 2 or 3 hours, then I guess it's back to Windows.

What an utter disappointment.

---

