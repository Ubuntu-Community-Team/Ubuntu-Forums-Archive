---
title: "multisession cd copy"
date: 2008-03-14
forum: General Help
---

### Post by cdenley on 2008-03-14
How do I copy a multisession CD with gutsy? I tried the Ubuntu disc copy frontend. I tried this command:
```

cdrdao copy --source-device 1,0,0 --device 3,0,0

```
Both give me the same results.
```

$ cdrdao disk-info --device 1,0,0
...
CD-RW                : no
Total Capacity       : n/a
CD-R medium          : n/a
Recording Speed      : n/a
CD-R empty           : no
Toc Type             : CD-DA or CD-ROM
Sessions             : 2
Last Track           : 14
Appendable           : no

```

```

$ cdrdao disk-info --device 3,0,0
...
CD-RW                : no
Total Capacity       : n/a
CD-R medium          : Taiyo Yuden Company Limited
                       Long Strategy Type, e.g. Cyanine
Recording Speed      : n/a
CD-R empty           : no
Toc Type             : CD-DA or CD-ROM
Sessions             : 1
Last Track           : 13
Appendable           : no

```

---

