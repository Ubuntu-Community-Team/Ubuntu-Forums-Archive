---
title: "dig and nslookup commands are failing with a symbol lookup error"
date: 2021-11-11
forum: General Help
---

### Post by orionm42 on 2021-11-11
I can't pin down exactly when this happened as I don't run these commands overly often. General DNS resolution must be working seeing as I am asking this question.


I've seen similar issues on this site but the answers didn't seem applicable. As far as I know, just dig and nslookup are affected. wget and curl are both able to resolve URLs.

```
adam@latitude-7400:~$ nslookupnslookup: symbol lookup error: /lib/x86_64-linux-gnu/libisc.so.1601: undefined symbol: deflate
adam@latitude-7400:~$ dig
dig: symbol lookup error: /lib/x86_64-linux-gnu/libisc.so.1601: undefined symbol: deflate
adam@latitude-7400:~$ ldd /lib/x86_64-linux-gnu/libisc.so.1601
    linux-vdso.so.1 (0x00007fff7a472000)
    libcrypto.so.1.1 => /lib/x86_64-linux-gnu/libcrypto.so.1.1 (0x00007f0b01921000)
    libuv.so.1 => /lib/x86_64-linux-gnu/libuv.so.1 (0x00007f0b018f0000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f0b018cd000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f0b018c7000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f0b016d5000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f0b01c82000)
adam@latitude-7400:~$ ls -l /lib/x86_64-linux-gnu/libisc.so.1601
lrwxrwxrwx 1 root root 18 Oct 27 12:00 /lib/x86_64-linux-gnu/libisc.so.1601 -> libisc.so.1601.0.0

```

---

### Post by Doug S on 2021-11-11
Readers: See the same question on [askubuntu]("https://askubuntu.com/questions/1374876/dig-and-nslookup-commands-are-failing-with-a-symbol-lookup-error").

---

