---
title: "How can I delete the network connection?"
date: 2008-04-04
forum: General Help
---

### Post by MicroBoy on 2008-04-04
**How can I delete the network connection. I use the pppoe to connect into the internet. I need to delete because i'm having some problems.**

---

### Post by MrFSL on 2008-04-04
Edit

/etc/network/interfaces

alternatively run:
```
sudo pppoeconf
```

---

### Post by zvacet on 2008-04-04
```
poff dsl-provider
```

and if you want to connect again

```
pon dsl-provider
```

---

### Post by MicroBoy on 2008-04-05
> **MrFSL said:**
> Edit

/etc/network/interfaces

alternatively run:
```
sudo pppoeconf
```[B]Do I have to delete all the information in the interfaces ?
[/B]

---

### Post by MrFSL on 2008-04-05
No.

If you have setup your connection using pppoeconf you might see a ppp0 entry that you would want to remove.

---

### Post by MicroBoy on 2008-04-05
> **MrFSL said:**
> No.

If you have setup your connection using pppoeconf you might see a ppp0 entry that you would want to remove.Do I have to delete the file or just the words inside the file.

---

### Post by lswest on 2008-04-05
just delete the entry for ppp0 (the words)

---

