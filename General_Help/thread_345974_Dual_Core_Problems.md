---
title: "Dual Core Problems"
date: 2007-01-25
forum: General Help
---

### Post by thinkdez on 2007-01-25
Hello all,
         I have been working with Ubuntu as my main desktop for a couple of months now and I finally got my setup to be working just the way I like it and suddenly One of the CPU's in my Dual Core stopped being recognized. I cannot see why I am running edgy on a AMD dual core X2.   The only clue I have is the following line in my dmesg:
```

$ dmesg|grep Processor
Processor #0 15:11 APIC version 16
Processor #1 15:11 APIC version 16,
**WARNING: NR_CPUS limit of 1 reached.  Processor ignored.**
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 01

$ uname -a
Linux phantoms-dt 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686 GNU/Linux
```

The only thing I can think of that might have affected this was when I was getting Beryl to work on my system yesterday. I used the instructions at the following: [HTML]http://doc.gwos.org/index.php/BerylOnEdgy[/HTML]

Any help would be appreciated on getting the second core to work.

Thanks
Dez

---

### Post by bristleburger on 2007-01-25
The 2.6.17-10-386 kernel probably only supports 1 CPU. Try K7 and if that doesn't work i686.

---

### Post by thinkdez on 2007-01-25
Haha I feel like such an idiot.  I just noticed something and I must have been so tired when I posted this cause I realized my problem.  I updated the Kernel to 2.6.17-10-i386 instead of using the 2.6.17-10-generic. Doh!  How did I miss that.  All is well. I should have paid more attention when upgrading but I didn't notice that.

Thanks for your help.

Dez

---

