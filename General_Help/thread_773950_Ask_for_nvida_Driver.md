---
title: "Ask for nvida Driver"
date: 2008-04-29
forum: General Help
---

### Post by reyhan on 2008-04-29
i just want to install the Nvidia Driver 
but wht theres a text like this ?

> No precompiled kernel interface was found to match your kernel 

---

### Post by jespdj on 2008-04-29
Which version of Ubuntu are you running?

Are you trying to manually install the nVidia driver? Is there a reason why you are trying to install it manually?

In Ubuntu 8.04, a very new version of the nvidia driver is included. First, open a terminal and enter:
```
sudo apt-get update
```
Then, go to System / Administration / Hardware Drivers. It will show you that the nvidia driver is available, but not enabled. Enable it, let it download and install, reboot, and it works.

If for some reason you want to do it manually: Don't worry about that message. It just tells you that it doesn't have a precompiled kernel module, and it will proceed to compile a kernel module itself. If that doesn't work, then you have to install a compiler and the Linux kernel header files first:
```
sudo apt-get install build-essential linux-headers-generic
```

---

### Post by pro003 on 2008-04-29
```
System > Administration > Hardware Driver
```

just check nvidian to make it in use... must have internet connection

---

### Post by reyhan on 2008-04-29
i am running Ubuntu 8.04

---

### Post by Trampis on 2008-04-29
> **pro003 said:**
> ```
System > Administration > Hardware Driver
```

just check nvidian to make it in use... must have internet connection

I am actually having a similar problem when I tried that I got the message

> E: /var/cache/apt/archives/nvidia-glx-new_169.12+2.6.24.12-16.34_i386.deb: subprocess pre-installation script returned error exit status 2



You might want to try Envy, it is made for installing nvidia drivers, But it did not work for me in this instance

---

### Post by pro003 on 2008-04-29
make sure you have internet connection... 

go to: 

```
/var/cache/apt/archives
```

find the nvidia deb package and double click on it... if you have internet there should not be a problem to pick up the dependencies... although you must enable repositories by doing:

System > Administration > Software sources ... then check ubuntu software third party software, etc.

---

