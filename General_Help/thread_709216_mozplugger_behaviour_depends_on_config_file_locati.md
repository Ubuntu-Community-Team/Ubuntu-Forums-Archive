---
title: "mozplugger behaviour depends on config file location"
date: 2008-02-27
forum: General Help
---

### Post by barna on 2008-02-27
Hi,
I have added an extra entry to /etc/mozpluggerrc:

```

image/hpgl:plt,hpgl,hpg:HPGL file
        noisy swallow(hpglview.bin) : hpglview $file

```

but it does not work. However, if I write it into ~/.mozilla/mozpluggerrc, then it DOES work (but since this file seems to override /etc/mozpluggerrc, I only have this single mimetype handled by mozplugger. Any idea?

Thanks
Daniel

---- forget it, I edited the wrong file

---

