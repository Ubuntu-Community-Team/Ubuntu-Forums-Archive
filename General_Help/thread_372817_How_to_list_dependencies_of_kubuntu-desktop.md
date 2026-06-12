---
title: "How to list dependencies of kubuntu-desktop?"
date: 2007-02-28
forum: General Help
---

### Post by Dave / Mosaic on 2007-02-28
Is there a straightforward way to have apt-get, or some other program, list out the complete tree of dependencies for the kubuntu-desktop metapackage (or ubuntu-desktop, or any particular package, for that matter...)?

I'm wanting to do this, so as to get to a cleaner install with a minimum of unnecessary stuff on my system.

Thanks...

---

### Post by IcemanV9 on 2007-02-28
Yes, you can! :)

```
aptitude show kubuntu-desktop
aptitude show ubuntu-desktop
```

---

### Post by Dave / Mosaic on 2007-02-28
okay - thanks much; will try that --dave

---

### Post by strabes on 2007-02-28
For the future, most commands have an option "--help" that you can write after it to get information about the command. In this case you would run "aptitude --help"

Running that command tells you about "show" etc

---

