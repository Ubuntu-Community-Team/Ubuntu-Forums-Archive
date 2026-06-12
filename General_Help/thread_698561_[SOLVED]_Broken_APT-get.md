---
title: "[SOLVED] Broken APT-get"
date: 2008-02-16
forum: General Help
---

### Post by Jeztastic on 2008-02-16
> The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.

I seem to have broken apt-get. Oops. How can I fix this? Thanks.

Jez

---

### Post by pointone on 2008-02-16
Have you tried what it recommends? Try running apt-setup and apt-get update.

---

### Post by jan quark on 2008-02-16
if you have broken packages try these codes


```
sudo apt-get -f install
```

```

sudo dpke --configure -a
```

---

### Post by wolfen69 on 2008-02-16
> **jan quark said:**
> if you have broken packages try these codes


```
sudo apt-get -f install
```

```

**sudo dpke --configure -a**
```

it should be:

```
sudo dpkg --configure -a
```

---

### Post by Jeztastic on 2008-02-16
I had an incorrect address for a repo causing the crash. Thanks for the help guys.

---

