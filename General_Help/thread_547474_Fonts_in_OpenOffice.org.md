---
title: "Fonts in OpenOffice.org"
date: 2007-09-10
forum: General Help
---

### Post by kirios on 2007-09-10
[COLOR="DarkRed"]How do I get OpenOffice.org to recognize and use other fonts (like msttcorefonts)?[/COLOR]

---

### Post by Perfex on 2007-09-10
As long as it is a font file, and it is in .fonts in your home folder I don't know why it wouldn't recognize it.

---

### Post by eggdeng on 2007-09-10
If not already installed, ```
sudo apt-get install msttcorefonts
```
To make available ```
sudo fc-cache -f -v
```

---

