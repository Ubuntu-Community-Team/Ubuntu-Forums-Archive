---
title: "Razer Blade Laptop"
date: 2012-10-16
forum: General Help
---

### Post by scphan on 2012-10-16
Hello,

I was wondering if anybody knows anything about installing and running Ubuntu on one of the Razer Blade laptops.  I'm looking at buying one and wanted to know how compatible it is with Ubuntu 12+.

Here's a link to the product site:
[http://www.razerzone.com/gaming-systems/razer-blade]("http://www.razerzone.com/gaming-systems/razer-blade")

As you see it has that special touchpad that doubles as a 2nd screen.  Will it be recognized in Ubuntu as a 2nd monitor?

So far google hasn't turned up anything on the matter of this laptop and ubuntu running on it.

Thanks

---

### Post by s3gfault on 2013-01-31
Here are the few things I have learned in my attempt to install Linux Mint 13 on the 2nd gen Razer Blade (2012).

1) The software driving the caching SSD (Dataplex) munges the partition table.  Other operatings systems cannot read it.  Dataplex has to be uninstalled from windows before you will be able to install linux (if you want to keep the original two NTFS partitions (main and recovery)).

2)the nouveau driver hard locks the computer occasionally.  I'm pretty sure this is what was causing it because it happened most often when i was fiddling with the displays, but it also happened at other times, and eventually happened too often for the computer to be usable.

3) The trackpad works as a mouse, and the buttons work (left and right mouse buttons) but the 10 dynamic image buttons do not work of course.  The default image appears on the trackpad.

Other than these things I had no complaints.  Wireless and sleep worked, webcam worked, and it was fast, since i had Linux installed on the SSD (since it wasn't caching anything anymore).

UPDATE: Installed 12.10 today (2/2/13) on this computer and it hasn't locked up in about 5 hours, so pretty good so far.  Suspend and resume are working, and the volume buttons on the keyboard.  The Keyboard brightness buttons work, but the display brightness buttons don't.

UPDATE 2: 12.10 still hasn't crashed, but the trackpad gestures are not working.  I think it's not being detected as a trackpad, the configuration options are not present in the mouse settings.  I'm starting to look into this.

---

### Post by tr1sth3t on 2013-06-21
I'm running Ubuntu 13.04 on the first Razer Blade that was released. I have not been pleased at all. I have not had crashes, but the ole' lack of driver support for Linux in general is certainly my issue. For instance mouse gestures do not work. Sometimes the mouse and keyboard simply do not work when booted. It also seems to not register key hits on the keyboard (which is extremely annoying because it's intermitent). Then you really can't get the Nvidia graphics card to work like it should. I've tried many days to get nvidia proprietary drivers with bumblebee-nvidia to work and it failed. Also the HDMI doesn't work in Ubuntu.

When running Ubuntu on my Razer Blade laptop, I've simply got a laptop that can't handle any graphic intensive games with a really fast processor, a really fast hard drive, and a crappy keyboard and touch pad. Hopefully they'll see the value in making drivers for Ubuntu since Steam was realeased for Ubuntu and Alienware offering Ubuntu as an operating system.

P.S. I've had my laptop for a year and try once a month to see if I can get things to work properly by searching Google and asking in IRC about the issues, but I still have not had much luck.

---

### Post by meawoppl2 on 2014-02-25
Any updates to be had on this?  I am considering getting one.  Does wireless work.  gltests?

---

### Post by mastablasta on 2014-02-25
it seems these computers were made to only run windows and as such only have driver support for windows operating system.

ofcourse you could always write your own drivers in linux but who has time for that....

---

