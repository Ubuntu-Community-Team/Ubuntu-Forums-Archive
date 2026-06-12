---
title: "how do I connect to two networks at once"
date: 2008-04-08
forum: General Help
---

### Post by darkorical on 2008-04-08
At work we have 2 different networks and I am one of the few people who need to be connected to both. 
my desktop is windows xp pro and does this just fine but my laptop is vista / ubuntu vista has no issues with both connections but when I switch to linux it seems to only allow one at a time.

one is wireless and one is wired any time I try to tell ubuntu to connect to the wireless it disconnects the wired how do I get connected to both at the same time?

---

### Post by darkorical on 2008-04-08
wow this place moves fast ... no replies and 3 hours later its at the bottom of page 3 
well I tried looking in manual config and came up empty handed and network tools didnt seem to helop me any so what am I missing

---

### Post by Iowan on 2008-04-08
> **darkorical said:**
> wow this place moves fast ... no replies and 3 hours later its at the bottom of page 3 Yes, but 40-some have looked at it...  
Wireless is a bit out of my league.  Check the **/etc/network/interfaces** file to see if both connections are set to "auto".

---

### Post by nkassi on 2008-04-08
You can definitively setup both. can you explain a little more about your network topology? I understand that you have one network you want to access with wireless and the other with wired. 

Use the automatic configuration for wireless (using the little applet at the top.) and for the wired connection. If you go to System->Administration->Network you should be able to see your wired connection and switch from roaming to manual. Once on manual you can setup the static ip information or stay with dhcp. 

If this still doesn't work. All is not lost, you can use the command line and an editor to fix it all up. 

Let me know.

---

