---
title: "Laptop monitor 1080p and External HiDPI monitor"
date: 2020-09-13
forum: General Help
---

### Post by gsync on 2020-09-13
Hello,

I'm using Ubuntu 20.04 of my laptop (with FHD monitor), connected to external HiDPI monitor (4K - 3840x2160).
The external monitor is 4K and default text scaling doesn't do the job,
therefore I'm disabling the laptop screen and utilizing only the external by changing the text scaling.

```
gsettings set org.gnome.desktop.interface text-scaling-factor 1.5
```

I've been trying to setup dual monitor usage (laptop + external) using **xrandr**, but with no success up to now.
I end up with messed up desktop setup each time.

Most of the articles I manage to find are referring to solution where people have the setup in reverse - laptop monitor is HiDPI and the external in FHD. 

How I can achieve scaling only on the external monitor, but keep the build in as it is ?

---

### Post by Autodave on 2020-09-13
Perhaps if you gave some info on your laptop, someone might be able to help you.

---

### Post by gsync on 2020-09-13
> **Autodave said:**
> Perhaps if you gave some info on your laptop, someone might be able to help you.


I don't think laptop information is required, because you can have the same situation with desktop PC and two external displays that has different DPI.

But here are the details - Lenovo Legion Y740, with RTX 2070 Max-Q, build-in display 144Hz 1080p.

---

