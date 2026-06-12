---
title: "Language (as in a spoken language) of bash"
date: 2014-03-23
forum: General Help
---

### Post by eline.wiel on 2014-03-23
When I as a user execute commands like, date, cal and even ls -l the output is in Dutch

When I let root do it (my cron.daily script for trim writes to my own log) the output is in English.

I am Dutch but I don't know how Ubuntu knows that (does this use my location?)

This annoys me, because I like things to be consistent. How did this happen and is there any way I can change this?

---

### Post by Korkel on 2014-03-23
Choosed the Dutch language on setup..?

---

### Post by eline.wiel on 2014-03-23
No, I did not, and my whole GUI is in English.

---

### Post by bapoumba on 2014-03-23
My system is also in English, but my locales are in French (date, cal, etc.).
Please check yours :
```
~$ locale
LANG=en_US.UTF-8
LANGUAGE=en_US:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC=fr_FR.UTF-8
LC_TIME=fr_FR.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=fr_FR.UTF-8
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=fr_FR.UTF-8
LC_NAME=fr_FR.UTF-8
LC_ADDRESS=fr_FR.UTF-8
LC_TELEPHONE=fr_FR.UTF-8
LC_MEASUREMENT=fr_FR.UTF-8
LC_IDENTIFICATION=fr_FR.UTF-8
LC_ALL=

```

---

### Post by eline.wiel on 2014-03-23
```
eline@Eline-Laptop:~$ locale
LANG=en_US.UTF-8
LANGUAGE=en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC=nl_NL.UTF-8
LC_TIME=nl_NL.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=nl_NL.UTF-8
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=nl_NL.UTF-8
LC_NAME=nl_NL.UTF-8
LC_ADDRESS=nl_NL.UTF-8
LC_TELEPHONE=nl_NL.UTF-8
LC_MEASUREMENT=nl_NL.UTF-8
LC_IDENTIFICATION=nl_NL.UTF-8
LC_ALL=
```

So the ones that are French in yours are Dutch in mine. Can you change these?

---

### Post by bapoumba on 2014-03-23
Yes, you can :)
[https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale)

The file to edit is ~/.pam_environment. You'll need to logout and log back in. Keep a backup file just in case :)
```
~$ cat .pam_environment 
LANGUAGE=en_US:en
LANG=en_US.UTF-8
LC_NUMERIC=fr_FR.UTF-8
LC_TIME=fr_FR.UTF-8
LC_MONETARY=fr_FR.UTF-8
LC_PAPER=fr_FR.UTF-8
LC_NAME=fr_FR.UTF-8
LC_ADDRESS=fr_FR.UTF-8
LC_TELEPHONE=fr_FR.UTF-8
LC_MEASUREMENT=fr_FR.UTF-8
LC_IDENTIFICATION=fr_FR.UTF-8
PAPERSIZE=a4
```

---

