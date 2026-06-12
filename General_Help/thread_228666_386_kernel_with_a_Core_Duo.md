---
title: "386 kernel with a Core Duo"
date: 2006-08-03
forum: General Help
---

### Post by NTolerance on 2006-08-03
I have been having some performance problems with the 686 kernel, so I am going to try using the 386 kernel instead.  I'd like to know what I'm losing by running the 386 kernel. 

Can I still take advantage of dual cores with the 386 kernel, such as some programs running on one core and other programs running on the other, or does one core go unused all the time?

---

### Post by skymt on 2006-08-03
By switching back, all you're losing are a few optimizations. This means it's unlikely you'll get *better* performance. You'll most likely get very slightly worse performance, since the 386 kernel is the lowest common denominator.

Someone please correct me if I'm wrong, but I believe the proper kernel for a Core Duo is linux-686-smp.

---

### Post by Ramses de Norre on 2006-08-03
If I'm right there is no such thing as an smp kernel nomore since dapper. The smp support is included on demand in the 686, k7, amd64 and powerpc kernels (which means it's there and used when you've got a multicore cpu) but not in the 386 kernel. So I'm afraid you'll need to either use another kernel instead of the 386 or compile your own 386 kernel with smp support in order to use your two cores..

---

### Post by Ocxic on 2006-08-03
since you used the term core duo, I'll assume you're using a mac, so this may not work for you, but I was instructed to add "ht=on"
in the 'kopt' line of my /boot/grub/menu.lst and then run sudo update-grub, apparently it's supposed to activate hyperthreading support for my P4 CPU, maybe it will have the same effect on your cpu????

---

### Post by NTolerance on 2006-08-03
Well, I have confirmed my suspicions that the 686 kernel was killing XGL performance on my ATI X1400.  I installed the 386 kernel and now everything is much faster.  But now I only have one CPU being shown in System Monitor and in /proc/cpuinfo.  How do I get my 2nd core working but keep this speedy performance?

---

### Post by 5-HT on 2006-08-04
> **NTolerance said:**
> Well, I have confirmed my suspicions that the 686 kernel was killing XGL performance on my ATI X1400.  I installed the 386 kernel and now everything is much faster.  But now I only have one CPU being shown in System Monitor and in /proc/cpuinfo.  How do I get my 2nd core working but keep this speedy performance?

Unfortunately, as Ramses de Norre mentioned, Dapper's 386 kernels do not have SMP support which is needed in order to take advantage of both cores. If you'd really like to get the second core functioning, I'd suggest compiling your own kernel if you're experience such performance issues with Dapper's 686 kernels. There are some detailed guides on compiling kernels for Ubuntu in the HowTo forum.

---

### Post by NTolerance on 2006-08-04
Luckily I don't have to compile my own kernel.  Up until this point I have had ONLY the 686 kernel installed.  I went back and intalled the 386 kernel, then booted back into the 686 kernel and now everything is working smoothly.  Why I need to have both installed simultaneously I don't know, but I'm just happy it's working.

---

### Post by DoubleDangerClub on 2006-08-04
So now your graphics is working properly with your 686 kernel?

I noticed this too.  I have a duo core and since the 686 kernel, the graphics got killed, but the 386 runs the graphics the way it should. I have an x1400 too.

Any tips on getting 686 and my ati drivers to work together?

---

### Post by NTolerance on 2006-08-17
> **DoubleDangerClub said:**
> So now your graphics is working properly with your 686 kernel?

I noticed this too.  I have a duo core and since the 686 kernel, the graphics got killed, but the 386 runs the graphics the way it should. I have an x1400 too.

Any tips on getting 686 and my ati drivers to work together?

Do you have the 386 kernel installed?

Also, did you install the fglrx driver on both kernels?

---

