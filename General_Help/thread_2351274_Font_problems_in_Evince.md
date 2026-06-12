---
title: "Font problems in Evince"
date: 2017-02-01
forum: General Help
---

### Post by rgaddi on 2017-02-01
I'm having a problem where Evince is failing to display some characters in some PDF files.  Ghostview shows them fine.  Any ideas?

Evince:
[ATTACH=CONFIG]273472[/ATTACH]

GV:
[ATTACH=CONFIG]273474[/ATTACH]

Original PDF is at [http://www.ti.com/lit/ds/symlink/tps2660.pdf](http://www.ti.com/lit/ds/symlink/tps2660.pdf); it seems I can't attach it.

I'm running Xubuntu 16.04.
```

$ lsb_release -a
LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

```

---

### Post by ajgreeny on 2017-02-01
Perhaps try a different pdf reader, eg okular, qpdfview, xpdf; there are plenty available, and I have also occasionally found that evince does not display some files properly.

Could the problem be related to the fonts installed on your system not including those in and therefore needed by the PDF file viewer?

---

