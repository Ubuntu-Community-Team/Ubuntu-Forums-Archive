---
title: "Filedate changes when files are copied"
date: 2008-06-01
forum: General Help
---

### Post by Amoko on 2008-06-01
Hi,
My very first question:

How can I avoid changing the date of the files  when I copy them from Windows?

:confused: Amoko

---

### Post by Monicker on 2008-06-01
Use the -p option, which should preserve the timestamps.
```

cp -p somefile /destination
```

---

### Post by Amoko on 2008-06-02
> **Monicker said:**
> Use the -p option, which should preserve the timestamps.
```

cp -p somefile /destination
```
Hi Monicker,

Thanks for a swift answer; I had hoped for something in one of the graphic programs though :-) Amoko

---

