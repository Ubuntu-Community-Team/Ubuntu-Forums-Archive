---
title: "Adding firejail to chromium and firefox launcher"
date: 2017-05-28
forum: General Help
---

### Post by linuxyogi on 2017-05-28
I  have installed firejail. When I do ```
 firejail firefox
```  it works as expected but I want to add the firejail to the chromium and firefox launcher.

How do I do it ?

---

### Post by vasa1 on 2017-05-28
Modify the Exec= in copies of the firefox and chromium-browser .desktop files?

---

### Post by linuxyogi on 2017-05-29
> **vasa1 said:**
> Modify the Exec= in copies of the firefox and chromium-browser .desktop files?

Done. Thanks.

---

### Post by howefield on 2017-05-29
> **linuxyogi said:**
> Where are the .desktop files located ?

```
/usr/share/applications/
```

---

