---
title: "I accidentilly removed CUPS, and when I reinstalled, my printer's not on the list"
date: 2007-05-06
forum: General Help
---

### Post by Falcorian on 2007-05-06
So I had my HP D2360 working fine... I just plugged it in, and followed the instructions (I even wrote a post about how easy it was...).

Then I was stupid and uninstalled part of CUPS. I've reinstalled all of cupsys that I can find... But my printer is not longer on the list in the printer install wizard.


Anyone have any advice? I feel like such a noob at this point... ;)



[SIZE="4"]FIX:[/SIZE] Installed hplips and ```
sudo /etc/init.d/cupsys restart
```, and it showed up in the wizard.

---

### Post by m0eman on 2007-05-06
Maybe when you uninstalled cups it uninstalled some other drivers with it, and you didn't get them back after you reinstalled. Try installing the following:

hplip (HP printer drivers)
cupsys-driver-gutenprint (Lots of printer drivers)
bluez-cups (Bluetooth printer drivers)

And then try again.
(Those were the pakages listed for removal when I tested removing cups) (I should also mention that I'm using feisty so the gutenprint one might not even be on earlier releases, but I'm pretty sure hplip is the only one you really need)

---

### Post by Falcorian on 2007-05-06
I removed cups when removing (because I didn't know better and hit yes too fast) gs-common.

This also removes:

```
gs-esp gs-common cupsys-driver-gutenprint evince cupsys
```

I have however reinstalled all of these. Maybe I'm not remembering correctly when I originally installed my printer and there was no D2300 (I know there was no D2360, but there was a D2300), but I'm pretty sure there was. :-/

---

### Post by m0eman on 2007-05-06
I looked under my add a printer and it lists deskjet d2300 under hp. It uses the hpijs driver which is also available in synaptic. Try installing or reinstalling it, hopefully that works.

---

### Post by Falcorian on 2007-05-07
Thanks! I had reinstalled hplips, but it didn't show up so I figured it didn't work.

This time I installed it and restarted cupsys, and there it is! :)

---

