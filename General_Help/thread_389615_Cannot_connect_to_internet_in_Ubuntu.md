---
title: "Cannot connect to internet in Ubuntu"
date: 2007-03-20
forum: General Help
---

### Post by billdotson on 2007-03-20
My motherboard and PSU failed a couple weeks ago and I got it put back together today.  I booted it up and the internet in Windows works fine.  Although when I am in Ubuntu the internet does not work at all.  

An ethernet cable connects directly into the wireless router and that is how I get my internet.  I use DHCP because by IP address is dynamic.  When I try to start firestarter it says eth1 isn't conifgure or something similar to that.

If I go to network tools it shows two connections, eth1 which has no data at all (meaning it isn't connected I assume) and the loop connection (lo).  Before my PC went down I had had a similar issue where the inter wasn't working really well in either Windows or Ubuntu but the times it was working in Windows it was not in Ubuntu.  Something happened and the internet started working again.. I do not know if I did something by accident or what.  Before I had to get a replacement motherboard and PSU the network tools said that my ethernet interface was eth0.  I have the same motherboard that I had then except this motherboard has a newer BIOS.  

Also the wlan0 (I think) does not show up anymore in network tools as it used to.  I do not use it but I do not know if that is an issue.  I have an onboard wi-fi AP and it isn't disabled but it does not have the actual wi-fi access point hardware attached to it.  My Asus P5B Deluxe/Wi-Fi AP edition has an option in the BIOS>USB configuration to enable or disable USB 9,10/Wifi-AP.  I have thought that possibly the onboard wireless is conflicting but I am not sure if disabling the USB 9,10/Wifi-AP in the BIOS would disable the wireless or both the wireless and USB ports 9 and 10.

I tried ifconfig and it returned some data that isn't very well interpreted by myself.  Although I did notice that the results showed that the (lo) sent and received 8 packets while the eth1 did not send or receive any packets.

Thank you.  This is very frustrating because I am only a novice Linux user and there is no help for these type of things w/o the internet.  Btw why is there no Ubuntu manual in a local folder somewhere for these issues?

---

### Post by GchadB on 2007-03-21
well im not sure if i can help... but what is the make, socket, bla bla bla of your motherboard: this info might help more experienced users solve you problem...

Can you set you DNS or proxy settings to automatic, like windows, or wont that work with you router... suppose not...

If your motherboard has onboard LAN, try checking if it is enabled or disabled in BIOS...

Hope i helped

xxx

---

### Post by billdotson on 2007-03-25
AAAHHHHHHHHH!!!!! I cannot get ANY help!!

Please respond.

In my BIOS it seems that there are a couple things that are switched.  I have a Core 2 Duo and is the same model as my old motherboard (this is a replacement MB).  W/ my old MB for the CPU it would show the first and second cores, the first having 4096KB and the second having 32KB.  I assumed this was okay but I assumed the first core is the dominant one.  Now the values are switched.  The dominant core is the 2nd one and therefore it has 4096KB of cache.  Also, as I have two onboard ethernet ports they seem to be switched as well.  

It isn't visible really in the BIOS but in Ubuntu if I have the ethernet cable plugged into the one I normally have it plugged into (which is the first ethernet port in Windows and the second [I am almost certain] in the BIOS) In Windows the connections are 1394 Connection 2, Local Area Connection (not connected) and Local Area Connection 3 (connected).  In Ubuntu if I boot from the install on my external HDD where I installed it before I got the replacement motherboard the device is eth1 and says it is not connected.  If I put the ethernet cable in the other port it shows that eth1 is sending packets but none of them are being accepted and it has an address (next to IPv6 I think) but still doesn't have a hardware address or anything in that section.  If I boot from the Ubuntu LiveCD it does the same thing only using the Ubuntu LiveCD the ethernet device is eth0, like it was on my external HDD install before I got this replacement MB.

I went into the BIOS and disabled the port that Ubuntu always recognizes to try and force it to recognize the other ethernet port but that did not work.  There showed no ethernet connection at all even after putting the ethernet cable in the port that WAS activated.  
It is really weird that my CPU cores are backwards and that it also seems that my devices like my ethernet ports are backwards.  This is quite annoying.

---

### Post by billdotson on 2007-03-25
update: I got the internet working in Ubuntu.  I plugged in the ethernet cable into the other port (the only one that is recognized by Ubuntu) and then ran sudo ifup eth1 --force.  I first booted the Ubuntu LiveCD and since w/ the LiveCD the ethernet device is shown as eth0 I ran sudo ifup eth0 --force and then the internet started working.

Then I booted into my Ubuntu install and the internet worked.  I went ahead and did sudo ifup eth1 --force to make sure.  So I guess that fixed it.  But I still do not know why Ubuntu will only recognize one ethernet port.

---

