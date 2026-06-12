---
title: "install/remove programs"
date: 2008-01-31
forum: General Help
---

### Post by santanadiablo on 2008-01-31
I've just put Kubuntu onto an older PC, today.  Installation went fine.  I used install/remove programs to install a firewall and that went fine.  Next, I checked Firefox and Sun Java for installation. The install got hung up and quit.  So I went back in and tried it again.  It kept giving me an error msg. saying that something didn't work out with dependencies on my last install try.  Only, now, no matter what I try to install the installation stops and gives me an error.  Basically, now the install/remove programs won't work--at all.  WTFO?  This is bizarre.

---

### Post by zvacet on 2008-01-31
> This is bizarre.

Yes it is.Go to the** system>administration>software sources**<chek all boxes under Ubuntu software tab and under updates tab.Reload.For Java,Flash ans other things you will need go to programs >accessories>terminal and type

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by kesman on 2008-01-31
and before that terminal command, run this in terminal:
```

sudo apt-get update

```

---

### Post by zvacet on 2008-01-31
@ **kesman**

It is updated by reloading.

---

### Post by santanadiablo on 2008-01-31
> **zvacet said:**
> @ **kesman**

It is updated by reloading.

It was reloaded. The problem still persisted. I think it's just a buggy packet manager.

---

### Post by zvacet on 2008-01-31
We can try other way 

```
cat /etc/apt/sources.list
```

Post it here.

---

### Post by jan quark on 2008-01-31
or try this code
```
sudo apt-get -f install
```

this should fix the broken packages

---

