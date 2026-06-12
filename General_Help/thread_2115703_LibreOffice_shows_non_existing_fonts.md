---
title: "LibreOffice shows non existing fonts"
date: 2013-02-13
forum: General Help
---

### Post by ubunet on 2013-02-13
Hi,

I **uninstalled** the Microsoft Fonts, and the LibreOffice shows some of this fonts (Arial, Times New Roman) in the documents edited. I changed the default font of LibreOffice and of the this documents to *Liberation Sans* but, when I close e open the document, the name o MS font show again.

I rebuild the cache and reboot but didn't work
```
sudo fc-cache -f -v
```

Ubuntu 12.10 x86

---

### Post by coffeecat on 2013-02-13
> **ubunet said:**
> I **uninstalled** the Microsoft Fonts,

How did you uninstall? By uninstalling the ttf-mscorefonts-installer package or by deleting the actual font files themselves? If you only uninstalled the ttf-mscorefonts-installer package the fonts will still be there. The package is simply an installer which downloads the fonts at installation time.

Have a look in /usr/share/fonts/truetype/msttcorefonts. If you have a number of ttf files in there (probably 60), they need to be deleted after which you would need to run fc-cache again.

---

### Post by ubunet on 2013-02-13
The folder */usr/share/fonts/truetype/msttcorefonts* does **not** exists.

EDIT:

The command line below remove the installer and directory with fonts:
```
sudo apt-get **purge** ttf-mscorefonts-installer
```However, if I open a **new** document, I didn't see the MS fonts. Only in edited documents.

---

### Post by hawthornso23 on 2013-02-14
Sometimes fonts are stored in the document so that it can be read even if you send it to someone who doesn't have your font. Perhaps that is what you are seeing.

---

