---
title: "Im getting an error with /dev/dsp busy how do I investigate"
date: 2008-06-24
forum: General Help
---

### Post by darkworld on 2008-06-24
/dev/dsp.....digital signal processing? if im being told its busy or being used by another process....what commands can I use to investigate, by what and where? Thanks in advance.

---

### Post by iaculallad on 2008-06-24
> **darkworld said:**
> /dev/dsp.....digital signal processing? if im being told its busy or being used by another process....what commands can I use to investigate, by what and where? Thanks in advance.

Try to look at your /var/log/messages file.

```
cat /var/log/messages
```

---

