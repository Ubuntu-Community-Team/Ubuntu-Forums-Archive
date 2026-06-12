---
title: "Is it possible to slowdown application?"
date: 2006-11-23
forum: General Help
---

### Post by Mis_Uszatek on 2006-11-23
Ok. I have an application XYZ.
I start it, and it uses 100% of my proc.
Is it possible to start it in some special mode, so application XYZ will use (for example) only 20% of my proc.
So,is it possible, that linux will give to application XYZ only 20% of proc-power?

---

### Post by bollix47 on 2006-11-23
Not sure if you can do exactly what you're asking but you can lower the priority of XYZ so that it doesn't interfere with other applications by using the [nice command]("http://www.ss64.com/bash/nice.html").

---

