---
title: "Wireless printer keeps 'disappearing'"
date: 2014-02-28
forum: General Help
---

### Post by skitter on 2014-02-28
I have a laptop running 12.04 and an Epson 4020 printer.   The printer isn't using a cable, it's connecting to my router via WIFI. I frequently get an 'unable to locate printer' when I check the printer's status.  If I simply delete the printer from the Printing applet, and then go through the process to add a new printer, the printer is quickly found and installed and it will work for a seemly random amount of time (a day or more).  Deleting / re-adding the printer only takes a moment, but it would be nice to find a 'real' fix.  Any suggestions?  I have another machine that is able to connect to the printer every time (but this machine uses a wired connection, not WIFI).   I used printer config utility to set a static  IP for the printer, but that hasn't helped.

---

### Post by varunendra on 2014-03-03
Almost all of the network printers have a 'Sleep' feature, which enables them to save power by sending their permanently active parts to 'Sleep' or low power mode.

If the wireless is otherwise working smoothly, like browsing the local network or connecting/browsing internet, then this maybe a problem on the printer's side as mentioned above. Please check the printer manual to see if it has such a feature and if there is a way to change this setting. This will make it more readily available at the cost of a little extra power.

---

### Post by skitter on 2014-03-03
Thanks Varun, but I'm able to use the printer from another machine with out problems.   Something on the laptop seems to keep 'breaking.'

---

### Post by varunendra on 2014-03-04
Does it happen with only the printer or with normal browsing as well? If it is a networking related issue, I may be able to help. If it is printer specific, then I'm a useless guy. :p

---

### Post by desconocido on 2014-03-05
> **skitter said:**
> I have a laptop running 12.04 and an Epson 4020 printer.   The printer isn't using a cable, it's connecting to my router via WIFI. I frequently get an 'unable to locate printer' when I check the printer's status.  ...  I have another machine that is able to connect to the printer every time (but this machine uses a wired connection, not WIFI).   I used printer config utility to set a static  IP for the printer, but that hasn't helped.
Does the WiFi connection work better if the cabled connection is removed? Just a thought.

I have a laptop running 12.04 and an Epson Stylus SX420W printer, connected by WiFi, works fine, there is no cable connection to the printer.

---

### Post by kurt18947 on 2014-03-06
I don't know if this will help but here is my experience.  I had a similar issue with Brother printers.  Install, it works great.  Try to print a few days later and no printer found.  I started assigning static I.P. addresses to the printer then in the device URI address I use
```
socket://xxx.xxx.xxx.xxx:9100
```
where xxx=assigned printer i.p. address.  This has been very reliable for me.  Brother printers seem to conform closely to HP printer protocols.  I'm not sure if this would work as well with Epson or not.

For printer configuration I prefer the app used by Xubuntu, Mint and others, "system-config-printer".  I find it much more useful than the native "printers" app.  It's available in the repositories.

---

### Post by skitter on 2014-03-10
Thanks Kurt,  that seems to have solve the riddle for me. I found that I had to add a trailing slash to get it to work. So I ended up with this-  socket://192.168.1.100:9100/

---

### Post by kurt18947 on 2014-03-10
Great!  Dontcha love it when a plan comes together?:D

---

