---
title: "Emerald Theme not Applied"
date: 2008-05-13
forum: General Help
---

### Post by Lelouch on 2008-05-13
I am trying to apply an emerald theme on Hardy

I have Emerald Themer 0.7.2

When i try to double click on the theme icon i get this error message:

"There is no application installed for this file type"

I even tried to select the theme from the emerald theme manager, but nothing changed and the theme wasnt applied!

Thanks,

---

### Post by NightwishFan on 2008-05-13
Press alt+f2 and type:
```
emerald --replace
```

---

### Post by RRFarFar on 2008-05-13
As far as I know, the command above is just for current session. If try to put in startup it might work, as for me, I restored my system after this small command. Ubuntu just not loaded on next startup. Strange, isn't it
If you want to use emerald

sudo gedit /usr/bin/compiz-decorator

Change line 30 from

USE_EMERALD=”no”

to

USE_EMERALD=”yes”

---

### Post by NIT006.5 on 2008-05-13
> **RRFarFar said:**
> 

sudo gedit /usr/bin/compiz-decorator

Change line 30 from

USE_EMERALD=”no”

to

USE_EMERALD=”yes”

Thanks! I didn't know about that until now. It also appears to have solve some minor display glitches when using emerald. :)

---

### Post by RRFarFar on 2008-05-14
Another thing I have found out yesterday. If install from synaptic the package of Compiz Fusion Icon (which shows icon of compiz in tray), you have enable emrald once again by right clicking an choosing emerald instead of gtk.
Also in LINE 30 (see above) change to 'yes' to only for emerald but also 'yes' for decorator (LINE 31) as well.
It works for me

---

### Post by NikoC on 2008-05-14
I managed to fix it like this (I guess the result is the same):
Main menu > System > Preferences > Advanced Desktop Effects Settings > Effects > Window Decoration (make sure it's enabled) and then add 'emerald --replace' in the command box > close

---

