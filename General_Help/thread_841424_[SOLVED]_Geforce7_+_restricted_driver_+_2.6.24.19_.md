---
title: "[SOLVED] Geforce7 + restricted driver + 2.6.24.19 kernel"
date: 2008-06-26
forum: General Help
---

### Post by benste on 2008-06-26
Hy, I saw that update manager updated to kernel 19
last week, now ichanged grub for the 19 kernel
- I booted and my grafic card is not detected by restricted manager.
lspci founds:
```
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)

```

No one here?

---

### Post by NT4usB on 2008-06-26
Seems the kernel caused nvidia troubles for a few folks.
I ran [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to fix it.
Read the [faqs ]("http://www.albertomilone.com/envyfaq.html")first.

---

### Post by benste on 2008-06-26
I know about envy I only thought there's something wrong because the driver was installed in 18 kernel but now it seems not to recognize - load it

---

### Post by brtomkin on 2008-06-26
I have an old nvidia card which worked in kernel -18, but stopped after the second kernel -19 update (it still worked after the first update 2.6.24-19.33, but not the second 2.6.24-19.34).  

I reinstalled the following to get it to work again (I wanted to avoid using envy):

linux-restricted-modules-2.6.24-19-generic (2.6.24.13-19.42)
linux-restricted-modules-common (2.6.24.13-19.42)
linux-restricted-modules-generic (2.6.24.19.21)
nvidia-glx (1:96.43.05+2.6.24.13-19.42)
nvidia-kernel-common (20051028+1ubuntu8 )

---

### Post by benste on 2008-06-27
I used envy now - and all is ok now expected gdm which now runs in 1024*800 instead of 1280

---

