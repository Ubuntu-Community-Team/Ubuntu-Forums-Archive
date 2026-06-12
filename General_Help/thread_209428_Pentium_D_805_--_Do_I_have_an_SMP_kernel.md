---
title: "Pentium D 805 -- Do I have an SMP kernel?"
date: 2006-07-05
forum: General Help
---

### Post by thomas.hood on 2006-07-05
I've just done a fresh install of 6.06 (32bit) and wondered if I've SMP support for my dual core Pentium D CPU. How do I tell?

I installed the 32 bit distro (ubuntu-6.06-desktop-i386.iso) as I see there are various broken packages and other issues with 64bit for dubious benefits.

Thanks,

Thomas Hood

---

### Post by patrickfromspain on 2006-07-05
You have to install the 686 kernel in order to have SMP support:

sudo apt-get install linux-image-686

---

### Post by Jagot on 2006-07-05
The 686 kernel doesn't have SMP support as far as I know - it's just for 686 processors.  You need:

```
sudo aptitude install linux-686-smp
```

---

### Post by patrickfromspain on 2006-07-05
The 686-dapper kernel has SMP support, you won't find any 2.6.15 smp kernel in the repos ;)

---

### Post by thomas.hood on 2006-07-05
Will upgrading this effect anything else? Will all my packages be upgraded?

I don't want to bugger-up a working system....

Thanks,

Tom

---

### Post by JoWilly on 2006-07-06
[quote=thomas.hood]Will upgrading this effect anything else? Will all my packages be upgraded?

I don't want to bugger-up a working system....

Thanks,

Tom[/quote] 
The i686 kernel definitely HAS smp support.

No, it won't update anything else. Just make sure that you also install the linux-restricted-modules for this kernel (contain nvidia,ati,wifi, etc.. drivers).

---

