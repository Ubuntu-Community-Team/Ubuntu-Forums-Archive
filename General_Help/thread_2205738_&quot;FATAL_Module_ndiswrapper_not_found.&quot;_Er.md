---
title: "&quot;FATAL: Module ndiswrapper not found.&quot; Error. Please help."
date: 2014-02-15
forum: General Help
---

### Post by jaxgamer1793 on 2014-02-15
I'm fairly new to Ubuntu and I'm getting sick of not being able to fix this error. I just want to use my wirelss adapter (Netgear WNDA3100). I have ndiswrapper installed through the ubuntu software centre, it works fine until I try to install the driver (from my usb drive) for my adapter. the full error says:

"Module could not be loaded. Error was:


FATAL: Module ndiswrapper not found.


Is the ndiswrapper module installed?"

I can't find anything useful online, I don't know if this OS just hates me or I'm bad at it being I'm new. I've tried following the first answer (suggestion #2) on this page, but I always get the error:

"tar (child): ndiswrapper.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now"

Any help would be greatly appreciated.
PC Specs:
Pentium 4 3ghz
1026mb DDR RAM
GeForce FX 5200
Ubuntu 12.04 LTS

---

### Post by ajgreeny on 2014-02-15
ndiswrapper in 12.04 is broken and the easiest way out is to compile it yourself. 
 **DONT PANIC** at this suggestion, just follow the instructions below.

COMPILE NDISWRAPPER.

Download source from sourceforge :-
[http://sourceforge.net/projects/ndiswrapper/files/latest/download?source=files](http://sourceforge.net/projects/ndiswrapper/files/latest/download?source=files)

Install these from repos:-
ndisgtk, ndiswrapper-common, ndiswrapper-dkms, ndiswrapper-source and ndiswrapper-utils-1.9
plus all dependencies.

Ensure you have installed the linux-header packages for your kernel version.

Extract the downloaded tar.gz file and cd to extracted ndiswrapper-1.59 folder

Run these three commands in order:-

sudo make
sudo make install
sudo modprobe ndiswrapper

Wireless connection should now be available, though you may need to re-install the netgear WNDA3100.inf file.

---

### Post by jaxgamer1793 on 2014-02-18
how do I compile ndiswrapper?

---

### Post by philip16 on 2014-02-18
I did this on my install still no wireless connection. Done everything I've found via Google and nothing.  I used the same usb wireless device a couple of years ago and had no issue.  Very frustrating.  I'm using a Trendnet 424UB usb network device.

---

### Post by monkeybrain20122 on 2014-02-18
I would just get a Linux compliant usb wireless adapter. They are quite cheap. ndiswrapper is sort of a hack from the old days and doesn't always work that well from what I heard.

---

### Post by philip16 on 2014-02-18
I tried a netgear usb wireless adapter I have (WG111) and same issue.  It shows up in the Wireless driver GUI and says it's present but I get no connection. still frustrating.

---

### Post by monkeybrain20122 on 2014-02-18
> **philip16 said:**
> I tried a netgear usb wireless adapter I have (WG111) and same issue.  It shows up in the Wireless driver GUI and says it's present but I get no connection. still frustrating.

Here is a thread about how to compile the Linux driver for this wifi adapter(without ndiswrapper)

[http://linuxforums.org.uk/ubuntu/netgear-wg111t/msg29572/#msg29572](http://linuxforums.org.uk/ubuntu/netgear-wg111t/msg29572/#msg29572) 

This may be out of date though, but all info I found about this card  on Google is pretty old and most of the tutorials about it involve ndiswrapper. So it seems that by some bad luck both your wifi adapters are Linux incompatible or semicompatibe if the tutorial above works (I bought two a while back without any prior research, one worked out of the box, the other worked out of the box in 13.04, and 12.04 only needed editing some config file)

---

