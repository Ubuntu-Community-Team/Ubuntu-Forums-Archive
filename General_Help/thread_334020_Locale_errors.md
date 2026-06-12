---
title: "Locale errors"
date: 2007-01-08
forum: General Help
---

### Post by tito2502 on 2007-01-08
Hi, I have installed the latest version of Cedega but when I start it I get

```
(Point2Play_gui.py:6746): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 44, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
tito@tito-ubuntu:~$ cedega

(Point2Play_gui.py:7117): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 44, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

```

I have seen similar errors several times when running commands too.

This is Ubuntu 6.10 x86

---

### Post by meng on 2007-01-08
1. Does cedega still work?
2. What languages besides English do you have on this system?

---

### Post by tito2502 on 2007-01-08
No, cedega won't start.

As far as I know I only have English; can I check?

---

### Post by tito2502 on 2007-01-08
When i try to launch VNC I get 

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:",
        LC_ALL = (unset),
        LANG = "en_GB.ISO-8859-15"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

You will require a password to access your desktops.

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:",
        LC_ALL = (unset),
        LANG = "en_GB.ISO-8859-15"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```

---

### Post by Sandlst on 2007-01-15
Have yall tried this?
[http://ubuntuforums.org/showthread.php?t=325102&highlight=locale+error]("http://ubuntuforums.org/showthread.php?t=325102&highlight=locale+error")

---

