---
title: "Does Ubuntu support OpenType Collection (.ttc) fonts?"
date: 2015-01-14
forum: General Help
---

### Post by TriforceOfKirby on 2015-01-14
Can I install a OTC font on Ubuntu? If so where would it go to be installed system-wide? /usr/share/fonts/opentype?

---

### Post by Dennis N on 2015-01-14
"OpenType Collection Fonts" I take to mean Opentype fonts? I have some opentype and put them in ~/.fonts, but system wide would be in /usr/share/fonts or a subdirectory of that as you have indicated. Opentype works fine. But the opentype font files I know have an extension of .otf, not .ttc - don't know about .ttc

---

### Post by TriforceOfKirby on 2015-01-14
No I actually mean OpenType Collection fonts, .ttc is the file extension for TrueType Collection fonts, OpenType Collection Fonts share the same file extension. As far as I know it's more commonly used with asian fonts. Source Han Sans is an example of a font that comes as an OTC: [https://github.com/adobe-fonts/source-han-sans](https://github.com/adobe-fonts/source-han-sans)

---

### Post by TriforceOfKirby on 2015-01-15
The documentation for Source Han Sans says to use the .ttc file on OSx v10.8 or greater, and to use the .otf files on Windows, but doesn't mention Linux. So I just decided to try putting the Source Han Sans .ttc in /usr/share/fonts/opentype/adobe and ran sudo fc-cache -f -v, hoping nothing would break. It seems to work just fine, I tested it with LibreOffice.

---

