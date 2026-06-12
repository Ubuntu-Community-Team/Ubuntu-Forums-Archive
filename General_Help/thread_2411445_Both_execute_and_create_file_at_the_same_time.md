---
title: "Both execute and create file at the same time"
date: 2019-01-30
forum: General Help
---

### Post by raleigh3 on 2019-01-30
Is there a way to get this to show the results as well as create a file?

```
systemd-analyze >> boot_up_time.txt
```

---

### Post by spjackson on 2019-01-30
```

systemd-analyze | tee -a boot_up_time.txt

```

---

