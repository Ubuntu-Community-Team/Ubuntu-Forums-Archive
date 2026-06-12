---
title: "cant add remove apts"
date: 2008-03-26
forum: General Help
---

### Post by timetoballj on 2008-03-26
says to run dpkg --configure -a i dont know what that means can any one help me

---

### Post by kesman on 2008-03-26
do as it says, run
```

dpkg --configure -a

```
in terminal. You need to be superuser(root) to do this, so add **sudo** in front of the command, so it looks like this:
```

sudo dpkg --configure -a

```

---

### Post by kpkeerthi on 2008-03-26
It attempts to fix broken packages/dependencies in your installed packages. You actually need run ```
**sudo** dpkg --configure -a
``` in a terminal window.

---

### Post by timetoballj on 2008-03-27
i run the dpkg but know it said i have a broken package and to use "broken" filter to locate it how do i do that

---

