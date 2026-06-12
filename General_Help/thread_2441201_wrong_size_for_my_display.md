---
title: "wrong size for my display"
date: 2020-04-20
forum: General Help
---

### Post by jarp53 on 2020-04-20
I am running Ubuntu 18.04 the display manager shows [ Samsung Electric Company 55" ]   but it really is a 32" ; could some one please show how to edit this error and please be a little specific as I am not very technical; Thank you very much

---

### Post by Autodave on 2020-04-20
What cabling/adapters are you using to connect the PC to the TV?

---

### Post by gsahli on 2020-04-20
You didn't say, so I ask:
Does your Ubuntu desktop fit the screen correctly, but it just doesn't report the Device name correctly in the Control Center > Displays dialog box?

---

### Post by jarp53 on 2020-04-20
I have two other OS's windows and LMDE 4, they both show the correct size ; and yes the desktop looks fine , so maybe is just the name is not display correctly .

---

### Post by CelticWarrior on 2020-04-21
Yes, it's just the name.

---

### Post by jarp53 on 2020-04-21
now I notice that several games open in full screen they go past the edges , I think I really need to make the display 32 inches , how do I do that .

---

### Post by CelticWarrior on 2020-04-21
I can't be just some games. If it is oversacnning the desktop is affected in the same way. And that being the case the adjustment is done in the TV. Some vendors call it Picture Mode, others Proportion (e.g. LG - QMenu), etc.

It is NOT related with the name/size, unless the resolution is also incorrectly set.

---

### Post by jarp53 on 2020-04-21
the resolution is 1920x1080 which is correct,  but then why LMDE 4, and Windows show the correct size , and could I just open the file that shows the monitor size and change it from 55 to 32 ; and I also need to mention that this is a new re installation and I have not change any thing , and in the past 18.04 has always shown the right size

---

### Post by Yellow Pasque on 2020-04-21
As far as I'm aware, the screen size in inches is calculated from the EDID. Maybe this will help you get a better understanding (remove the serial number if you share this info, just to be on the paranoid side):
```
sudo apt-get install edid-decode
xrandr --verbose >> edid.txt
edid-decode edid.txt
```

---

