---
title: "FInding Wireless Networks"
date: 2006-12-11
forum: General Help
---

### Post by DannyG on 2006-12-11
Hi,

I've got my wireless BCM4318 Card working no problem using NDISWrapper on Ubuntu Edgy, however, I cannot search for networks.

I can manually enter the SSID in the Network Manager, and this works fine, but when I go to area's that have different SSID's or I don't know the SSID it is quite annoying.

Is there a fix so that the SSID of all available networks will appear on the drop down list in Network Manager (note, i managed to do this in Dapper).

Thanks,
Daniel.

---

### Post by orb9220 on 2006-12-11
Need to install nm-applet known as network manger applet. It is in synaptic and is an applet that sits in tray. Just left click and will show all access points just select to change.

Synaptic should have version 0.6.3 or 4

---

### Post by PrinceArithon on 2006-12-11
Actually I can't find that in my synaptic manager...is there any other way to get it??

---

### Post by DannyG on 2006-12-11
I found it in synaptic, its called "network-manager" if you search for it.

---

### Post by PrinceArithon on 2006-12-11
LOL, thank you, I got it now.  Now my next question is do I have to restart to get it to work or what do I do??

---

### Post by DannyG on 2006-12-11
Took a bit of figuring out myself. If your using the default Network Manager inside Ubuntu, you have to disable the card your using with it.

So access System --> Network Manager, and uncheck the boxes that indicate your using the card.

I then restarted, and you should now be able to left click the icon and connect to your wireless networks. The trick is to make sure your network card is NOT being used the default network manager.

---

