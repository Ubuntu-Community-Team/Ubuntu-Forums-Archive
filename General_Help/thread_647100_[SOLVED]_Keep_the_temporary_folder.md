---
title: "[SOLVED] Keep the temporary folder"
date: 2007-12-21
forum: General Help
---

### Post by mahsheed on 2007-12-21
Hey!
I dont know if this is possible but i somehow want to keep the things that are stored in the temporary folder while i surf the net ( for example youtube videos ) using firefox.

I dont want them to get deleted the moment i restart my computer so that i dont have to go on downloading them completely again and using up my limited the MB of downloading i paid for.

---

### Post by dcstar on 2007-12-21
> **mahsheed said:**
> Hey!
I dont know if this is possible but i somehow want to keep the things that are stored in the temporary folder while i surf the net ( for example youtube videos ) using firefox.

I dont want them to get deleted the moment i restart my computer so that i dont have to go on downloading them completely again and using up my limited the MB of downloading i paid for.

```
gksudo /etc/default/rcS
```

Change TMPTIME=0 to TMPTIME=whatever days you want to keep tmp files.

---

