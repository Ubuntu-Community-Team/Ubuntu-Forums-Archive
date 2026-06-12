---
title: "GUI not loading with 8800GT.  Drivers are installed, weird"
date: 2007-12-02
forum: General Help
---

### Post by Thomme on 2007-12-02
So, I'm running Ubuntu 7.10 with Mac 4 Lin (sans Beryl/Compiz and the startup managers) with a Q6600, 8800GT and 2 gigs of ram on an Intel DG33TL mobo.  Now, this is actually the second time I've run into this issue, and it only arised when I'm trying to configure my wireless card.

So, what ends up happening, is after about 2 days of Ubuntu running fine on the 8800GT with Mac 4 Lin v.3 on it, I tried to configure my broadcom usb adapter and when I rebooted linux to see if it worked, it hung up after the loading bar on the command, "Running local boot scripts (/etc/rc.local).......................................[ok]" and then I can use ctrl+alt+F2 to get a CMD prompt.  If I restart the system using the Intel GMA965, it boots up fine.  But, with the 8800GT, it just hangs up, like the drivers aren't there.  So, I reinstall the drivers, and I get nothing.

Next, I tried reinstalling the OS itself, and it just didn't work until I actually deleted the partitions and repartitioned my HDD.  So, I had linux working for today with the 8800GT again.  So, I loaded up Mac 4 Lin again, got my Linux looking pretty cool.  And I bought a new WLAN card (a Dynex with Atheros chipset) and tried to get it working with madwifi, but it didn't for some reason... it was strange.  So, I turned off the computer and went to the store and when I came back and booted it, it hung up at exactly the same time.  What was weird was that before shutting down the computer, I didn't change any settings or anything, but once I booted it up into Linux: the GUI wouldn't boot!

I need some serious help with this one.

---

### Post by Thomme on 2007-12-03
Problem seems to have gone away on it's own.  I rebuilt the Xorg file and got it working in low res, then I reinstalled the 800GT drivers and it went back to nothing but a CMD prompt.  After two or three roboots it just worked and hasn't done it sinces about 11:00 last night.  Wierd...

---

