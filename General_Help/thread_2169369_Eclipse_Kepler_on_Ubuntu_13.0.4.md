---
title: "Eclipse Kepler on Ubuntu 13.0.4"
date: 2013-08-21
forum: General Help
---

### Post by NGSG on 2013-08-21
dear experts,
I recently installeed the latest Eclipse 4.3 (Kepler) on my laptop which runs Ubuntu 13.0.4 (Linux pcclratl12 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:19:35 UTC 2013 i686 i686 i686 GNU/Linux)
There is obviously something wrong in what i did, since the eclipse command line keeps crashing with a seg.fault.
Did someone by chance experience such an issue and provide some guideline on how to solve this issue?
thanks in advance.

PS: i put below the output and the crash when i try to resize the eclipse window.
> eclipse 
No bp log location saved, using default.
[000:000] Browser XEmbed support present: 1
[000:000] Browser toolkit is Gtk2.
[000:000] Using Gtk2 toolkit
No bp log location saved, using default.
[000:028] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[000:028] No bp log location saved, using default.
[000:028] Browser XEmbed support present: 1
[000:028] Browser toolkit is Gtk2.
[000:028] Using Gtk2 toolkit
[000:000] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[000:000] No bp log location saved, using default.
java version "1.7.0_25"
OpenJDK Runtime Environment (IcedTea 2.3.10) (7u25-2.3.10-1ubuntu0.13.04.2)
OpenJDK Server VM (build 23.7-b01, mixed mode)
Segmentation fault (core dumped)

---

### Post by jjaison-daniel on 2013-08-22
check eclipse bug you might fall into that [https://bugs.eclipse.org/bugs/show_bug.cgi?id=404776](https://bugs.eclipse.org/bugs/show_bug.cgi?id=404776)
Workaround is add the following in eclipse.ini
```
-Dorg.eclipse.swt.browser.DefaultType=mozilla
```

---

### Post by NGSG on 2013-08-22
Thanks for the hint. I tried it and reverted back to the latest Java. It seems to fix it, since i could not reproduce the crash anymore.
thanks again for the fast feedback.

---

