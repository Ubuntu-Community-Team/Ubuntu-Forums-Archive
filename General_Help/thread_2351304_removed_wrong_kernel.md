---
title: "removed wrong kernel"
date: 2017-02-01
forum: General Help
---

### Post by rburkartjo on 2017-02-01
i have ubuntu 16.04 on 1 partition and 17.04 on another. i removed the kernel for 16.04 by error. still have 16.04 on partition just cant boot. any ideas or am i just sol. tried boot repair but that didnt work. any ideas?

---

### Post by rburkartjo on 2017-02-01
if i download the most recent kernel for 16.04 while in 17.04 and then run sudo update-grub would that work. if so where would i find a link to it.

---

### Post by &amp;KyT$0P# on 2017-02-01
I'd probably [FONT=Courier New]chroot[/FONT] into the borked 16.04 system/partition and attempt reinstalling the kernel from there.

---

### Post by rburkartjo on 2017-02-01
also have a live 16.04 cd

---

### Post by DuckHook on 2017-02-01
> **halogen2 said:**
> I'd probably [FONT=Courier New]chroot[/FONT] into the borked 16.04 system/partition and attempt reinstalling the kernel from there.
+1
> **rburkartjo said:**
> also have a live 16.04 cd
That would work too, but halogen2's fix is the easiest. You are in very good shape. Having a dual boot is fortuitous. Both of them being Ubuntu is fortuitous. And coincidentally, instructions for chrooting were recently just posted in another thread which is… fortuitous!
[https://ubuntuforums.org/showthread.php?t=2351038&p=13601213#post13601213](https://ubuntuforums.org/showthread.php?t=2351038&p=13601213#post13601213)
Replace the last step with:```
apt install linux-image-generic
```

---

### Post by rburkartjo on 2017-02-02
tks duck didnt work only picks up kernel on 17.04

ray@nightmare:~$ sudo update-grub
[sudo] password for ray: 
Generating grub configuration file ...
Found background: /home/ray/12.jpeg
Found background image: /home/ray/12.jpeg
Found linux image: /boot/vmlinuz-4.9.0-16-generic
Found initrd image: /boot/initrd.img-4.9.0-16-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
ray@nightmare:~$

---

### Post by DuckHook on 2017-02-02
](*,)

I can be such an idiot (that's what happens from lack of sleep). Of course. You are installing from 17.04. :roll:

Should have been:```
apt install linux-generic-lts-xenial
```But first, you must get rid of the wrong kernel with:```
apt purge linux-image-generic && apt autoremove && apt clean
```

---

### Post by DuckHook on 2017-02-02
FWIW,

Had you used your DVD and done this from a LiveDVD of Xenial, the first command would have worked. linux-image-generic will always install the kernel from the version of OS you are actually running.

---

### Post by DuckHook on 2017-02-02
Speaking of sleep, will be signing off now. Will catch up again in the morning.

---

### Post by rburkartjo on 2017-02-02
duck didnt have to do what you suggested in #7. just ran grub customizer and it fixed grub.tks

---

### Post by DuckHook on 2017-02-02
Glad it worked out. Make sure you add the generic kernel afterwards if you want automatic kernel updates.

---

### Post by rburkartjo on 2017-02-02
duck how would i do that

---

### Post by rburkartjo on 2017-02-02
my bad already did it

---

### Post by DuckHook on 2017-02-02
> **rburkartjo said:**
> duck how would i do thatFrom within your working install, *now* do:```
 sudo apt install linux-image-generic
```

---

