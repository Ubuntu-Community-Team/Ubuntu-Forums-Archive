---
title: "Gtk-Warning with hplip GUI"
date: 2018-01-28
forum: General Help
---

### Post by engine on 2018-01-28
well beyond my comprehension, as someone who just wants to be able to print &#8230; first, warnings that there was no GUI installed for hplip. Installed the required GUI. Now, messages about fonts, locales and who knows what else:

```
(process:3938): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Fontconfig warning: ignoring mate.desktop: not a valid language tag
"sni-qt/3938" WARN  13:00:56.605 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE
```

Do I stand any chance of correcting these errors? if so, what do I need to do?

Thanks in advance!

---

### Post by managerceo1 on 2018-01-28
First make sure your library language is installed

sudo apt-get install language-pack-en-base,


Then, as superuser, shorten the work by allowing Ubuntu to automatically configure them:

sudo dpkg-reconfigure locales

---

