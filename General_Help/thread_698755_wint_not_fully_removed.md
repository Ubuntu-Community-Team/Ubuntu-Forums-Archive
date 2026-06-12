---
title: "wint not fully removed?"
date: 2008-02-16
forum: General Help
---

### Post by maphco on 2008-02-16
I removed Wine using
```
sudo apt-get remove wine
```

However, when I go to applications, Wine is still listed in the drop down.  Anyone know of why it wasn't removed, and how do I remove it from there?

---

### Post by overdrank on 2008-02-16
> **maphco said:**
> I removed Wine using
```
sudo apt-get remove wine
```

However, when I go to applications, Wine is still listed in the drop down.  Anyone know of why it wasn't removed, and how do I remove it from there?

HI and have you tried 
```
sudo apt-get remove wine --purge
sudo apt-get autoclean
sudo apt-get autoremove

```

---

### Post by maphco on 2008-02-17
It's still there.

---

### Post by quanumphaze on 2008-02-17
Try removing the .wine folder in your home directory.

If it still persists then you could try to remove it from the menu manually.
[LIST=1]Right click Applications
[*]Click Edit Menus
[*]Click Applications in the left pane if it isn't already
[*]Right click Wine and click Delete
[/LIST]
Can't help any more without trying it myself first ;)

---

