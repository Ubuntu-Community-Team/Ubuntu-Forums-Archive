---
title: "locale-gen fails"
date: 2013-06-11
forum: General Help
---

### Post by helium78 on 2013-06-11
Hi, can somebody point me to start debugging?

```

timo@uk:~$ sudo locale-gen de_DE.UTF-8
Generating locales...
  de_DE.UTF-8... /usr/sbin/locale-gen: line 243: 20736 Killed                  localedef $no_archive -i $input -c -f $charset $locale_alias $locale
failed
Generation complete.
timo@uk:~$ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=de_DE.UTF-8
LANGUAGE=
LC_CTYPE="de_DE.UTF-8"
LC_NUMERIC=de_DE.UTF-8
LC_TIME=de_DE.UTF-8
LC_COLLATE="de_DE.UTF-8"
LC_MONETARY=de_DE.UTF-8
LC_MESSAGES="de_DE.UTF-8"
LC_PAPER=de_DE.UTF-8
LC_NAME=de_DE.UTF-8
LC_ADDRESS=de_DE.UTF-8
LC_TELEPHONE=de_DE.UTF-8
LC_MEASUREMENT=de_DE.UTF-8
LC_IDENTIFICATION=de_DE.UTF-8
LC_ALL=
timo@uk:~$ locale -a
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory
C
C.UTF-8
POSIX

```

btw it's raring.

---

