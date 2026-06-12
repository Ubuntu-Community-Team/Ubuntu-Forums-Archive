---
title: "Main Menu Icons in Thunderbird 2 Beta"
date: 2007-02-01
forum: General Help
---

### Post by Athanasius on 2007-02-01
I have installed Thunderbird 2 beta (following the installation guide for Sunbird in the How-to section) and I cannot get the icon to show up in the Internet part of the Applications bar; it makes a new section called "Other".  Here is what I used:
```
[Desktop Entry]
Name=Thunderbird
Comment=E-Mail Application
Exec=thunderbird.sh
Icon=/opt/thunderbird/chrome/icons/default/default.xpm
Terminal=false
Type=Application
Categories=Application;Internet;
```

I am thinking that the problem is in the "Categories" part.

---

### Post by Athanasius on 2007-02-01
crickets

---

### Post by Athanasius on 2007-02-01
figured out my error, it is supposed to be ```
Categories=Application;Network;
```
thanks anyways

---

