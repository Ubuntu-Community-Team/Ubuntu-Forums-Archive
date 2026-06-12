---
title: "Duplicate entries in grub's menu.lst, after each updating"
date: 2008-06-20
forum: General Help
---

### Post by figo2476 on 2008-06-20
Hi:

As the title suggest, I am having duplicate entries in menu.lst, after each updating. 

e.g.

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=92feda5e-ec11-4743-98f0-f6144961bbd9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=92feda5e-ec11-4743-98f0-f6144961bbd9 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=92feda5e-ec11-4743-98f0-f6144961bbd9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=92feda5e-ec11-4743-98f0-f6144961bbd9 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=92feda5e-ec11-4743-98f0-f6144961bbd9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

I wonder is there any way to fix it? (One way is I can delete them, but can I make it never happen again)

---

### Post by figo2476 on 2008-06-20
It is my bad. They are different. I guess I just want the latest version to show up.

---

### Post by iaculallad on 2008-06-20
> **figo2476 said:**
> It is my bad. They are different. I guess I just want the latest version to show up.

You could edit your GRUB menu list and delete/comment out the old kernel versions and later on, delete the old kernels using your Synaptics (*search for the work "linux-image" (w/o quote)*) and delete them.

```
gksu kedit /boot/grub/menu.lst
```

---

### Post by Zorael on 2008-06-21
You could limit the number of kernels to be shown. In /boot/grub/menu.lst:
```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=**1**
```


You could also disable recovery mode entries getting automatically generated. I'd not advise this, since you'd have to learn how to manually start such a session if the need arises.
```
## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=**false**
```
Then have grub update the entries.
```
$ sudo update-grub
```
To start in recovery mode if you have those entries disabled, hit E to edit the grub entry, then E again on the kernel line and add the argument *single*. Enter, then B to boot.

---

