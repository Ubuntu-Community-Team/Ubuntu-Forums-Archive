---
title: "Install LibreOffice 4 on Ubuntu 12.04?"
date: 2013-04-20
forum: General Help
---

### Post by rbscairns on 2013-04-20
I am trying to install LibreOffice 4 on Ubuntu 12.04 (with Gnome Classic). So far. I have-
[LIST=1]
[*]Downloaded LibreOffice_4.0.2_Linux_x86_deb.tar.gz.
[*]Using Airchive Manager, extracted LibreOffice_4.0.2.2_Linux_x86_deb (saved in my Downloads).
[*]Started to follow the README_en-US and ensured that all traces of the previous LibreOffice had been removed (using Ubuntu Software Center) including any entries in the Main Menu.
[*]Opened the DEBS folder and found 51 .deb files and a desktop-intergration fold.
[*]As per the README_en-US, I right-cicked within the DEBS directory to choose "Open in terminal".
[*]There was no "open in terminal option available to me.
[*]
[/LIST]
So now I have the LibreOffice 4 DEBS folder saved in my Downloads directory. How do I install LibreOffice 4 on my Ubuntu 12.04 (with Gnome Clasic) machine?

---

### Post by Irihapeti on 2013-04-20
You have two choices.

If you have no right-click option available, you can open a terminal from the main menu and 

```
cd /Downloads/Libreoffice4.0/DEBS
```

(or whatever the correct directory path is) and then proceed with the rest of the instructions.

Or, if you want to install the right-click-to-open-terminal functionality (and it can be useful), install nautilus-open-terminal.

---

### Post by rbscairns on 2013-04-21
Thank you Irihapeti. Everything worked well with the code you suggested. I now have LibreOffice 4.0.2.2 installed.

---

### Post by Irihapeti on 2013-04-21
You're welcome. Glad to hear that it worked.

---

