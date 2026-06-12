---
title: "X windows broken"
date: 2006-12-22
forum: General Help
---

### Post by edgyUser on 2006-12-22
Hi,

I was trying to install/reinstall something on my Ubuntu Edgy and now my X windows is broken. Cannot load nvidia module or something like that. I am running Ubuntu Edgy 32 bit and using the nvidia package for my 7600GT graphics card.

My internet connection is also broken, therefore I am not able to use apt-get update from the internet repositoty. My questions are the following:
1. What are the packages that I have to re-install in order to make X Windows work again?
2. If I cannot install via the internet using apt-get, how do I use the Ubuntu CD to install the needed packages?
3. I also read somewhere that packages that I may need may already be in the /var/cache/apt/archives. Does that mean that I can re-install the packages from this location? 

Sorry if this sounds like FAQ.

regards,
Vincent

---

### Post by hanzomon4 on 2006-12-22
**3.** Yes you can ```
sudo dpkg -i /var/cache/apt/archives/name.of.package.deb
```

**1. **I think you need  the restricted  modules... linux-restricted-modules-generic(or linux-restricted-modules-your.kernel.version) So that would be:```
sudo dpkg -i /var/cache/apt/archives/linux-restricted-modules-generic
```

---

