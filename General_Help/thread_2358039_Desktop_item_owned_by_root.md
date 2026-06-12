---
title: "Desktop item owned by root ?"
date: 2017-04-09
forum: General Help
---

### Post by raleigh3 on 2017-04-09
I made a desktop file.

It runs ok, but the file is owned by root instead of by me.

(It shows a cute lock symbol in the corner of the icon.)

```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=CX7 Maintenance
Comment=CX7 Maintenance
Keywords=
Exec=libreoffice --writer /home/andy/Documents/CX7_Maintenance_Log.odt
Icon=/home/andy/Icons/Mazda_CX-7.png
Categories=
Terminal=false
StartupNotify=true
Name[en_US]=
```

Why is that ?

---

### Post by Impavidus on 2017-04-09
Shouldn't happen automatically. Maybe you used sudo when creating that file? You can fix it with chown.

---

### Post by raleigh3 on 2017-04-09
I do not think I used sudo to produce the file, but I may have.

I used chown to fix it.

---

