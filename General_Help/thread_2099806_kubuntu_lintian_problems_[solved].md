---
title: "kubuntu lintian problems [solved]"
date: 2012-12-30
forum: General Help
---

### Post by dumbbeatnix on 2012-12-30
I am running kubuntu KDE Platform Version 4.9.3 and got some errors concerning lintian 2.5.11

They were basically errors to do with the update process, it wouldn't update on the gui provided.

The simple way around this is to open a terminal and type:

```
sudo apt-get update
```

This should let the system put all the packages in the right place, what you'll be left with is Wine updates after that [if you have wine installed].

:popcorn:

---

