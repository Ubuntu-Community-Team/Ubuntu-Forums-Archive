---
title: "Finding disk-hog packages"
date: 2008-04-13
forum: General Help
---

### Post by thk on 2008-04-13
Is there a way to list the disk space used by installed packages? I'd like to find the 10 or 20 with the greatest disk usage. (I keep a pair of ~5GB partitions and alternate between them with each upgrade cycle. Hardy is way bigger than Gutsy!)

---

### Post by thk on 2008-04-13
Answering my own question. Here is one solution.

```
for pkg in `dpkg -l | perl -ne 'if (/^ii\s+(\S+)/){print "$1 "}'`; do for f in `dpkg -L $pkg`; do if test -f $f; then stat -c "%s" $f; fi; done | perl -ne 'BEGIN{$x=0};$x+=$_;END{print"$x "}'; echo $pkg; done | sort -n | tail -n 40
```
```

25583032 eclipse-platform
26608769 openoffice.org-help-en-gb
26992241 openoffice.org-help-en-us
28394414 atlas3-sse2
31665343 emacs21-common
31968292 linux-headers-2.6.24-12
31984244 sun-java6-jdk
32519775 linux-headers-2.6.24-14
32519892 linux-headers-2.6.24-15
34977495 libgl1-mesa-dri
45691212 linux-restricted-modules-2.6.24-12-generic
45910919 linux-restricted-modules-2.6.24-14-generic
45910990 linux-restricted-modules-2.6.24-15-generic
52318054 googleearth
55767449 linux-image-2.6.24-14-generic
55792052 linux-image-2.6.24-12-generic
72156328 acroread
80583826 sun-java6-bin
112818490 openoffice.org-core

```

---

