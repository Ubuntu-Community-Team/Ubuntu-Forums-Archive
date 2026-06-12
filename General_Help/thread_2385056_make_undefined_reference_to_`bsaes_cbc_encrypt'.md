---
title: "make: undefined reference to `bsaes_cbc_encrypt'"
date: 2018-02-15
forum: General Help
---

### Post by slowerphoton on 2018-02-15
I am trying to install OpenSSL on my laptop with Ubuntu (Xenial). However none of the "fips releases" can make it through make. If we talk specifically about **OpenSSL-fips-2_0_13**, this is what make returns before exiting:

```

    ../libcrypto.a(e_aes.o): In function `aes_init_key':
    e_aes.c:(.text+0x267): undefined reference to `bsaes_cbc_encrypt'
    collect2: error: ld returned 1 exit status
```


What does it mean? What additional information should I include in this post?


The way I install it:


I download the version from the official OpenSSL github account as tar.gz, I unpack it, call ```
./config --prefix=[some_address] --openssldir=[some_address]/openssl
```, which exits succesfully and I follow it immediately with ```
make
```.

---

