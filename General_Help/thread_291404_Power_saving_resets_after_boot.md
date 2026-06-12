---
title: "Power saving resets after boot"
date: 2006-11-02
forum: General Help
---

### Post by tubunu on 2006-11-02
Each time I go to Monitor & Display/Power saving and set the monitor to switch off after e.g. 2 minutes, next time I boot it's set to 2 hours. 

How come? Any fix for that?

---

### Post by tubunu on 2006-11-02
Does anyone know how to keep the power saving setting intact on Edgy?

---

### Post by tubunu on 2006-11-02
no clues? :)

---

### Post by Footer on 2006-11-05
I'll add to this thread ... I have the same problem except it resets to 5 hours.  I'm using Kubuntu.  Not only that but even after the power saving kicks in, it still really isn't fully in power saving mode ... The screen blanks out but there is still full power getting to it.

What's the fix???

---

### Post by tubunu on 2006-11-06
Apparently the bug has already been filed. But no fix in sight...... *sigh*

Your power saving turns to 5 hours because you set it to switch off after 5 min, right? 

The conversion table as follows: **1 min = 1 hour ** :-|

---

### Post by Footer on 2006-11-06
Nope, I reset it to 15 minutes and after every reboot or restart of the xserver (logout/login), it goes back to 5 hours.  :-(

Do you have a link to the bug page?  I would like to track it.

Thanks!

---

### Post by tubunu on 2006-11-06
**- KDE Screen power saving settings aren't reloaded after reboot**
* Bug report : [https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/65791]("https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/65791")
* Workaround : None for the moment

---

