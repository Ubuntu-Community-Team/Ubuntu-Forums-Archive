---
title: "How to switch between Right To Left and Left To Right layout"
date: 2013-05-24
forum: General Help
---

### Post by mbnoimi on 2013-05-24
I want to know how can I switch between Right To Left and Left To Right layout for GTK based applications.

Qt based (KDE) use "-reverse" argument so in case current locale is LTR "-reverse" will switch the interface in RTL... I'm wondering what's the alternative for GTK based?!

---

### Post by mbnoimi on 2013-05-24
I tried the following but it didn't show RTL layout!

```
#!/bin/bash
locale
LANG=ar_LY.UTF-8
LANGUAGE=ar_LY.UTF-8
LC_ALL=ar_LY.UTF-8
locale
gramps
```

The output was:
```
mbnoimi@mbnoimi-pc /media/truecrypt1/Documents/Projects/Arabizing/gramps $ ./run_tmp.sh 
LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
./run_tmp.sh: line 6: warning: setlocale: LC_ALL: cannot change locale (ar_LY.UTF-8)
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=ar_LY.UTF-8
LANGUAGE=ar_LY.UTF-8
LC_CTYPE="ar_LY.UTF-8"
LC_NUMERIC="ar_LY.UTF-8"
LC_TIME="ar_LY.UTF-8"
LC_COLLATE="ar_LY.UTF-8"
LC_MONETARY="ar_LY.UTF-8"
LC_MESSAGES="ar_LY.UTF-8"
LC_PAPER="ar_LY.UTF-8"
LC_NAME="ar_LY.UTF-8"
LC_ADDRESS="ar_LY.UTF-8"
LC_TELEPHONE="ar_LY.UTF-8"
LC_MEASUREMENT="ar_LY.UTF-8"
LC_IDENTIFICATION="ar_LY.UTF-8"
LC_ALL=

(process:22559): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
mbnoimi@mbnoimi-pc /media/truecrypt1/Documents/Projects/Arabizing/gramps $ 

```

By the way, the applications show Arabic strings but the layout appears in LTR instead of RTL

---

### Post by mbnoimi on 2013-05-24
I successfully updated the locales... 
```
mbnoimi-pc mbnoimi # locale-gen ar_LY.UTF-8
Generating locales...
  ar_LY.UTF-8... done
Generation complete.
mbnoimi-pc mbnoimi # locale-gen ar_SY.UTF-8
Generating locales...
  ar_SY.UTF-8... done
Generation complete.
mbnoimi-pc mbnoimi # dpkg-reconfigure locales
Generating locales...
  ar_LY.UTF-8... up-to-date
  ar_SY.UTF-8... up-to-date
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZM.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.
mbnoimi-pc mbnoimi # 

```

The output became:
```
LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
LANG=ar_LY.UTF-8
LANGUAGE=ar_LY.UTF-8
LC_CTYPE="ar_LY.UTF-8"
LC_NUMERIC="ar_LY.UTF-8"
LC_TIME="ar_LY.UTF-8"
LC_COLLATE="ar_LY.UTF-8"
LC_MONETARY="ar_LY.UTF-8"
LC_MESSAGES="ar_LY.UTF-8"
LC_PAPER="ar_LY.UTF-8"
LC_NAME="ar_LY.UTF-8"
LC_ADDRESS="ar_LY.UTF-8"
LC_TELEPHONE="ar_LY.UTF-8"
LC_MEASUREMENT="ar_LY.UTF-8"
LC_IDENTIFICATION="ar_LY.UTF-8"
LC_ALL=
2013-05-24 20:03:16.805: WARNING: __init__.py: line 66: Date parser for 'ar_LY' not available, using default
2013-05-24 20:03:16.842: WARNING: __init__.py: line 82: Date displayer for 'ar_LY' not available, using default
2013-05-24 20:03:17.186: WARNING: Spell.py: line 60: Spelling checker is not installed
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
2013-05-24 20:03:17.972: WARNING: Relationship.py: line 1853: Family relationship translator not available for language 'ar'. Using 'english' instead.
```

Any help guys?

---

### Post by mbnoimi on 2013-05-24
Oops... it works I just needed to reboot my system

---

