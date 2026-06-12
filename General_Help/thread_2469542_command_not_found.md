---
title: "command not found"
date: 2021-12-02
forum: General Help
---

### Post by peter-1984 on 2021-12-02
Hi,
To Ubuntu 20, why does it say "agt-get command not found", to the command below?

sudo agt-get install lightdm

---

### Post by tea for one on 2021-12-02
Looks like a typo:-
agt > ```
apt
```

---

### Post by timgood on 2021-12-02
As previous poster, you have used a typo. Also apt-get is now deprecated and you should be using 'sudo apt install <packagename>'

---

### Post by ActionParsnip on 2021-12-02
switch "agt" for "apt". The command is
```

sudo apt-get install lightdm

```
not
```

sudo agt-get install lightdm

```

---

### Post by rsteinmetz70112 on 2021-12-03
I wasn't aware apt-get was depreciated. 

Last I heard apt was newer and more user friendly but still lacked some of the capabilities of apt-get and the other older apt-xxx commands but was recommended for use in scripts..

---

### Post by ActionParsnip on 2021-12-03
It's still there (to my knowledge) but yes, apt should be used going forward.

---

