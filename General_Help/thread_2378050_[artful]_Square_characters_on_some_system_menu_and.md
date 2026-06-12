---
title: "[artful] Square characters on some system menu and dialog"
date: 2017-11-19
forum: General Help
---

### Post by paulushe on 2017-11-19
Hi! I've run into a small but weird problem.
I'm running the Ubuntu desktop flavor, 17.10 version (a.k.a. artful, the version that uses GNOME shell desktop). This is a freshly installed system. the problem is, some applications have the captions in the menus and system dialogs squared. In my case, this happens to "onlyoffice" and "Adobe Brackets". This doesn't affect the other parts of the application at all. Other applications installed in this system doesn't exhibit this problem at all, including LibreOffice, Firefox and Android Studio. What could be the cause (and possible fix)?
These 2 applications run perfectly on my ubuntu 16.04 system. Running these 2 affected applications inside Xephyr doesn't eliminate the problem. The output of 'locale' is:
```

LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC=id_ID.UTF-8
LC_TIME=id_ID.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=id_ID.UTF-8
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=id_ID.UTF-8
LC_NAME=id_ID.UTF-8
LC_ADDRESS=id_ID.UTF-8
LC_TELEPHONE=id_ID.UTF-8
LC_MEASUREMENT=id_ID.UTF-8
LC_IDENTIFICATION=id_ID.UTF-8
LC_ALL=

```

Screenshots:
[ATTACH=CONFIG]277588[/ATTACH] This is the file open dialog of both brackets and onlyoffice.
[ATTACH=CONFIG]277589[/ATTACH] This is the brackets' main window. Notice the squared characters of the titlebar.

---

### Post by Holger_Gehrke on 2017-11-19
You're not the only one affected by this problem on brackets [Bugreport and solution on bracket issuetracker on github.]("https://github.com/adobe/brackets/issues/13738")

Holger

---

### Post by paulushe on 2017-11-19
Oh I see. So it is the CEF's problem because of recent changes in libpango.
Thanks for the info.

---

