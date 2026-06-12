---
title: "gutsy hang at &quot;starting Firestarter firewall&quot;"
date: 2007-12-23
forum: General Help
---

### Post by FRuMMaGe on 2007-12-23
I installed firestarter yesterday. Now Gutsy will not boot.

A small portion into the startup process, text says "Stopping the Firestarter firewall", then it complains about rt73 firmware not being found.

Also, when I boot using the live cd, I mount my drive and cant seem to find firestarter anywhere. It seems like the installation was invalid.

How do I start ubuntu so I can remove firestarter or manually remove it using the live disc. I have tried recovery mode but it does the same thing.

Please help as it is EXTREMELY important that I have full access to my computer by TONIGHT!

---

### Post by FRuMMaGe on 2007-12-23
bump

this is EXTREMELY important

---

### Post by zarqoon on 2007-12-23
have you tried choosing the recovery mode with grub and removing it from there?

---

### Post by FRuMMaGe on 2007-12-23
> **zarqoon said:**
> have you tried choosing the recovery mode with grub and removing it from there?

yes.

It did the same thing.

Wow, I think I've solved it myself somehow. I used the live CD to delete the firestarter script from /etc/init.d

Probably not the best idea, but i will see how it goes from here

---

