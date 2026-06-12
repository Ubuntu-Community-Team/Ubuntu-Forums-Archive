---
title: "Ubuntu 16.04LTS how to capture boot time errors"
date: 2020-09-23
forum: General Help
---

### Post by Frank P on 2020-09-23
When the server boots the output scrolls past to fast to read. Is there a way to capture it so it can be read

Thanks

---

### Post by #&amp;thj^% on 2020-09-23
To see information from your most recent boot, run

```
journalctl -b
```

To see the details that were logged during a previous boot, just in case you need to compare them with your most recent, run

```
journalctl --list-boots 
```
I thought 16.04 was eol

---

### Post by Frank P on 2020-09-23
Thanks, I'll do that
16.04lts server has til April 2021

Frank

---

### Post by #&amp;thj^% on 2020-09-23
I thought wrong then.:) Not the first nor the last i'm afraid. LOL
Regards

---

