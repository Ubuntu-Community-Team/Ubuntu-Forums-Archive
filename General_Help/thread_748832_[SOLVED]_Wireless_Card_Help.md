---
title: "[SOLVED] Wireless Card Help"
date: 2008-04-07
forum: General Help
---

### Post by neodude237 on 2008-04-07
I finally got a dual boot working, but I need some help with my wireless card, it is an Atheros card, and I need some help getting it to work... I do have access to a wired connection now if that matters, but for tomorrow, I will probably need wireless if I am going to use Linux.

---

### Post by ibuclaw on 2008-04-07
Hi, Welcome to Ubuntu (I read your previous thread).

OK, first thing to ask, before I start.

What is the name and model of your Wireless Device?

ie:
Mine is a Netgear WG311T

Regards
Iain

---

### Post by neodude237 on 2008-04-07
Is there anyway Linux can tell me? Or do I have to boot back into windows and get it there?

---

### Post by ibuclaw on 2008-04-07
Nevermind, I'll just go with a generic walkthrough.

Atheros Cards generally need **MadWifi** Drivers.

90% of these cards should be picked up by Ubuntu.
Open up your restricted drivers manager (System>Administration>Restricted Drivers)

If your card is in the list, enable it and Ubuntu will download and install everything for you.
[[IMG]http://img365.imageshack.us/img365/1046/screenshothardwaredrivegs8.th.png[/IMG]](http://img365.imageshack.us/my.php?image=screenshothardwaredrivegs8.png)

If that fails. There is a tool called ndiswrapper. It gives you the ability to use Windows drivers on wireless devices in Linux.

---

### Post by neodude237 on 2008-04-07
It says it is already enabled @_@ Am I just not connecting to networks right?

---

### Post by prshah on 2008-04-07
> **neodude237 said:**
> It says it is already enabled @_@ Am I just not connecting to networks right?

try ```
iwconfig
``` and post the results here.

---

### Post by ibuclaw on 2008-04-07
Okay, presuming that it is in use and functional.

Leftt-Click on the Network Manager Icon in the top right-hand corner of the screen.

[[IMG]http://img369.imageshack.us/img369/8677/42481157gm2.th.png[/IMG]](http://img369.imageshack.us/my.php?image=42481157gm2.png)

And then click on the name of your Wireless Router.
[[IMG]http://img358.imageshack.us/img358/2210/screenyx0.th.png[/IMG]](http://img358.imageshack.us/my.php?image=screenyx0.png)

A window will pop-up prompting you for your Passphrase or WEP Key.

If you enter in a Passphrase, make sure that you click on the "ASCII" check box.

Regards
Iain

---

### Post by neodude237 on 2008-04-07
Yeah, I do not see that @_@

---

### Post by ibuclaw on 2008-04-07
Okay, then it's as prshah said then.

Open up a terminal (Applications>Accessories>Terminal) and type in:
```
 iwconfig 
```

Copy the output and post it.

Regards

---

### Post by neodude237 on 2008-04-07
lo no wireless extensions.
eth0 no wireless extensions.

---

### Post by ibuclaw on 2008-04-07
OK, the device driver module isn't enabled.

To enable it.

I think this should do it.
```

sudo modprobe ath_pci
sudo modprobe ath_rate_sample
sudo modprobe wlan
sudo modprobe ath_hal

```

Any errors, just copy them and post them.

Regards
Iain

---

### Post by neodude237 on 2008-04-07
It still says it is not enabled :( should I just get the card model out of windows?

---

### Post by neodude237 on 2008-04-07
Om my card is an Atheros AR5007EG Wireless Network Adavpter Device ID: PCI

---

### Post by prshah on 2008-04-08
> **neodude237 said:**
> Om my card is an Atheros AR5007EG Wireless Network Adavpter Device ID: PCI

For atheros5007 you will need to use ndiswrapper since there is no native driver. Download the xp driver from [http://www.atheros.cz/](http://www.atheros.cz/) and then use ndiswrapper.

---

