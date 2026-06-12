---
title: "Force the 32 bit version of libpng.so.3 to install"
date: 2013-02-02
forum: General Help
---

### Post by Horbo on 2013-02-02
I'm running 64 bit (as any sensible person with 64 bit hardware would)  12.10 and am trying to install HiDPoint.

Unfortunately they have written it only for 32 bit.  They claim that installing ia32-libs will let it work on a 64 bit OS, but this is incorrect - it doesn't solve the libpng problem.

I have tried installing and soft linking to the 64 bit libpng.so.3, but they even go so far as to check the version of libpng and refuse to install if it isn't 32 bit!

So I'm pretty sure I have no choice but to install what they want.

I can't just use apt-get to install libpng3 - it installs the 64 bit version.

How can I install the 32 bit version of libpng3 on my 64 bit Ubuntu?

---

### Post by Cheesemill on 2013-02-02
Have you tried...
```
sudo apt-get install libpng3:i386
```

---

### Post by Yellow Pasque on 2013-02-02
Probably a good idea to make sure multiarch-support package is installed too.

> They claim that installing ia32-libs will let it work
Those directions are outdated. Debian/Ubuntu handle multiarch differently nowadays.

---

### Post by Horbo on 2013-02-02
Thank you very much guys!

Multiarch didn't help unfortunately, but Cheesemill's 
sudo apt-get install libpng3:i386did exactly what I needed...

---

