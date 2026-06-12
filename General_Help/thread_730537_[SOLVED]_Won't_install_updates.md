---
title: "[SOLVED] Won't install updates"
date: 2008-03-21
forum: General Help
---

### Post by p110011 on 2008-03-21
So I got updates to MYSQL through update Manager, and they don't install.

In the Terminal I typed apt-get updates and install, but it says the same thing, that there are two packages not upgraded.

I removed MYSQL (along with Amorok):(
Then reinstalled them:)
but still no good.

I thought it might have something to do with this file.. /var/lib/apt/lists/lock
so I removed it, but still no good.

I'm not fluent in Linux so let me know if I broke something, or if you can help please.

Gill

---

### Post by zvacet on 2008-03-21
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by p110011 on 2008-03-21
Ok, sudo apt-get upgrade did it...Thanks!

---

