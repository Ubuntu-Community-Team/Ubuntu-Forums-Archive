---
title: "Nautilus image converter"
date: 2016-05-08
forum: General Help
---

### Post by dFlyer on 2016-05-08
Running Ubuntu 16.04 LTS (Unity), I installed Nautilus image converter with has two scripts one for resize and the other for rotate. The resize  script seems to be working correctly. The rotate not working at all. Can someone please verify that this is a problem for them beside my self. A quick search didn't find any recent bugs listed.

Thanks

---

### Post by mc4man on 2016-05-08
There was a bug that prevented the rotate dialog from showing up. Was fixed about 2 yrs. ago in git but nobody pays much attention lately, the extension hasn't been updated since 14.10, if then..

fortunately this can be fixed simply by editing a .ui file as root. So in a terminal - 
```
 sudo -H gedit /usr/share/nautilus-image-converter/nautilus-image-rotate.ui
```

you want to remove this line & the space it occupied - 
> <property name="has_separator">False</property>
Then save & close gedit, the dialog should now open (whether it actually works you'll have to see..
Ck. screenshot, the line to remove is highlighted, about 33 lines down

---

### Post by dFlyer on 2016-05-08
Thank you. That worked.

---

