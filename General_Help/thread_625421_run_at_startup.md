---
title: "run at startup"
date: 2007-11-28
forum: General Help
---

### Post by jasonpeinko on 2007-11-28
Everytime i start my compter i need to run this command for wireless to work:
```

suod modprobe ndiswrapper

```
when i add it to the sessions startup it does not do anything.

---

### Post by Tenken on 2007-11-28
You could try adding ndiswrapper to your system start up programs. I think Ubuntu uses the /etc/rc.d/rc.local file.

---

### Post by qqzhenyi on 2007-11-28
is it somewhere inside the /etc/modprobe.d/ folder? Sorry I can't remember

---

