---
title: "Tilde (~) character now one keystroke more away"
date: 2008-05-14
forum: General Help
---

### Post by pertti on 2008-05-14
Hi,

This is a bit obscure, but it's something that has bothered me since I upgraded to Hardy. Before Hardy, when I wanted to write a tilde (~) character, e.g. in a terminal for referring to my home folder, I just hit AltGr + 4 and the ~ appeared right away.

Now when I hit AltGr + 4 no character is shown, but rather I have to press space (or AlgGr + 4 again) to write the ~. Of course, this way of entering the ~ is useful for writing characters such as ã or õ, but since I have never had that need I'd like to turn this behavior off.

I'm using the Spanish locale (ES_es) and the regular Spanish keyboard distribution. I've taken a look at the options on the keyboard preferences but didn't find any option to change this. This happens both in Gnome Terminal and in a TTY terminal, so I guess it's not related to Gnome.

Is there a way to restore the old ~ behavior?

Thanks in advance

---

### Post by legg on 2008-08-27
I'm also interested in a solution to this problem in 8.04. The problem is not present in previous versions.

Keyboard configured as spanish, generic PC 105 intl.

locale output:
```

LANG=es_MX.UTF-8
LC_CTYPE="es_MX.UTF-8"
LC_NUMERIC="es_MX.UTF-8"
LC_TIME="es_MX.UTF-8"
LC_COLLATE="es_MX.UTF-8"
LC_MONETARY="es_MX.UTF-8"
LC_MESSAGES="es_MX.UTF-8"
LC_PAPER="es_MX.UTF-8"
LC_NAME="es_MX.UTF-8"
LC_ADDRESS="es_MX.UTF-8"
LC_TELEPHONE="es_MX.UTF-8"
LC_MEASUREMENT="es_MX.UTF-8"
LC_IDENTIFICATION="es_MX.UTF-8"
LC_ALL=

```

---

### Post by mixmaster on 2008-08-27
I'm thrashing in the dark a bit here, as I don't use spanish keyboard layouts but ...

keyboard behaviour can be altered with xmodmap, and it sounds as though
the spanish map has changed between releases.  If you can boot an older version you can dump the map with xmodmap -pke.  Comparing that to an output
of the current version should locate the change and you can feed this back
into xmodmap to reset the keys to the way you like them.

---

### Post by legg on 2008-08-27
It worked!! Thank you.

I'm attaching the output of version 7.10, the file should be renamed to .xmodmaprc and placed in the home directory (according to xmodmap man page).

---

