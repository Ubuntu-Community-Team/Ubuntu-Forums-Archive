---
title: "Strange MS something font error"
date: 2007-01-01
forum: General Help
---

### Post by Unreallinux on 2007-01-01
Every time I try to download a program from the add/remove thing I get errors about how it couldn't connect to some source forge servers for MS fonts...

I think this started when I used automatix because it had an error while installing the fonts.(but I cant choose to uninstall them in automatix since it didn't finish.) 

How do I fix this?

---

### Post by Unreallinux on 2007-01-02
Anyone know how I can make it stop?!

---

### Post by arnieboy on 2007-01-02
> **Unreallinux said:**
> Every time I try to download a program from the add/remove thing I get errors about how it couldn't connect to some source forge servers for MS fonts...

I think this started when I used automatix because it had an error while installing the fonts.(but I cant choose to uninstall them in automatix since it didn't finish.) 

How do I fix this?
try doing:
```
sudo apt-get remove msttcorefonts
```

---

### Post by Unreallinux on 2007-01-02
Thank you so much, it worked!

---

