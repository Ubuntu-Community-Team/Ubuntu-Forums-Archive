---
title: "Ubuntu 13.04 running in slow motino (in VMware Workstation)"
date: 2013-05-25
forum: General Help
---

### Post by altjx on 2013-05-25
I run several VMs in VMware Workstation 8.x just fine very often (i.e. Kali Linux, Win XP, Win7, etc.). However, the latest installation of Ubuntu 13.04 seems to be very sluggish. For example, when I pull up the menu to run a command, it lags extremely bad. 

Is there a setting or something I have to change within VMware Workstation's settings to get Ubuntu 13.10 to run fine? I've installed it just with 1 GB of memory (assuming that's sufficient).

As a side note, I've also experienced this on an older desktop that I've tried installing it on. Not to say that it's strictly Ubuntu issues on the desktop, but I'm having the same issue in VMware Workstation that I have on my older desktop. Not sure what's going on.

Any help would be greatly appreciated.

Thanks,
Alton

---

### Post by 2F4U on 2013-05-25
Did you install the VMWare guest additons in the Ubuntu guest system?

---

### Post by HiImTye on 2013-05-25
you def. need the guest additions since llvmpipe is slow. you might want to use a lighter distro in a VM, such as Lubuntu, in which case you won't need the drivers to make the desktop usable

---

### Post by altjx on 2013-05-25
Ahhh, VMware guest additions. I didn't install that but going to shortly. 

Thanks for the reply and I'll post back once fixed.

---

### Post by 3rdalbum on 2013-05-25
I'm still not sure how well Unity will run in a virtual machine, even with guest additions.

For the virtual install you might want to use XFCE or LXDE - these are installable from Ubuntu Software Center and then can be enabled from the login screen.

---

### Post by altjx on 2013-05-25
> **3rdalbum said:**
> I'm still not sure how well Unity will run in a virtual machine, even with guest additions.

For the virtual install you might want to use XFCE or LXDE - these are installable from Ubuntu Software Center and then can be enabled from the login screen.

Ohh ok. I'll try that as well. Thanks!

---

### Post by altjx on 2013-05-25
Well, that didn't work out too well... I ended up just installing Linux Mint 14 Cinnamon, and that's working flawlessly. Thanks for the help guys.

---

