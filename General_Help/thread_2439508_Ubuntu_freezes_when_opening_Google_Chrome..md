---
title: "Ubuntu freezes when opening Google Chrome."
date: 2020-03-28
forum: General Help
---

### Post by davidzhou2 on 2020-03-28
For now, it has only happened to me when I open it right after starting the system, but I don't know what the cause may be. The system freezes completely and there is nothing I can do. I attach an image of the system monitor.

---

### Post by CelticWarrior on 2020-03-29
Welcome.

You didn't provide any hardware information, namely graphics card (integrated, discrete or hybrid) so it's anyone's guess. Also no information about your Ubuntu version/release/flavor, etc. And the system monitor screenshot that you had to take when the system was *not* frozen is hardly helpful.

The most common cause for such issues is graphics drivers. Do you by any chance have a Nvidia graphics and are runninmg it with the default open-source driver? That being the case all you need to do is install the Nvidia proprietary drivers that you can find with Additional Drivers.

---

### Post by daniewicz on 2020-03-29
Yes more information is needed. Fresh install? Old computer or new? Need some details before we can help.

---

### Post by mörgæs on 2020-03-30
The standard way of providing hardware information is to copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and post lshw.txt in CODE tags.

---

### Post by davidzhou2 on 2020-03-30
a

---

### Post by mörgæs on 2020-03-31
Please use CODE tags when posting terminal output.

For hardware as new as this I recommend a clean install of 19.10, maybe even 20.04.

---

### Post by davidzhou2 on 2020-04-01
Would it be possible to upgrade from ubuntu 18.04 to 20.04 so I don't have to go through the installation process again?

---

### Post by CelticWarrior on 2020-04-01
> **davidzhou2 said:**
> Would it be possible to upgrade from ubuntu 18.04 to 20.04 so I don't have to go through the installation process again?

Yes, certainly. I wouldn't do that though, I prefer fresh installations - better results and much faster then a release upgrade. And by "much faster" I mean the difference between few minutes and potentially a couple of hours or more. Also there are many differences between those LTS releases that even more strongly recommend a fresh installation.

---

