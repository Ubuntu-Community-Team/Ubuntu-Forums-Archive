---
title: "thin client login screen error"
date: 2008-04-09
forum: General Help
---

### Post by tmelbye on 2008-04-09
Have changed the login screen for the thin clients using the following:

sudo cp -r /opt/ltsp/i386/usr/share/ldm/themes/Edubuntu /opt/ltsp/i386/usr/share/ldm/themes/MyTheme

sudo rm /opt/ltsp/i386/usr/share/ldm/themes/default

sudo ln -s /opt/ltsp/i386/usr/share/ldm/themes/MyTheme
/opt/ltsp/i386/usr/share/ldm/themes/default

The folder: mytheme has permission 755
The default "file" has permission 777 (unable to change)

Now the thin clients only display a gray screen without any icons. Login works as normal.

Have tried to change the default back but the problem is still there.

What am I doing wrong???

Anyone know what I should do???????

---

