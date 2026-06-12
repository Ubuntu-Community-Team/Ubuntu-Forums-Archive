---
title: "Cannot bring up web page"
date: 2007-04-11
forum: General Help
---

### Post by projectubun2 on 2007-04-11
Hi,

Another relatively new Linux user.

System: Cel. 2.4/256mb/20gb/MSI MS7005 mobo.

I have just installed the Ubuntu 7.04 Beta as a clean install with only Linux on the drive. Went really well and Ubuntu installed all the necessary drivers. Amazing.

I threw in a Dlink DWL-520 PCI Wireless Card and Ubuntu picked it up and it appears in Device Manager. The green light on the back of the card even flashes.

I have fiddled around in networking and the Wireless Connection says it has 68% strength to my Excel Access Point. However, I have tried everything, well nearly, but I can't get Firefox to display a webpage.

Ant pointers? I have gone into the advanced settings in Firefox and tried different options in how Firefox connects to the net but nothing worked.

Cheers.

---

### Post by NICU on 2007-04-11
Before applying a few patches I had a similar problem.  I originally fixed my problem by removing the WiFi card then reattaching it.  That probably won't work for a PCI card...  My first suggestion is to apply any patches/updates that are available if you have a wired connection.  

If that doesn't work try ```
sudo ifdown eth0
``` or whatever your wireless adapter's name is.  Then use iwconfig to setup your WiFi connection ```
sudo iwconfig eth0 essid your_routers_essid
``` then ```
sudo ifup eth0
``` 

If that doesn't work let me know any error messages you receive.  Good luck :D

---

### Post by projectubun2 on 2007-04-11
Thanks for reply and advice.

I'll give all that a go and let you know.

Cheers.

---

### Post by projectubun2 on 2007-04-12
Hi NICU,

Your suggestion worked a treat.

I didn't have a wired connection so I skipped the updates and went straight to the next idea and entered what your said in a terminal window.

I opened Firefox and got a web page up first time.

Thanks for your help.

Cheers,

Peter

---

