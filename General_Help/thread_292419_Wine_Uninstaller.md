---
title: "Wine Uninstaller"
date: 2006-11-03
forum: General Help
---

### Post by musther on 2006-11-03
I've just installed wine in edgy, installed a piece of software which didn't work and now I want to remove it.  I used to access the wine-uninstaller by typing "wine uninstall", but now this happens.

```
musther@dominus:~$ wine uninstall
wine: could not load L"c:\\windows\\system32\\uninstall.exe": Module not found
```

Am I missing some extra wine packages or something?

Cheers

---

### Post by ~LoKe on 2006-11-03
```
sudo dpkg -r wine
```

---

### Post by musther on 2006-11-03
Sorry, maybe I wasn't clear, I didn't want to remove wine, I wanted to open the uninstaller in order to remove windows software which I was running through wine.

---

### Post by ~LoKe on 2006-11-03
```
wine uninstaller
```

---

### Post by musther on 2006-11-03
Ah, thanks!

---

