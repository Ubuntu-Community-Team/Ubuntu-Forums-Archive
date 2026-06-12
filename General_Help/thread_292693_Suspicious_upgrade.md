---
title: "Suspicious upgrade?"
date: 2006-11-04
forum: General Help
---

### Post by Zalbor on 2006-11-04
An upgrade for my kernel appeared today. I'm using "generic", which I guess is Edgy's version for 686. There are also upgrades for restricted-modules and nvidia-glx.
The problem is that if I choose to upgrade it also wants to install a 386 kernel. I checked the dependencies and saw no need for it... Why is it asking for it since it will have the generic one anyway?

---

### Post by kerry_s on 2006-11-04
When i installed my nvidia-glx it installed the 386 kernel, it did that on all my installs.

---

### Post by Zalbor on 2006-11-04
So what does that mean, I'll have to have 386 installed and not use it? Or will I have to use 386, because generic won't work with nvidia? And how come it needs 386, when it's not a dependency of the package?

---

### Post by Zalbor on 2006-11-04
It installed the 386 kernel, but afterwards I removed it and it didn't complain. Strange.

---

### Post by kerry_s on 2006-11-04
I prefer the 386 to that multipurpose generic one, the 386 one seems faster on my computer. It always seemed like the generic was taking longer to load.

---

### Post by Zalbor on 2006-11-04
Isn't the "generic" a replacement for 686 then?

---

### Post by kerry_s on 2006-11-04
From my understanding it's a bloated kernel, by bloated i mean it has every option turned on at compile time to work on a more broad range of machines. For instance if you have duel core it should work in the generic kernel rather than having to install the smp kernel. So of course with more options you have to give a little here and there,bigger size,more devices to scan through,...

---

