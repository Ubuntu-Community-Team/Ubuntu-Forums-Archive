---
title: "[SOLVED] Bootchart Advise"
date: 2008-06-11
forum: General Help
---

### Post by dicecca112 on 2008-06-11
Could I get some help with optimizing my boot.  I have an SSD in this system and its not booting as fast as it should.  

Image is attached and specs are below

Dell 1520
NVIDIA 8400GS
Supertalent 60GB SataII SSD
Intel 3945abg Wireless
2GB Memory

What can't be removed
- Wireless 
- Vmware Daemons

---

### Post by sdennie on 2008-06-11
I think you forgot to attach the picture.  Also can you be more specific on "as fast as it should"?  The boot process uses something called readahead which is designed to read much of the needed boot files into memory before they are needed.  This likely puts a regular disk more or less on par with an SSD.

---

### Post by dicecca112 on 2008-06-11
> **vor said:**
> I think you forgot to attach the picture.  Also can you be more specific on "as fast as it should"?  The boot process uses something called readahead which is designed to read much of the needed boot files into memory before they are needed.  This likely puts a regular disk more or less on par with an SSD.

Image is up, where looking at 63secs, were I've always had it under 40s with regular HDDs.  With the review I wrote for this, it was around 28s for Windows XP.  My experience with Ubuntu has always been since 6.06 that it booted way faster.

---

### Post by sdennie on 2008-06-11
63 seconds is excessive.  If you are coming from an upgrade, it's possible that you have a stale ipw3945 udev rule and the switch to iwl3945 is causing a huge pause for the udev phase of the boot.  Check the file /etc/udev/rules.d/70-persistent-net.rules and see if there is a comment about ipw3945 (NOTE: ipw and not iwl).  If there is, comment out that rule.

---

### Post by dicecca112 on 2008-06-11
> **vor said:**
> 63 seconds is excessive.  If you are coming from an upgrade, it's possible that you have a stale ipw3945 udev rule and the switch to iwl3945 is causing a huge pause for the udev phase of the boot.  Check the file /etc/udev/rules.d/70-persistent-net.rules and see if there is a comment about ipw3945 (NOTE: ipw and not iwl).  If there is, comment out that rule.


No upgrade here, only fresh formats then installs.  Don't trust the upgrade function, seen too many issues here

no IPW only iwl and b44

> # PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:b9:7e:b5:75", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:77:e8:63:9f", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

---

### Post by sdennie on 2008-06-11
Did you recently install the SSD?  If so, were any of your previous partitions on your old disk auto-mounted with udev rules?  It really seems like there is a huge pause for udev (though, I've never tried to read one of these so, I'm not positive).

---

### Post by dicecca112 on 2008-06-11
> **vor said:**
> Did you recently install the SSD?  If so, were any of your previous partitions on your old disk auto-mounted with udev rules?  It really seems like there is a huge pause for udev (though, I've never tried to read one of these so, I'm not positive).


Recent install yes, but the drive was formatted so no previous partitions on it.  Just Ubuntu.

---

### Post by sdennie on 2008-06-11
I notice that you are using a pre-release version of the -rt kernel.  How did you install it?  It's possible that it's missing some modules you need for the boot process (sudo apt-get install linux-rt should get you everything).  Does the same thing happen if you use a stock Hardy kernel?

---

### Post by dicecca112 on 2008-06-11
> **vor said:**
> I notice that you are using a pre-release version of the -rt kernel.  How did you install it?  It's possible that it's missing some modules you need for the boot process (sudo apt-get install linux-rt should get you everything).  Does the same thing happen if you use a stock Hardy kernel?


It was the RT kernel, I don't even know why I installed that.  But were down to a little over 20s.  

Thanks for that.  I don't think I can improve on 20s

---

