---
title: "Where is the Bitstream Charter font file?"
date: 2008-05-19
forum: General Help
---

### Post by pistos on 2008-05-19
I searched the forums but was not able to find the answer to this question. In 8.04 the fonts don't appear to be in quite the same places as previous versions of the OS. I am looking for the font file for Bitstream Charter, in particular. Thank you for help.

---

### Post by chandra on 2008-05-19
```
dpkg -L texlive-fonts-recommended | grep charter
```

---

### Post by pistos on 2008-05-19
Thanks for the reply. Unfortunately, that does not do the trick. It returns stating that texlive is not installed on my system. But, I know the Charter font is installed because I use it quite often.  :confused:

---

### Post by p_quarles on 2008-05-19
On the system I'm using right now (Debian, so should be similar if not the same), they're in
```
/usr/share/fonts/X11/100dpi
```

---

### Post by pistos on 2008-05-19
Are those screen fonts? Where are the printer fonts,i.e., truetype or type 1 versions?

---

### Post by chandra on 2008-05-20
For what it is worth:

1. The files in /usr/share/fonts/X11/100dpi are gzipped X11 Portable Compiled Font data.

2. The files installed from texlive are PostScript Type 1 fonts.

3. If you had TTF fonts, were they from Corel Draw? The Bitstream Charter fonts have been known to be bundled with Corel Draw products when they were available for Linux.

---

### Post by pistos on 2008-05-20
Thanks for the info.

---

### Post by fmmarzoa on 2010-09-19
> **pistos said:**
> Thanks for the reply. Unfortunately, that does not do the trick. It returns stating that texlive is not installed on my system. But, I know the Charter font is installed because I use it quite often.  :confused:

apt-get install texlive-fonts-recommended
dpkg -L texlive-fonts-recommended | grep charter

---

