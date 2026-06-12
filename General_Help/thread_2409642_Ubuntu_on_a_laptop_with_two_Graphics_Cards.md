---
title: "Ubuntu on a laptop with two Graphics Cards"
date: 2019-01-04
forum: General Help
---

### Post by atticusghost on 2019-01-04
Hello all

I would like to install Ubuntu on a laptop with two graphics adapters (CPU Integrated and a discrete). I tried once before and the OS froze very often as a result. Every guide Ive found talks about disabling the discrete card which I do not want to do. Does Ubuntu have the same provisions as MS Windows to handle both adapters based on application running?

Thanks

---

### Post by QIII on 2019-01-04
Hello!

Are the adapters from the same manufacturer?

If it's a hybrid system (Intel/NVIDIA or Intel/AMD) you may have a tough row.  Even if they are from the same manufacturer, this can be a difficult proposition.

---

### Post by atticusghost on 2019-01-04
It's a Lenovo Y40-80 with an Intel/AMD setup.

I REALLY want to give Linux a go as I'm trying to be more privacy consious. But since my laptop is the only system I can afford to give up windows on at this point. It's making it hard :(

---

### Post by QIII on 2019-01-04
Unforutunately, the manufacturers have not made that sort of hybrid graphics environment easy for Linux users.

vga_switcheroo used to work, but I haven't been able to test it since AMD went to the AMDGPU driver.  I wouldn't hold much hope on it working, since it was originally an fglrx thing.

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)  This has not been updated since 2015.

PRIME was another option but, again, I'm not sure if that will work.  It would require the removal of AMDGPU (if it's installed) and the installation of xf86-video-amdgpu, which might work perfectly well if it doesn't render your machine inoperable.

[https://wiki.archlinux.org/index.php/PRIME](https://wiki.archlinux.org/index.php/PRIME)  This has not been updated since the middle of 2017.

I suspect that most people simply blacklist the Intel graphics, but you don't want that.

---

### Post by atticusghost on 2019-01-04
I don't actually know if the laptop functions without disabling the Intel adapter. I guess I could try that

---

