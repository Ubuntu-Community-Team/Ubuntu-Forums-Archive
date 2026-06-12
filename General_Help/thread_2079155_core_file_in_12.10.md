---
title: "core file in 12.10?"
date: 2012-11-01
forum: General Help
---

### Post by tomhorsley on 2012-11-01
I run a program that is intended to dump core so I can test software that reads core file. On ubuntu 12.10, it says "core dumped", but there is no core file.

I found the silly /proc/sys/kernel/core_pattern file was piping things to some nonsense named "apport", so I removed apport from the system, and the core_pattern file went back to just saying "core", but I still get no core files.

How can I eradicate all the "helpful" crap and put things back the way they always were?

---

### Post by tomhorsley on 2012-11-01
OK, I finally found it. Even though apport was removed, apparently the upstart init file was still there. I went ahead and reinstalled apport then, as root did:

echo manual > /etc/init/apport.override

So obvious :-).

But I now get actual core files.

---

