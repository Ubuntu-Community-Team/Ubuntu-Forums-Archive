---
title: "No wireless found"
date: 2013-01-24
forum: General Help
---

### Post by LT83 on 2013-01-24
Hello all.  I'm stuck and can't get out (figuratively speaking).  Was having difficulty with WICD not finding any wireless networks.  Ran sudo ifconfig -a ; sudo ifconfig wlan0 up;  iwconfig wlan0 essid Eagle1;  iwlist wlan0 scan essid Eagle1; and so on.  All indications thru terminal window reflected a wireless signal being detected by my laptop, but WICD wasn't finding any wireless.  My ssid is not broadcasted, but WICD allows you to 'find a hidden network'.   Entering my ssid info, wicd still found nothing.

Reviewing other threads i saw that i could purge WICD thru the apt-get purge wicd* ; but when i attempted to do an apt-get install wicd, no luck.  Looking at another post, i saw reference to synaptic package mgr.  I found the wicd pkg, but of course i couldn't install because--I HAVE NO INTERNET CONNECTION.  Yes, it was a bonehead moment. :rolleyes:


I restarted my box and ethernet connection found.  I used synaptic package mgr to install wicd.  Still no wireless.
 
When i do an IWLIST SCAN i see my router with it's hidden beacon:  ESSID: "\x00\x00\x00……"
I then executed SUDO IWCONFIG WLAN0 SCAN ESSID EAGLE1, and i see my ssid and associated parameters: encryption key on, bit rates, freq, etc.
But when i go to the wicd n/w mgr, it tells me there no wireless networks found. 

I ran DMESG |GREP WLAN0 and saw the following:  ADDRCONF (NETDEV_UP), wlan0: link is not ready.  Then DMESG |GREP IWL3945, and got this:  detected intel wireless wifi link 3945abg.  Just before submitting post, i saw the "Check if already posted" button.  Reviewing some other threads, i ran LSHW -C NETWORK and saw my PRO/Wireless 3945G info, then i ran RFKILL LIST ALL and saw nothing is blocked.  

I'm at a loss and need help?  I'm using Backtrack 5 (Ubunto 10.04).

---

