---
title: "_S_create_c_locale name not valid"
date: 2014-07-18
forum: General Help
---

### Post by sgofferj on 2014-07-18
Hi,

so for my new computer I decided to try kubuntu (14.04) after 18+ years on SuSE and I'm currently stuck with a weird problem:
Several programs crash with this message:

```
terminate called after throwing an instance of 'std::runtime_error'
  what():  locale::facet::_S_create_c_locale name not valid
```

I have already figured out that it might be a problem caused by LC_ALL set to nothing but when I try to set LC_ALL, I get
```
bash: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
```

Well, and dpkg-reconfigure locales also blew up in my face...:
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = "en_FI.UTF-8",
        LC_PAPER = "en_FI.UTF-8",
        LC_ADDRESS = "en_FI.UTF-8",
        LC_MONETARY = "en_FI.UTF-8",
        LC_NUMERIC = "en_FI.UTF-8",
        LC_TELEPHONE = "en_FI.UTF-8",
        LC_IDENTIFICATION = "en_FI.UTF-8",
        LC_MEASUREMENT = "en_FI.UTF-8",
        LC_TIME = "en_FI.UTF-8",
        LC_NAME = "en_FI.UTF-8",
        LANG = "en_FI.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/bin/bash: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
Generating locales...
  en_AG.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_AU.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_BW.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_CA.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_DK.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_GB.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_HK.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_IE.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_IN.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_NG.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_NZ.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_PH.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_SG.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_US.ISO-8859-1... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
done
  en_US.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_ZA.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_ZM.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  en_ZW.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
  fi_FI.UTF-8... /usr/sbin/locale-gen: line 177: warning: setlocale: LC_ALL: cannot change locale (en_FI.UTF-8)
up-to-date
Generation complete.

```

So, I tend to assume that there is some major bug in 14.04...? How do I get around it, is the question...

-S

---

### Post by sgofferj on 2014-07-18
Yup, it's a bug - pretty fat one...
In the KDE settings, I configured country "Finland" and language "American English". The setup turned that into en_FI.UTF-8 - which of course is nonsense. The other bug is in the libraries which go ballistic and die instead of falling back to some default value...

---

### Post by F-3000 on 2014-07-20
I've ran into this same oddity of "*en_FI.UTF-8*" with Kubuntu 14.04, but luckily I yet have not faced any crashes (defaulting back to C works). It relates to that I want to have my DE language as english, yet use Finnish locales.

This is what I had when I installed GIMP:
```
[...]
Fetched 24.6 MB in 5s (4235 kB/s)            
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LC_TIME = "en_FI.UTF-8",
        LC_MONETARY = "en_FI.UTF-8",
        LC_ADDRESS = "en_FI.UTF-8",
        LC_TELEPHONE = "en_FI.UTF-8",
        LC_NAME = "en_FI.UTF-8",
        LC_MEASUREMENT = "en_FI.UTF-8",
        LC_IDENTIFICATION = "en_FI.UTF-8",
        LC_NUMERIC = "en_FI.UTF-8",
        LC_PAPER = "en_FI.UTF-8",
        LANG = "en_FI.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously unselected package libamd2.3.1:amd64.
[...]
Processing triggers for man-db (2.6.7.1-1) ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Processing triggers for hicolor-icon-theme (0.13-1) ...
[...]
```

Here's content of *locale*:
```
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_FI.UTF-8
LANGUAGE=en
LC_CTYPE="en_FI.UTF-8"
LC_NUMERIC=en_FI.UTF-8
LC_TIME=en_FI.UTF-8
LC_COLLATE="en_FI.UTF-8"
LC_MONETARY=en_FI.UTF-8
LC_MESSAGES="en_FI.UTF-8"
LC_PAPER=en_FI.UTF-8
LC_NAME=en_FI.UTF-8
LC_ADDRESS=en_FI.UTF-8
LC_TELEPHONE=en_FI.UTF-8
LC_MEASUREMENT=en_FI.UTF-8
LC_IDENTIFICATION=en_FI.UTF-8
LC_ALL=
```

Content of */var/lib/locales/supported.d/local*:
```
fi_FI.UTF-8 UTF-8
en_US.UTF-8 UTF-8
```

Content of */etc/default/locale*:
```
LANG="en_US.UTF-8"
LC_NUMERIC="fi_FI.UTF-8"
LC_TIME="fi_FI.UTF-8"
LC_MONETARY="fi_FI.UTF-8"
LC_PAPER="fi_FI.UTF-8"
LC_NAME="fi_FI.UTF-8"
LC_ADDRESS="fi_FI.UTF-8"
LC_TELEPHONE="fi_FI.UTF-8"
LC_MEASUREMENT="fi_FI.UTF-8"
LC_IDENTIFICATION="fi_FI.UTF-8"
```

---

