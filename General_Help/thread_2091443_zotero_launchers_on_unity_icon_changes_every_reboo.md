---
title: "zotero launchers on unity icon changes every reboot"
date: 2012-12-05
forum: General Help
---

### Post by kevinr1 on 2012-12-05
So, this is a wierd one... I have created a zotero launcher icon using this code and placed it in /usr.share/applications/

#!/usr/bin/env xdg-open
[Desktop Entry]
Type=Application
Name=Zotero
GenericName=Bibliography Reference Manager
Icon=/home/kevin/.icons/default48.png
Exec=/opt/Zotero_linux-x86_64/zotero %f
Categories=Office
Terminal=false

I then search for it in the dash and add it to the launcher.  However, everytime I reboot the computer, a different icon displays for a dictionary and when I search for Zotero in the Dash I get one with the same wrong icon and a different description of "Open-source reference manager".

Any thoughts?

---

### Post by kevinr1 on 2012-12-06
figured it out.  there was a duplicate icon in ~/.local/share/applications that took priority over the one in /usr/share/applications

---

