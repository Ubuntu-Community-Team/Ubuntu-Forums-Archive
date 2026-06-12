---
title: "locale -a problem"
date: 2007-02-20
forum: General Help
---

### Post by mitjab on 2007-02-20
when i type locale -a i get

C
en_US.utf8
POSIX

i want all this languages

[http://php.merhar.si/locale.txt](http://php.merhar.si/locale.txt)

/usr/lib/locale has only one folder

mitjab@server:/usr/lib/locale$ dir
en_US.utf8


how to add it?

Thx

---

### Post by bapoumba on 2007-02-20
That's a very large amount of languages to add! For dapper, I do not remember where the  "Language Support" menu is located (> System > Administration on edgy).

---

### Post by mitjab on 2007-02-20
thx for answer. For first enough will be sl_SI or slovenian. I do not have X11 instaled. 
Is it possible to add by console this locale files?

---

### Post by bapoumba on 2007-02-20
```
:~ $ aptitude show language-pack-sl
Package: language-pack-sl
State: not installed
Version: 1:6.10+20070115
Priority: optional
Section: translations
Maintainer: Martin Pitt <martin.pitt@ubuntu.com>
Uncompressed Size: 90.1k
Depends: language-pack-sl-base
PreDepends: dpkg (>= 1.10.27ubuntu1)
Replaces: language-pack-sl-base, language-pack-sl-base (< 1:6.10+20070115), language-pack-gnome-sl-base (< 1:6.10+20070115), language-pack-kde-sl-base (<
          1:6.10+20070115), language-pack-sl (< 1:6.10+20070115)
Description: translation updates for language Slovenian
 Translation data updates for all supported packages for: Slovenian 
 
 language-pack-sl-base provides the bulk of translation data and is updated only seldom. This package provides frequent translation updates. 
 
 Please note that you should install language-support-sl to get full support for this language.

```

You should install language-pack-sl:
**sudo aptitude install language-pack-sl **

Here are the packages versions for dapper:
[http://packages.ubuntu.com/dapper/translations/language-pack-sl]("http://packages.ubuntu.com/dapper/translations/language-pack-sl")
[http://packages.ubuntu.com/dapper/translations/language-pack-sl-base]("http://packages.ubuntu.com/dapper/translations/language-pack-sl-base")

---

### Post by mitjab on 2007-02-20
thx

Must i install all of this packages
```

  aspell aspell-sl bsh dictionaries-common language-pack-sl
  language-pack-sl-base language-support-sl libaudio2 libflac7
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libicu34 libjline-java
  libneon25 libportaudio0 libsndfile1 libstartup-notification0
  libstlport4.6c2 libwpd8c2a libxalan2-java libxaw7 libxmlsec1
  libxmlsec1-nss libxmlsec1-openssl libxmu6 libxt-java libxt6
  mozilla-firefox-locale-sl-si myspell-sl openoffice.org-common
  openoffice.org-core openoffice.org-help-sl openoffice.org-java-common
  openoffice.org-l10n-common openoffice.org-l10n-sl
  openoffice.org-style-crystal openoffice.org-style-default
  openoffice.org-style-hicontrast openoffice.org-style-industrial
  openoffice.org-writer python-uno thunderbird-locale-sl ttf-opensymbol
  xml-core

```

becouse i do not need openoffice and similar products?

---

### Post by bapoumba on 2007-02-20
Mmm... Did not think of that, sorry.
Try with apt-get: **sudo apt-get install language-pack-sl**, you may have less X-based packages dependencies.
So, you want to have your tty in slovenian, right ?
I'm checking, as I never ran into that type of question ;)
Anyone else ?

---

### Post by bapoumba on 2007-02-20
**No guaranty** this will work ;)
Here is my /var/lib/locales/supported.d/local :
```
fr_FR.UTF-8 UTF-8
en_US.UTF-8 UTF-8
```
I have both French and English locales.

May be add :
```
sl_SI.UTF-8 UTF-8
```
To your /var/lib/locales/supported.d/local and then run:
```
sudo locale-gen
```

Have a look at /usr/share/i18n/SUPPORTED.

edit : see also **man locale-gen**.

---

### Post by mitjab on 2007-02-20
Thx You Very Much!

Now Works Fine!

---

