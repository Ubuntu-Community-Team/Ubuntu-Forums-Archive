---
title: "Ubuntu gutsy server and locales.."
date: 2007-12-06
forum: General Help
---

### Post by googlah on 2007-12-06
Hey guys,

Just switched from Debian to Ubuntu Gutsy. The way you change locales in the terminal doesn't seem to be quite right.. :(  'dpkg-reconfigure locales' just re-generates the selected locales and you're actually not able to choose from any as in Debian.

Please, I want "åäö" to start working. Where do I start? the package "localeconf" doesn't seem to be around either.

---

### Post by googlah on 2007-12-06
Okay.. solved it. This is how I did:

My /etc/environment looks like this
```

LANG="sv_SE.ISO-8859-1"
LANGUAGE="sv_SE.ISO-8859-1"
LC_CTYPE="sv_SE.ISO-8859-1"

```

My /etc/default/console-setup looks like this
```

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.
XKBMODEL="pc105"
XKBLAYOUT="se"
XKBVARIANT=""
XKBOPTIONS=""

```

enjoy :)

---

### Post by smyrman on 2008-03-20
Hi. Another way to change your locale settings, is to edit this file: **/etc/default/locale** This seams to be loaded after the /etc/enviorment file(PS! This goes for ubuntu based distroes, and maybe debian, but not others. In ubuntu 8.04, this seams io be the standard file for locale settings).
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
LC_NUMERIC="en_GB.UTF-8" # 100 000.02 en use 'dot' as decimal point
LC_MONETARY="nn_NO.UTF-8" # kr
LC_TIME="en_DK.UTF-8"   # iso-8601, 24h + weeks start Mon + format yyyy-m$
LC_CTYPE="nn_NO.UTF-8"  # which characters are letter
LC_COLLATE="nn_NO.UTF-8" # sort order, eg. a-ring; is after z
LC_NAME="nn_NO.UTF-8"
LC_ADDRESS="nn_NO.UTF-8"
LC_TELEPHONE="nn_NO.UTF-8"

```

---

