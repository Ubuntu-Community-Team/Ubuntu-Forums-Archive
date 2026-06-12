---
title: "Which nvidia driver?"
date: 2007-01-13
forum: General Help
---

### Post by solarwind on 2007-01-13
Hi all, I have an ASUS M2NBP-VM Motherboard with onboard NVIDIA Graphics. What NVIDIA driver should I install? I'm a bit confused. :-k

---

### Post by PriceChild on 2007-01-13
Well it should install "nv" by default... but I always change to the proprietory "nvidia" driver.
```
sudo aptitude install nvidia-glx
sudo nvidia-xconfig
```

---

### Post by solarwind on 2007-01-13
> **PriceChild said:**
> Well it should install "nv" by default... but I always change to the proprietory "nvidia" driver.
```
sudo aptitude install nvidia-glx
sudo nvidia-xconfig
```

So that driver should work with almost any relatively new video card / integrated graphics?

---

### Post by solarwind on 2007-01-13
The nvidia drivers in the repository didn't work for me.

---

### Post by solarwind on 2007-01-14
I did that, no change, nothing... Still the same resolution and horrible 60 Hz refresh rate. I have an ASUS M2NBP-VM board.

---

