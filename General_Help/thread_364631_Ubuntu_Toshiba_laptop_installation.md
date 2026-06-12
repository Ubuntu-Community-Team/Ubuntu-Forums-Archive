---
title: "Ubuntu Toshiba laptop installation"
date: 2007-02-18
forum: General Help
---

### Post by stchman on 2007-02-18
Hello all, I just purchased a laptop with Windows Vista.  I erased the HD in favor of Ubuntu 6.10.

Only problem is when I get to 82% installation it seems to just sit there for a long time and do nothing.  Here is what I get.

Installing System
Configuring apt

Scanning the Mirror

I can stil lmove the mouse and stuff, but nothing else.  I have tried to install a couple of times.

Here is the model laptop I purchased.

Toshiba Satellite A135-S2246.

I booted up the system with the Live portion from the CD.  Everything worked except the wireless card.  Has anyone else had this problem.  Any help would be appreciated.

Thanks

---

### Post by tribble222 on 2007-02-19
I could be wrong, but it sounds like it's trying to scan the repositories and failing.  You might try disabling networking within Ubuntu and seeing if it will then time out on the "scanning the mirror" part.

---

### Post by edubarr on 2007-02-19
I've got a toshiba M70 laptop and the instalation went smoothly, but I had my wireless switch on "off" and a network cable plugged in. After it finished the installation I followed the [WPA how-to]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo") to install WPA support. After this the wireless works without any problems on open or WPA networks. For some odd reason (which I didn't bother to research) it won't connect to 64/128-bit WEP networks.

Hope this helps.

---

### Post by am_pcguy on 2007-02-20
I just got my Toshiba A130/A135 custom Laptop yesterday.  I bought it from Toshiba so I could pick the intel wireless card.  It has a Realtek ethernet card that didn't work under the live CD but works fine after the full install.  

I try installing without the network.  Do you know the brand of the wired and wireless NIC's?

---

