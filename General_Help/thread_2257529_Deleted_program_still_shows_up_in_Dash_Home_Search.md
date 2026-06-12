---
title: "Deleted program still shows up in Dash Home Search"
date: 2014-12-20
forum: General Help
---

### Post by michael-piziak on 2014-12-20
Any way to get rid of icon of deleted program that still shows up in Dash Home ?
Program:  Epiphany (I installed then unistalled in software center)

---

### Post by deadflowr on 2014-12-20
Open privacy and run clear history.

Or do you mean it stills shows when you run a search.

---

### Post by mc4man on 2014-12-20
remove this package - 
epiphany-browser-data
that's the package where the .desktop is installed from.

---

### Post by michael-piziak on 2014-12-20
Yes only shows when I run a search in Dash Home
I tried clear history in Privacy - didn't clear it.
Dash thinks it's an application and also thinks it's installed

---

### Post by michael-piziak on 2014-12-20
> **mc4man said:**
> remove this package - 
epiphany-browser-data
that's the package where the .desktop is installed from.

what exactly do i type in terminal, "remove epiphany-browser data"  ?

---

### Post by mc4man on 2014-12-20
This will do 
```
sudo apt-get purge epiphany-browser-data
```

---

### Post by michael-piziak on 2014-12-20
> **mc4man said:**
> This will do 
```
sudo apt-get purge epiphany-browser-data
```

That did it.

Marking this thread as solved.

---

