---
title: "no more space on root&gt; syslog full with cmr10.tfm: File corrupted, or not a TFM file"
date: 2015-05-07
forum: General Help
---

### Post by B_Tutzer on 2015-05-07
Hi,
I am running Ubuntu for a few months now and today I got a warning that my root file system was full. I checked and found out the reason was an overfull /var/log/syslog (~40GB). The whole file was full of the following error message:
```

May  7 11:47:40 benLIN gnome-session[1701]: page: Error: /usr/share/texlive/texmf-dist/fonts/tfm/public/cm/cmr10.tfm: File corrupted, or not a TFM file
May  7 11:47:40 benLIN gnome-session[1701]: page: Warning: font `cmr10' not found, trying metric files instead

```
I tried reinstalling texlive and hoped the file would be ok again, but it didn't help.
The messages won't appear during the first few minutes after a reboot, but after a few minutes they start showing up multiple times a second.
Any idea what this might be?

---

### Post by dino99 on 2015-05-07
maybe you can find something related to 'fonts' inside /usr/share/doc/texlive-doc/latex/
[http://www.tug.org/interest.html](http://www.tug.org/interest.html)

---

