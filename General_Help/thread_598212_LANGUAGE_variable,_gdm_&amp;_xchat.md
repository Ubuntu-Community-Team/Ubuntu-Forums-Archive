---
title: "LANGUAGE variable, gdm &amp; xchat"
date: 2007-10-31
forum: General Help
---

### Post by bananarama on 2007-10-31
Hi,

This is the content of my /etc/default/locale:
```
LANGUAGE="en_GB:en:de_DE:de"
LANG="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_CTYPE="de_DE.UTF-8"
LC_NUMERIC="de_DE.UTF-8"
LC_TIME="de_DE.UTF-8"
LC_COLLATE="de_DE.UTF-8"
LC_MONETARY="de_DE.UTF-8"
LC_PAPER="de_DE.UTF-8"
LC_NAME="de_DE.UTF-8"
LC_ADDRESS="de_DE.UTF-8"
LC_TELEPHONE="de_DE.UTF-8"
LC_MEASUREMENT="de_DE.UTF-8"
LC_IDENTIFICATION="de_DE.UTF-8"
```

As you can see, the interface language for gnome and all programs is set to English while the other regional settings are set to German. This works as expected. However, gdm seems to unset the LANGUAGE variable.

Output of *locale* in gnome-terminal:
```
LANG=en_GB.UTF-8
LC_CTYPE=de_DE.UTF-8
LC_NUMERIC=de_DE.UTF-8
LC_TIME=de_DE.UTF-8
LC_COLLATE=de_DE.UTF-8
LC_MONETARY=de_DE.UTF-8
LC_MESSAGES=en_GB.UTF-8
LC_PAPER=de_DE.UTF-8
LC_NAME=de_DE.UTF-8
LC_ADDRESS=de_DE.UTF-8
LC_TELEPHONE=de_DE.UTF-8
LC_MEASUREMENT=de_DE.UTF-8
LC_IDENTIFICATION=de_DE.UTF-8
LC_ALL=
```

Output of *locale* in a STRG+ALT+? console:
```
LANG=en_GB.UTF-8
LANGUAGE=en_GB:en:de_DE:de
LC_CTYPE=de_DE.UTF-8
LC_NUMERIC=de_DE.UTF-8
LC_TIME=de_DE.UTF-8
LC_COLLATE=de_DE.UTF-8
LC_MONETARY=de_DE.UTF-8
LC_MESSAGES=en_GB.UTF-8
LC_PAPER=de_DE.UTF-8
LC_NAME=de_DE.UTF-8
LC_ADDRESS=de_DE.UTF-8
LC_TELEPHONE=de_DE.UTF-8
LC_MEASUREMENT=de_DE.UTF-8
LC_IDENTIFICATION=de_DE.UTF-8
LC_ALL=
```

As a result, XChat uses only the English dictionary for spell checking. When I start XChat in gnome-terminal with "LANGUAGE=en_GB:en:de_DE:de xchat", both languages are available for spell checking but the interface is set to German.

What am I doing wrong? I want to start XChat from the applications menu with both languages available for spell checking and an English interface.

Any Ideas?

---

