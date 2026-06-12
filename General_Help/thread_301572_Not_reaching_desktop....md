---
title: "Not reaching desktop..."
date: 2006-11-17
forum: General Help
---

### Post by Umut Ya&#351;ar on 2006-11-17
While booting, just after I type username and password, the desktop appeares once but after 10 sceonds it goes away and username&password screen reappeares.

I faced with that problem yesterday but I could reach the desktop after the 5th try. But today, I couldn't manage to reach. What to do? I am not really familiar with ubuntu...

Thanks...

---

### Post by taurus on 2006-11-17
Boot into recovery mode from GRUB and at the prompt, paste the output of this command here, assuming john is your user name (and remove files or directories that you don't want others to see).

```
ls -la /home/john
```

---

