---
title: "wine issues"
date: 2007-02-14
forum: General Help
---

### Post by potti on 2007-02-14
i am running kubuntu 6.10
i cant find a wine tut that can help me 

any suggestions 

&

help with installing ventrilo 

please help me

---

### Post by energiya on 2007-02-14
just download wine via Synaptic and then run
```

winecfg

```
from a terminal window to configure it for your needs.
After that, just 
```

cd /path/to/your/file.exe
wine file.exe

```
or
```

wine /path/to/your/file.exe

```

When you install stuff in your C: (it is emulated) you can find it in /home/YOURUSERNAME/.wine/drive_c/

---

