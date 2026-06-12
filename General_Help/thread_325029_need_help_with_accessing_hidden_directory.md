---
title: "need help with accessing hidden directory"
date: 2006-12-24
forum: General Help
---

### Post by ishii255 on 2006-12-24
hey i installed a game with wine and it put the install dir in a hidden folder in home
```
/home/john/.wine/C:\Program Files\Diablo II
```
that may or may not be the correct directory it's located in
anyway, can someone tell me how to access hidden directories in ubuntu
hope it isn't too noodish of me to ask that.

---

### Post by dcstar on 2006-12-24
> **ishii255 said:**
> hey i installed a game with wine and it put the install dir in a hidden folder in home
```
/home/john/.wine/C:\Program Files\Diablo II
```
that may or may not be the correct directory it's located in
anyway, can someone tell me how to access hidden directories in ubuntu
hope it isn't too noodish of me to ask that.

Open Nautilus (the file browser), and: View-Show Hidden Files (or simply press CTRL-H)

---

### Post by taurus on 2006-12-24
```
cd "~/.wine/C:/Program Files/Diablo II"
ls -la
```

---

### Post by ishii255 on 2006-12-24
hey thanks a lot, i've been trying to figure that out all day. Merry Christmas!

---

