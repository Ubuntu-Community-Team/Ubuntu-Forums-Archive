---
title: "Lowlatency kernel does not support nvidia driver"
date: 2007-06-11
forum: General Help
---

### Post by quatrecouleurs on 2007-06-11
Hello !

I'm new to ubuntustudio, and wondering about this issue : when I upgraded two days ago my kernel, and then restarted on the lowlatency kernel, xorg froze and couldn't launch the nvidia module.  It is just the update that did this.

But I can always boot on the generic kernel, wich just works fine. Without music :( The old lowlatency kernel works too.

So I wonder  if it is a bug from the update, or if I have to do anything else to allow the lowlatency to load properly with xorg. If I have sthing to do, wy could this just not been done in the .deb I downloaded  from ubuntustudio's repository ?

---

### Post by Stinger on 2007-06-12
Boot on the generic kernel and do this in a terminal

```
sudo apt-get install linux-restricted-modules-lowlatency linux-restricted-modules-2.6.20-16-lowlatency
```

and reboot into your lowlatency kernel (should be default)
this would bring you the newest restricted-modules matching your kernel.

Hope it helps.

---

### Post by quatrecouleurs on 2007-06-17
Thanks for your answer. I used the command-line you posted, but synaptic says that the files are already installed, but the lowlatency kernels are marqued as "installed manually" kernels... I did not install any kernel since I installed the distribution...

How should I proceed to have my lowlatency kernel upgrade ?

---

### Post by AmyRose on 2007-07-11
You could try purging ALL the "lowlatency" packages by removing them and then going into Synaptic and removing all the "residual config" packages. Then reinstall them and see what happens.

Good luck!

---

### Post by AstarothCY on 2007-07-24
Bump, same problem, have you solved this?

Edit: never mind, you just need to download the restricted driver package for the lowlatency kernel

---

