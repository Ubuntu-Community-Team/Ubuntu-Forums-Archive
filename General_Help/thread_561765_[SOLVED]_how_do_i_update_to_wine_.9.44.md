---
title: "[SOLVED] how do i update to wine .9.44"
date: 2007-09-28
forum: General Help
---

### Post by RuB3N on 2007-09-28
i have wine .9.33 but for guildwars to work fully i need to updaate it somehow?

if someone knows what to type in the terminal or how to get that update......







thanks for your time

---

### Post by IcemanV9 on 2007-09-28
Add "deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) <your release> main" in your source.list.

```
sudo aptitude update; sudo aptitude upgrade
```

It should upgrade your wine automatically.

---

### Post by RuB3N on 2007-09-28
thanks a buntch

---

