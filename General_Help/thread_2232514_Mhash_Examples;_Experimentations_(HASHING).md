---
title: "Mhash Examples; Experimentations (HASHING)"
date: 2014-07-02
forum: General Help
---

### Post by g35celicaz on 2014-07-02
Hello,

I have just installed mhash on Ubuntu 12.04 and I am trying to use it 

Here is the website: [http://mhash.sourceforge.net/](http://mhash.sourceforge.net/)

I have tried performing the second exampe displayed on this page: [http://mhash.sourceforge.net/mhash.3.html](http://mhash.sourceforge.net/mhash.3.html)

But I get the following errors: 

mhash.c:(.text+0x6c): undefined reference to `mhash_get_hash_pblock'
mhash.c:(.text+0x82): undefined reference to `mhash_hmac_init'
mhash.c:(.text+0x9c): undefined reference to `mhash'
mhash.c:(.text+0xa8): undefined reference to `mhash_hmac_end'
mhash.c:(.text+0xf9): undefined reference to `mhash_get_block_size'
collect2: error: ld returned 1 exit status

From what I have read, it is just an interface? However based on the source code given, could anyone help me understand if I have the implement the hashing algorithms myself?! Eventhough it says it supports over 27 hashing algorithms? 

Thanks for your support in advance

---

### Post by steeldriver on 2014-07-02
please post the exact build command that you're using

---

### Post by g35celicaz on 2014-07-03
I was trying to run this:

 ```
#include <mhash.h>
 #include <stdio.h>
 int main()
 {
        char password[] = "Jefe";
        int keylen = 4;
        char data[] = "what do ya want for nothing?";
        int datalen = 28;
        MHASH td;
        unsigned char *mac;
        int j;

        td = mhash_hmac_init(MHASH_MD5, password, keylen,
                            mhash_get_hash_pblock(MHASH_MD5));
        mhash(td, data, datalen);
        mac = mhash_hmac_end(td);
 /* 
  * The output should be 0x750c783e6ab0b503eaa86e310a5db738
  * according to RFC 2104.
  */
        printf("0x");
        for (j = 0; j < mhash_get_block_size(MHASH_MD5); j++) {
                printf("%.2x", mac[j]);
        }
        printf("\n");

        exit(0);
 }
```

Thanks!

---

