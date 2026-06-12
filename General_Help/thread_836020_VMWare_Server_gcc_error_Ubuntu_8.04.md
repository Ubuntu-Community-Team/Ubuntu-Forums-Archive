---
title: "VMWare Server gcc error Ubuntu 8.04"
date: 2008-06-21
forum: General Help
---

### Post by br0ken on 2008-06-21
hi everyone, let me start off saying i'm fairly new to linux.

but here is the problem i'm having, and i haven't been able to find any help on this problem yet.

i have installed VMWare server on my ubuntu 8.04 machine and installation and configuration completes fine, but VMware won't launch.. 
when i use the command vmware i get this:

```
br0ken@br0ken:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```

any help would be greatly appreciated, and also let me know if anyone needs more information about my system. thanks!


edit i was able to get it working with help i found on another post with the following commands:

```
sudo cp /lib/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/
```

---

### Post by ANewAccount on 2008-06-23
Thank you, I just ran into this problem too and your solution fixed it right up!

---

### Post by ajaygautam on 2008-07-25
It lives.
Thanks so much for the solution :)

---

### Post by abadr on 2008-09-13
indeed it lives. Thanks for the tip.

---

