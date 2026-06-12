---
title: "Please help with local settings?"
date: 2008-03-15
forum: General Help
---

### Post by Rob2008 on 2008-03-15
How would i change my local settings ? 
Currency, language etc

Need to change them now i have installed

---

### Post by Amarsingh0793 on 2008-03-15
Try System > Preferences > Keyboard. I know that from there you can change your keyboard layout and stuff.

---

### Post by AndyCooll on 2008-03-15
There's also System > Administration > Language Support.

:cool:

---

### Post by smyrman on 2008-03-20
Hi. One of the better ways to change your locale settings, is to edit this file: **/etc/default/locale** (PS! This goes for ubuntu based distroes, and maybe debian, but not others).
For example, write this in a console:
```
$sudo nano /etc/default/locale
```

You wil here se somthing like:
```

LANG="en_GB.UTF-8"
LANGUAGE="en_GB:en:en_US:en"

```

Change this to what suites you best.

If you wander what options you have, write this in a console:
```
$locale -a
```

To see what locale the system is using, type this in a console:
```
$locale
```
**Install more:**

To add support for more languages, write this in a console (replace "xx" with something else):
```

$sudo aptitude install language-pack-xx

```

To se what options you have, write:
```

$aptitude search language-pack

```

Restart your computer for changes to take effect

**OPTIONAL:**
If you would like more advanced locale settings, you can add more lines to your **/etc/default/locale** file.

Example with partly norwegian locale:
```

LC_MESSAGES="en_GB.UTF-8" # language
LC_PAPER="nn_NO.UTF-8"   # a4, can't print without this
LC_MEASUREMENT="nn_NO.UTF-8" # metric system
LC_NUMERIC="en_GB.UTF-8" # 100 000.02 use 'dot' as decimal point
LC_MONETARY="nn_NO.UTF-8" # kr
LC_TIME="en_DK.UTF-8"   # iso-8601, 24h + weeks start Mon + format yyyy-m$
LC_CTYPE="nn_NO.UTF-8"  # which characters are letter
LC_COLLATE="nn_NO.UTF-8" # sort order, eg. "a-ring" is after z
LC_NAME="nn_NO.UTF-8"
LC_ADDRESS="nn_NO.UTF-8"
LC_TELEPHONE="nn_NO.UTF-8"

```

---

