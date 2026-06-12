---
title: "latex style file became broken, can't find font?"
date: 2008-03-16
forum: General Help
---

### Post by gnychis on 2008-03-16
Hi all,

I've used a style file, sig-alternate-10pt for quite some time for writing papers using latex.  As of the past month, something must have changed in the Ubuntu repositories that has caused my style file to break.  I get the error:
```

kpathsea: Running mktexmf ptmb8t
! I can't find file `ptmb8t'.
<*> ...:=ljfour; mag:=1; nonstopmode; input ptmb8t

```

It seems as though it can't find the font ptmb8t, but it exists on my system:
```

/usr/share/texmf/tex4ht/ht-fonts/alias/adobe/times/ptmb8t.htf

```

Any ideas?

Thanks!

---

### Post by gnychis on 2008-03-16
got it, i needed tetex-bin and tetex-base rather than texlive-base

---

### Post by hugmenot on 2008-03-17
Or texlive-fonts-recommended. TeTeX is obsolete.

---

