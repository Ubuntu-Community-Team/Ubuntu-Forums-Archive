---
title: "Screwing around -- Need to revert to Wily Repositories"
date: 2016-03-26
forum: General Help
---

### Post by neu5eeCh on 2016-03-26
So, I brought this on myself. ](*,)I used the wrong switch with do-release-upgrade, but stopped it before any downloading began.

Question is this:

All the repositories are set to Xenial. How do I revert them back to Wily?

Thanks.

---

### Post by grahammechanical on 2016-03-26
This command will change all "xenial" to "wily" in /etc/apt/sources.list

```
sudo sed -i 's/xenial/wily/g' /etc/apt/sources.list
```

Regards

---

### Post by neu5eeCh on 2016-03-26
Weird. Rather than interrupting it this time (a second time) I waited the option to abort (it didn't last time, which is why I interrupted it). I chose abort but my Wiley repos weren't reinstated. How do I reinstate them?

---

### Post by neu5eeCh on 2016-03-26
> **grahammechanical said:**
> This command will change all "xenial" to "wily" in /etc/apt/sources.list

```
sudo sed -i 's/xenial/wily/g' /etc/apt/sources.list
```

Regards

Thanks. That helped. It didn't restore the PPAs to wiley. I tried opening synaptic and editing every xenial entry to wiley, but now I'm getting "failed to fetch" complaints. Feh.

**Edit:** Would a recursive option work with the SED command?

---

### Post by neu5eeCh on 2016-03-26
Okay, everything is back to order. Third party repositories are enabled. Had to manually rename them. 

:/  <--- Exhibit A (being me) for how **not** to do this.

---

### Post by oldos2er on 2016-03-27
Proper spelling is **wily**, no "e" there.

Edit: Never mind, I see you used the correct spelling where it mattered.

---

