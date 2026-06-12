---
title: "Linux kernel no longer smp?"
date: 2008-06-24
forum: General Help
---

### Post by tgrimley on 2008-06-24
I just noticed today that yesterday's (or maybe the day before's) upgrade leaves my desktop with only one processor.  Which kernel do I need and how can I see which kernel was last installed?

I now get:```
tgrimley@tlomm-node1:~/Desktop$ uname -a
Linux tlomm-node1 2.6.24-19-386 #1 Wed Jun 4 15:54:02 UTC 2008 i686 GNU/Linux

```

I think it was running the 18-386 before (here's the relevant lines in menu.lst

```

title		Ubuntu 8.04, kernel 2.6.24-19-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=de08483c-06f3-4347-b185-1023b16df07e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-386
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=de08483c-06f3-4347-b185-1023b16df07e ro single
initrd		/boot/initrd.img-2.6.24-19-386

title		Ubuntu 8.04, kernel 2.6.24-18-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=de08483c-06f3-4347-b185-1023b16df07e ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-386
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=de08483c-06f3-4347-b185-1023b16df07e ro single
initrd		/boot/initrd.img-2.6.24-18-386


```

---

### Post by drs305 on 2008-06-24
Each time a kernel is introduced it is added to grub's boot menu. You can control what you see by editing menu.lst  Fortunately, there is an easier and safer method, using StartUp-Manager. It will allow you to decide how many kernels to display at boot, which kernel to use, how long to display the menu, and much more.

To learn more:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

When you say you are left with only one processor, you can select how many kernels to display via StartUp-Manager.

If you want to *remove* kernels from your machine, you can use synaptic to remove older images (linux-image-2.6.24-XXXX). Just make sure to keep the current one (and one other is recomended). Once a kernel is removed via synaptic the menu item for that kernel is automatically removed as well.

---

### Post by tgrimley on 2008-06-24
Am I crazy or was -18-386 smp enabled and -19-386 isn't?

---

### Post by sdennie on 2008-06-24
I don't think the -386 kernel has ever had SMP.  You'll need the generic kernel:

```

sudo apt-get install linux-generic linux-headers-generic

```

Then select the generic kernel at boot time.

---

### Post by bodhi.zazen on 2008-06-24
There used to be a smp kernel, but it was rolled into one giant "generic" kernel.

---

### Post by tgrimley on 2008-06-24
Yeah, okay that makes sense.  The description for generic didn't say it was SMP so I assumed I was losing my mind :)

---

