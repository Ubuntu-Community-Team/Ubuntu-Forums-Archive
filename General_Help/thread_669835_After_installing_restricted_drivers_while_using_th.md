---
title: "After installing restricted drivers while using the live cd, how do you use them?"
date: 2008-01-16
forum: General Help
---

### Post by rainwalker on 2008-01-16
My friend is using an Ubuntu 7.10 live cd, and none of the eyecandy works for him. He's on the latest MacBook (the black one), and I read that MacBooks work really well with Ubuntu (Full Circle Magazine issue 3). I told him to try the restricted driver, and he's in the process of doing that now.

Are we missing anything? Drivers? Certain configurations? Any general tips?

---

### Post by fragos on 2008-01-16
System-> Administration-> Restricted Drivers Management

---

### Post by rainwalker on 2008-01-16
> **fragos said:**
> System-> Administration-> Restricted Drivers Management

It says he doesn't need any restricted drivers


Also, he ran```
SKIP_CHECKS=yes compiz
```

And it said > Checking for XGL: not present.
Blacklisted PCID '8086:2a02' found
Aborting and using fallback: /usr/bin/metacity

---

### Post by fragos on 2008-01-16
It depends on the chipset.Run " lspci |grep VGA" and tell us what you see.

---

### Post by rainwalker on 2008-01-16
> **fragos said:**
> It depends on the chipset.Run " lspci |grep VGA" and tell us what you see.

Too late, we gave up
He's about to try a Linux Mint live cd now.

---

