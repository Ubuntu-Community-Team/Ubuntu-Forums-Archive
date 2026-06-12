---
title: "system hangs on boot"
date: 2016-12-30
forum: General Help
---

### Post by hyburn on 2016-12-30
systemd-analyze blame returns:
38.507s dev-sda2.device

how can I reduce this and achieve a faster boot?

---

### Post by cariboo on 2016-12-30
You'll have show us the output of the command you ran. The easiest way is to pipe the output to a text file:

```
systemd-analyze blame > blame txt
```

Then attach the text file to your next post.

**edit**: My output may be a lot shorter than yours, as my system boots in about 5 seconds.

---

