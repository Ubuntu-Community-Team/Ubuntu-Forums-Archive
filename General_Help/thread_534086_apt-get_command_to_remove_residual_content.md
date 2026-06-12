---
title: "apt-get command to remove residual content"
date: 2007-08-24
forum: General Help
---

### Post by Jamesbowden on 2007-08-24
I regularly remove the residual content left behind from commands like apt-get autoremove from my system via Synaptic, is there a quick way to do this via apt from the CLI?

thanks
James

---

### Post by apetresc on 2007-08-24
> **Jamesbowden said:**
> I regularly remove the residual content left behind from commands like apt-get autoremove from my system via Synaptic, is there a quick way to do this via apt from the CLI?

thanks
James
Yup, simply add --purge to your remove commands like so:```
sudo apt-get remove --purge packagename
```

---

### Post by capink on 2007-08-24
To purge all removed packages ( i.e remove all residual config files):

```
sudo aptitude purge '~c'
```

---

