---
title: "command-not-found"
date: 2013-02-12
forum: General Help
---

### Post by sinaphysics on 2013-02-12
I uses "kde partition manager" in terminal to open that app. I know this command is wrong to open but I see that command-not-found crashed.

> command-not-found version: 0.3
Python version: 3.2.3 final 0
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
Exception information:

unsupported locale setting
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/CommandNotFound/util.py", line 24, in crash_guard
    callback()
  File "/usr/lib/command-not-found", line 69, in main
    enable_i18n()
  File "/usr/lib/command-not-found", line 40, in enable_i18n
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python3.2/locale.py", line 541, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting 

---

### Post by ibjsb4 on 2013-02-12
A quick search turn up:

```
kdesudo partitionmanager
```

Give that a try.  More here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=start+kde+partition+manager+in+terminal&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=start+kde+partition+manager+in+terminal&sa=Search&cof=FORID:9)

---

### Post by dino99 on 2013-02-12
you seems to have 2 issues there:

- your crash, which might be reported: right click on the crash file found into /var/crash/, and select "report". Apport will do the job

- and the "locale" issue, you might try first to resolve it.

note: you can also reconfigure the package first:

```
sudo dpkg-reconfigure command-not-found
```

---

### Post by sinaphysics on 2013-02-12
I did the 
> 
sudo dpkg-reconfigure command-not-found

And the result was
> perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "en_US:en",
    LC_ALL = (unset),
    LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

I mention that all crashes was reported.

---

