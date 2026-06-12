---
title: "Transliteration"
date: 2007-12-19
forum: General Help
---

### Post by gerases on 2007-12-19
Hello, I'm trying to do something pretty simple -- use iconv to trnasliterate a piece of Russian into English.

Here's the command:
```

echo "&#1044;&#1086;&#1073;&#1088;&#1099;&#1081; &#1074;&#1077;&#1095;&#1077;&#1088;" | LC_ALL=ru_RU.UTF-8 iconv -t ASCII//TRANSLIT -f UTF-8
?????? ?????

```

What I get is a question mark for each of the characters and I should get "Dobryj vecher" or something close to that. It works for German though:

```

echo Schlüssel | LC_ALL=de_DE.UTF-8 iconv -t ASCII//TRANSLIT -f UTF-8
Schluessel

```

My locales are:

```

locale -a
C
cs_CZ
cs_CZ.utf8
de_DE.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX
ru_RU.utf8

```

Would be very curious to find out what I'm missing!!!

Thanks for any suggestions,
Sergei

P.S.: my terminal locale is set up as follows:

```

locale
LANG=en_US.UTF-8
LANGUAGE=en
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

```

---

