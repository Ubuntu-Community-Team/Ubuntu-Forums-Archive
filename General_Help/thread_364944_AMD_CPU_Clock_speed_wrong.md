---
title: "AMD CPU Clock speed wrong"
date: 2007-02-18
forum: General Help
---

### Post by bradasmaximus on 2007-02-18
Ubuntu is showing me 1ghz in my Athlon 3000+ 1.8ghz cpu it's fine in Windows but not Ubuntu.
Any idea's on how to fix that?

---

### Post by kamaboko on 2007-02-18
i get the same thing with my AMD Sempron.  i don't know of a fix.

---

### Post by RAOF on 2007-02-18
There's no fix, 'cause it's not a bug.  It's the CPU frequency scaling cutting in.  When your CPU is being heavily used, it should scale back up to 1.8GHz, and while it's idle it'll scale down to 1GHz.

This is also known as "Cool 'n' Quiet"

---

### Post by kamaboko on 2007-02-19
Cool. :-)  i didn't know that.

---

### Post by Ramses de Norre on 2007-02-19
You can turn it on/off with **sudo /etc/init.d/powernowd start/stop**.

---

### Post by bradasmaximus on 2007-02-19
Thanks mate that worked great.

---

### Post by stchman on 2007-03-02
> **RAOF said:**
> There's no fix, 'cause it's not a bug.  It's the CPU frequency scaling cutting in.  When your CPU is being heavily used, it should scale back up to 1.8GHz, and while it's idle it'll scale down to 1GHz.

This is also known as "Cool 'n' Quiet"

I gather that Ubuntu installs Cool 'n' Quiet drivers for all Athlon 64 or any AMD processors that use this technology by default.  I do remember that my 3500+ can go down as low as 1GHz with cool 'n' quiet.  I just did not know that Ubuntu uses this.

Thanks

---

