---
title: "Unused Kernel Headers"
date: 2008-06-04
forum: General Help
---

### Post by Sleaka J on 2008-06-04
Now that I've upgraded to 2.6.24-18, do I still need 17 (or 16 for that matter)?

If I can get rid of them, would removing them from Synaptic be the best way?

---

### Post by ibuclaw on 2008-06-04
No, you don't really need the old headers at all (the only use I've had for them is compiling Vbox Modules). So it is safe to say bye to them.

Yes you can use synaptic to remove them. If that is what you prefer.

But here is the CLI way for you too:
```
sudo apt-get remove linux-headers-2.6.24-16 linux-headers-2.6.24-17
```

Regards
Iain

---

### Post by drs305 on 2008-06-04
I've just posted a thread about this. [HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by ibuclaw on 2008-06-04
+1, good stuff drs305

---

### Post by Ameneon on 2008-06-04
Ok, I'm not at all experienced, but I would presume that it's not quite so simplistic as "I don't need the old kernels anymore", myself. Of course it all varies by mileage but unless you're quite certain that the new kernel performs as well as the old one and is as stable could one say that it's no big deal to remove the old one(s).

In my own case, I'm still having to revert to the .16 kernel due to a performance issue that persists with both the .17 and .18 kernel and I would imagine that other similar situations (or alternatively stability issues) might not be readily seen at first glance but rather over time.

But again, the clear answer probably would vary by mileage and experience..

---

