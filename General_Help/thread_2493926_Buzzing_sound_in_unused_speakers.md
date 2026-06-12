---
title: "Buzzing sound in unused speakers"
date: 2023-12-30
forum: General Help
---

### Post by daanheuvelbeuk on 2023-12-30
Since last week I have speakers that are buzzing. And in Linux I only use my headphones. What can I do to stop the buzzing?

---

### Post by daanheuvelbeuk on 2023-12-30
Fwiw:
```

me@home:~$ pipewire
[E][00290.471616] mod.protocol-native | [module-protocol-:  660 lock_socket()] server 0x5598d5a0ed90: unable to lock lockfile '/run/user/1000/pipewire-0.lock': Resource temporarily unavailable (maybe another daemon is running)
[E][00290.471763] pw.conf      | [          conf.c:  560 load_module()] 0x5598d59f4260: could not load mandatory module "libpipewire-module-protocol-native": Resource temporarily unavailable
[E][00290.471876] default      | [      pipewire.c:  123 main()] failed to create context: Resource temporarily unavailable
me@home:~$ ls /run/user/1000/pipewire-0.lock
/run/user/1000/pipewire-0.lock
me@home:~$ ls -la /run/user/1000/pipewire-0.lock
-rw-rw---- 1 me me  0 dec 30 09:53 /run/user/1000/pipewire-0.lock
```

---

