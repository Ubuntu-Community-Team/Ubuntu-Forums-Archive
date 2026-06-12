---
title: "Just some help"
date: 2007-07-09
forum: General Help
---

### Post by Th0rn0 on 2007-07-09
I installed ubuntu. Liked it. But When I DL then Nvidia drivers [http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)
Linux cannot read it. I also did the console thing but don't know whether it worked. Also how do i got 1440x900 res. Thanks.

---

### Post by afbase on 2007-07-09
in command line, did you type:
```
sh NVIDIA-Linux-x86-100.14.11-pkg1.run
```

---

### Post by Th0rn0 on 2007-07-09
nope. I'm totally new to linux so I don't know ****!

---

### Post by Th0rn0 on 2007-07-09
Just done it and it says sh: Can't open NVIDIA-Linux-x86-100.14.11-pkg1.run

---

### Post by rus0 on 2007-07-21
> **Th0rn0 said:**
> Just done it and it says sh: Can't open NVIDIA-Linux-x86-100.14.11-pkg1.run

Hi there. Here is your problem/solution...

Problem: You are in the wrong directory, this is why it cannot open. Save NVIDIA-Linux-x86-100.14.11-pkg1.run to the desktop. 

In terminal type -- "cd Desktop" (without quotes obviously)

Now type "sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run"

 Problem solved. :P

---

