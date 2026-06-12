---
title: "What permissions on /var?"
date: 2007-01-11
forum: General Help
---

### Post by Nonno Bassotto on 2007-01-11
It seems that [Evince is not able to create font for my dvis]("http://www.ubuntuforums.org/showthread.php?t=336234"). According to the terminal output it should be due to an incorrect permission on the /var/cache directory
```

kpathsea: Running mktexpk --mfmode / --bdpi 600 --mag 1+0/600 --dpi 600 cmtt8
mkdir: impossibile creare la directory `././var/cache/fonts': Permesso negato
mktexpk: mktexdir /var/cache/fonts/pk/ljfour/public/cm failed.
kpathsea: Appending font creation commands to missfont.log.
page: Warning: font `cmtt8' at 600x600 not found, trying `cmr10' instead
page: Warning: cmtt8: checksum mismatch (expected 3745761907, got 1274110073)
kpathsea: Running mktexpk --mfmode / --bdpi 600 --mag 1+0/600 --dpi 600 cmbx8

```

My current permissions for /var/cache are drwxr-xr-x. Should I modify this? Please post here your permissions for comparison.
Thank you

---

