---
title: "Serif font in some websites?"
date: 2024-04-16
forum: General Help
---

### Post by cbiweb on 2024-04-16
During my migration to Ubuntu from Windows, I notice that the font of some websites are a serif font like Times New Roman.  I use these sites often, and they've always been sans-serif (Arial or something similar).

This is happening in the Linux versions of the browsers I use.  The Windows version are all fine.

Is there a top secret setting somewhere? :lol:

---

### Post by Impavidus on 2024-04-19
Web sites can ask your browser to use a particular font and if that font isn't installed on your system, the browser will fall back to a default. Your Windows system has Microsoft fonts installed, your Ubuntu system hasn't. Microsoft's license doesn't allow bundling them with Ubuntu.

There are two ways to deal with this. You can get into your browser settings and set a sans serif font as the default, or you can install the Microsoft fonts. The easy way is to install the package ttf-mscorefonts-installer from the Ubuntu repositories. Many people install the package ubuntu-restricted-extras, which includes this package and some additional software with difficult licenses. You'll have to agree with the license during installation.

---

### Post by cbiweb on 2024-04-24
> **Impavidus said:**
> Web sites can ask your browser to use a particular font and if that font isn't installed on your system, the browser will fall back to a default. Your Windows system has Microsoft fonts installed, your Ubuntu system hasn't. Microsoft's license doesn't allow bundling them with Ubuntu.

There are two ways to deal with this. You can get into your browser settings and set a sans serif font as the default, or you can install the Microsoft fonts. The easy way is to install the package ttf-mscorefonts-installer from the Ubuntu repositories. Many people install the package ubuntu-restricted-extras, which includes this package and some additional software with difficult licenses. You'll have to agree with the license during installation.

Aha, okay.  That makes sense. Just seeing this now by chance, sorry I didn't respond before now.  Thanks!

---

