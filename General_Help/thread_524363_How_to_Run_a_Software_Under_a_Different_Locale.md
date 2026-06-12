---
title: "How to Run a Software Under a Different Locale"
date: 2007-08-13
forum: General Help
---

### Post by Ran.Rutenberg on 2007-08-13
Hi,

I've just installed Kubuntu, and I can't make launch softwares in a different locale then English. Sometimes I need to run something in Hebrew, but it just doesn't work (neither does it work for any other language but English).

The command I'm trying to use is:
```
LC_ALL=he_IL foo
```


My locale settings are:

```
ran@Ran-PC:~$ locale -a
C
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

```


Thanks,
Ran Rutenberg

---

### Post by yorkie on 2007-08-13
I s SCIM input method setup  {under system /prefs } what your looking for
heres some info [http://www.scim-im.org/](http://www.scim-im.org/)

---

### Post by Ran.Rutenberg on 2007-08-14
I don't think I need to change the input method. All I need is to be able to sometimes launch software with a different UI language then the default one (English).
When I had gentoo all I had to do was to type:
```
LC_ALL=he_IL foo
```

and foo would be launched in Hebrew instead of English.

---

