---
title: "&quot;LC_ALL = (unset)&quot; local  problem need to config"
date: 2006-10-05
forum: General Help
---

### Post by Omnios on 2006-10-05
Hi I have been having this error message for a while when starting a program from the terminal.
```
Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale
```

 Anyways this has not been a problem till now as I am getting a different arror trying to launch the globs video benchmark program. Which gives this error

```
tom@miko:~$ globs

(globs:30642): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/globs", line 31, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

```

 Now after reading the other day I came accross this command 
```
sudo dpkg-reconfigure locales
```

I got this output.

```
tom@miko:~$ sudo dpkg-reconfigure locales
Password:
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
Current default timezone: 'US/Eastern'.
Local time is now:      Thu Oct  5 10:23:26 EDT 2006.
Universal Time is now:  Thu Oct  5 14:23:26 UTC 2006.
Run 'tzconfig' if you wish to change it.

```

 Now I think the problem is this [SIZE=3][COLOR=Red]LC_ALL = (unset),[/COLOR][/SIZE]

 Does anyone know how to config it and it seems that it is missing a file 
 Thanks in advance.

---

### Post by ayoli on 2006-10-05
you may try (in a terminal):
```
sudo dpkg-reconfigure localeconf
```

---

### Post by Omnios on 2006-10-05
> **ayoli said:**
> you may try (in a terminal):
```
sudo dpkg-reconfigure localeconf
```

K I installed localeconf and ran dpkg-reconfigure localeconf which gave me a xorg type praphics thing. What I want to know is there anything special I shlould know as I do not want to start the process then get stuck or stuck with a broken system.

---

### Post by nekr0z on 2006-11-15
I have the same LC_ALL problem after my Edgy upgrade. localeconf doesn't seem to work for me, because after running it "locale" command output doesn't change. Is there any other way to set LC_ALL up?

---

