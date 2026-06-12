---
title: "List of services during boot"
date: 2007-10-21
forum: General Help
---

### Post by BSK on 2007-10-21
Hi,

I'm pretty sure this as already been posted but I can't find it.

When Ubuntu is booting I see a logo and orange progress bar, is it possible to display a list of services currently booting ?  If so, how ?

Thanks a lot!

---

### Post by ntetreau on 2007-10-21
> **BSK said:**
> Hi,

I'm pretty sure this as already been posted but I can't find it.

When Ubuntu is booting I see a logo and orange progress bar, is it possible to display a list of services currently booting ?  If so, how ?

Thanks a lot!

Well your question is slightly convoluted.  If you want to know exactly which services are run at boot time, then you go into System > Administration > Services.  However, if you want to get a text feedback during boot then you need to remove "quiet" in the kernel line of /boot/grub/menu.lst

```
sudo gedit /boot/grub/menu.lst 
```

If you scroll down to find the section on your kernel, you'll find this:

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=04050f86-965d-4149-9f47-9387fbb828dd ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic quiet[CODE]

erase the 2 "quiet"

[CODE]]title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=04050f86-965d-4149-9f47-9387fbb828dd ro splash
initrd		/boot/initrd.img-2.6.22-14-generic
```

Additionally, if you'd like this to be the default for every bootup and kernels, then you need to change this line a well:

```
# defoptions=quiet splash
```

to


```
# defoptions=splash
```

It just never stops to amaze me how totally configurable Linux is!!!

---

### Post by BSK on 2007-10-21
Thanks a lot!

Removing the "quiet" did the trick!:KS

---

