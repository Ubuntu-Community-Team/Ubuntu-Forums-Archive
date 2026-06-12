---
title: "Computer Keeps Freezing"
date: 2015-09-22
forum: General Help
---

### Post by alexa3 on 2015-09-22
For quite awhile, this computer has been freezing. How do I find the cause?
I have this problem with my other computers, including another custom built desktop, and a laptop. This computer seems to have it happening the most.

Also, I think since buying the SSD, it started also freezing in a another way. Like if I click Firefox, the icon will flash but not open, if I click on restart or shut down, the message will disappear but the computer won't do anything. I'm not sure if the other computer have that problem, but I definitely notice it on this one.

My Full Specs:
Power Supply: Cooler Master Extreme2 625
Motherboard: ASUS Z87-K Motherboard
Processor: Intel Core i5-4670K CPU @3.40GHz x4
RAM: Kingston HyperX 8GB DDR3 x1
HDD/SSD: 1) 120GB SSD Silicon Power S60 with Ubuntu 12.04 (64-Bit) | 2) Western Digital 2TB Caviar Black (64MB/7200RPM) (No OS, just files)
Monitor: SAMSUNG Smart SmartTV 46" 1080p connected via "Rock Candy" Pink HDMI cable.
Keyboard/Mice: Wireless Logitech K360 Combo
Linksys Wireless G PCI Network Adapter

I hope that this helps.

---

### Post by alexa3 on 2015-09-22
My other desktop started acting up too. I restarted it becuase it stopped connecting to the Internet. I'm having a weird issue with downloading a torrent, and after I restarted the computer, it said that it couldn't find the source and to make sure that the drive was connected, something like that.

I think I should mention that last week, Firefox kept crashing imeediately upon opening. I deleted the config folder and s tarted new. It started working fine the later.
Right now, the Internet has stopped and "nothing" will work right... Wont shut down properly, programs take awhile to open. I started about 20 minutes ago. Not just the Internet.

My Full Specs:
Power Supply: Cooler Master Extreme2 525
Motherboard: ASUS B85M
Processor: Intel Pentium @3.20GHz
RAM: Crucial 8GB DDR3 1600 x1
HDD/SSD: 1) 120GB SSD Silicon Power S60 with Ubuntu 12.04 (64-Bit) | 2) Hitachi 750GB (32MB/7200RPM) with Windows 10.
Monitor: ASUS VS228H@1920x1080 connected via "Rock Candy" Pink HDMI cable.
Keyboard/Mice: Wireless Logitech K360 Combo/Mouse: Logitech M325
Realtek RTL8187B Wireless 802.11g 54Mbps USB adapter

I was posting this on my laptop, when it started messing up too. My laptop is a Toshiba Satellite L70D-A
It has same specs as it shipped with, except it runs Ubuntu 12.04 (64-Bit) and has a 120GB SSD (Silicon Power S60).

I'm on one of my Dad's office which seems to be running good for now. It has the same SSD and OS.

---

### Post by Bucky Ball on 2015-09-23
If all the machines are suddenly starting to act up and it starts while you're on the net then gets worse ... what websites have you been visiting lately and have you opened any emails from unknown sources? This may not be specific to Ubuntu, particularly if it is happening on a number of machine. This spells a hack. It would be impossible for all your Ubuntu machines to suddenly start having the same hardware issues simultaneously (or a gazillion to one coincidence).

Have you installed manually the same third-party PPA on _all_ the machines?

---

### Post by tgalati4 on 2015-09-23
It could be a failing power supply on the router.  Try rebooting the router and any modems.  Check the voltages of their power supplies with a voltmeter.  Since several computers are having problems, try to isolate them.  Disconnect one from the internet, and spend some time on it alone.  You can really only troubleshoot one at a time anyway.

Open a terminal and run top to see what is going on:

```
top
```

"q" to quit.  Look at the processes eating up CPU time.  Look at your RAM.  Is it full? Is swap being used? Look at DiskIO Waits (wa) and see if that is more than a few percent.

Ditch the pink hdmi cable.  Just because.

---

### Post by alexa3 on 2015-09-23
The computers seem to be working better now, opposed to last night. On Desktop one, still a problem with the Internet and the torrent showing not available source.
We've been having some weird issues with electronics in this house for awhile. Sometimes, things go haywire but only for short while.

It's my desktops that act up the most, Desktop 2 being the worst as it keeps freezing.
Is there something I can check in the log to see what caused it to freeze?

I haven't been visiting any unknown websites, and I have a few ppas installed on all machines. Here is a list:
[http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu)
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu)
[http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu)
[http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/)
[http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu)
[http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/)
[http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu)
[http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu)
[http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu)
[http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu](http://ppa.launchpad.net/indicator-brightness/ppa/ubuntu)
[http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu](http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu)

I'll use it without the Internet for awhile and see if anything happens.

---

