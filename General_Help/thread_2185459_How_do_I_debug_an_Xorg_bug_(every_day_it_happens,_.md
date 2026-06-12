---
title: "How do I debug an Xorg bug (every day it happens, why?)"
date: 2013-11-02
forum: General Help
---

### Post by Jim_Granite on 2013-11-02
I get this dialog to send a bug report to Canonical every day; but what can "I" do to debug myself what the problem is?

[ATTACH=CONFIG]247507[/ATTACH]

---

### Post by Jim_Granite on 2013-11-02
Actually, it seems to be a different crash that I just got now:
- bamfdaemon
- compiz
[ATTACH=CONFIG]247515[/ATTACH]

---

### Post by Bucky Ball on 2013-11-03
Are you doing regular updates? 13.10, problems to be expected, may be fixed with an update.

---

### Post by Jim_Granite on 2013-11-05
> **Bucky Ball said:**
> Are you doing regular updates? 13.10, problems to be expected, may be fixed with an update.

Yes. I have been accepting ALL update requests from the operating system. 
It hung yesterday, and the day before - but - today (it's before noon), it's working fine (so far).

If only I could debug these errors ... 
[ATTACH=CONFIG]247587[/ATTACH]

---

### Post by philinux on 2013-11-05
Have a look at the file xsession-errors.

```
cat ~/.xsession-errors | pastebinit
```

---

