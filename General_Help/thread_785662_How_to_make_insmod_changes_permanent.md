---
title: "How to make insmod changes permanent?"
date: 2008-05-07
forum: General Help
---

### Post by a_hernando on 2008-05-07
Hi,

After upgrading to 8.04 from 7.10 I had a lot of trouble getting the hardware driver to work with my GeForce 4 MX-4000 card. Finally I discovered that the problem was with one kernel module not loading correctly. In fact, if I just install the hardware driver and reboot, my machine goes into low-graphics model with the usual warning. At the console, I get:

```

$ lsmode | grep nvidia
  nvidia    3934028   0
  agpgart     34760   2   nvidia, intel_agp
$ lsmode | grep i2c
  i2c_core    24832   0

```

If I do:

```

$ sudo /etc/init.d/gdm stop
$ sudo rmmod nvidia
$ sudo insmod /lib/modules/`uname -r`/volatile/nvidia.ko
$ sudo /etc/init.d/gdm start

```

I get the system to start at my preferred resolution and all the eyecandy thingies work as a charm. Then, if I do:

```

$ lsmod | grep nvidia
  nvidia   4718832  0
  i2c_core   24832  1  nvidia
  agpgart    34760  2  nvidia, intel_agp

```

Of course, I don't want to have to go through this whole thing every single time I boot, so I've been looking for a way of making this change permanent. So far, the only way I have found that works is to add the following couple of lines at the beginning of /etc/init.d/x11-common (right after the [FONT="Courier New"]set -e[/FONT]):

```

rmmod nvidia
insmod /lib/modules/2.6.24-16-generic/volatile/nvidia.ko

```

Of course, this is just a patch, and it's bound to fail after the next upgrade or kernel change... Even worse, I'm not very good at keeping track of all the changes I make to my system so chances are I would forget that I ever did this and will spend a lot of time in the future trying to find out what I did and how I did it in the first place.

Thanks,
Andres.

---

### Post by sdennie on 2008-05-07
Have you previously installed the nvidia drivers manually?  The output of the following commands might be useful.  Specifically, before doing the rmmod/insmod fix:

```

modinfo nvidia | grep filename
dpkg -l | grep nvidia

```

---

### Post by a_hernando on 2008-05-07
> **vor said:**
> Have you previously installed the nvidia drivers manually?

Only after the Hardware Driver didn't work... I removed it completely.

> The output of the following commands might be useful.  Specifically, before doing the rmmod/insmod fix:

```

modinfo nvidia | grep filename
dpkg -l | grep nvidia

```

Here they go... Before the rmmod/insmod fix:
```

$ modinfo nvidia | grep filename
filename:       /lib/modules/2.6.24-16-generic/volatile/nvidia.ko
$ dpkg -l | grep nvidia
ii  nvidia-glx                          1:96.43.05+2.6.24.12-16.34       
   NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-kernel-common                20051028+1ubuntu8                
   NVIDIA binary kernel module common files
ii  nvidia-settings                     1.0+20080304-0ubuntu1            
   Tool of configuring the NVIDIA graphics driv

```

After the fix:
```

$ modinfo nvidia | grep filename
filename:       /lib/modules/2.6.24-16-generic/volatile/nvidia.ko
$ dpkg -l | grep nvidia
ii  nvidia-glx                           1:96.43.05+2.6.24.12-16.34       
   NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-kernel-common                 20051028+1ubuntu8                
   NVIDIA binary kernel module common files
ii  nvidia-settings                      1.0+20080304-0ubuntu1            
   Tool of configuring the NVIDIA graphics driv

```

So, they are identical.

Best,
Andres.

---

