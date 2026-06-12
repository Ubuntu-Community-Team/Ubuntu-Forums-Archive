---
title: "Pam_mysql.so error"
date: 2017-10-16
forum: General Help
---

### Post by mcparty2 on 2017-10-16
Hi folks,

In Ubuntu16.04 i am trying to get FreeRADIUS to use Pam & MySQL for authentication.
My problem is pam_mysql.so keeps throwing up an error.

```
Linux radius01 4.4.0-97-generic #120-Ubuntu SMP Tue Sep 19 17:28:18 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```


```

Oct 16 16:15:51 freeradius: PAM unable to dlopen(/lib/security/pam_mysql.so): /lib/security/pam_mysql.so: undefined symbol: make_scrambled_password_323
Oct 16 16:15:51 freeradius: PAM adding faulty module: /lib/security/pam_mysql.so
```

```

ldd -r /lib/security/pam_mysql.so
    linux-vdso.so.1 =>  (0x00007ffe533c2000)
    libpam.so.0 => /lib/x86_64-linux-gnu/libpam.so.0 (0x00007f0adf491000)
    libmysqlclient.so.18 => /usr/lib/x86_64-linux-gnu/libmysqlclient.so.18 (0x00007f0adee81000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f0adec64000)
    libcrypt.so.1 => /lib/x86_64-linux-gnu/libcrypt.so.1 (0x00007f0adea2c000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f0ade662000)
    libaudit.so.1 => /lib/x86_64-linux-gnu/libaudit.so.1 (0x00007f0ade43b000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f0ade237000)
    libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f0ade01d000)
    libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f0addc9b000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f0add992000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f0add77c000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f0adf8aa000)
undefined symbol: make_scrambled_password_323    (/lib/security/pam_mysql.so)
```


```
ii  libpam-mysql                        0.7~RC1-4ubuntu2                           amd64        PAM module allowing authentication from a MySQL server
```


Any ideas on how to fix this would be super helpful.

Many thanks

---

### Post by mcparty2 on 2017-10-17
It looks like a bug - There is a .deb link on the page which seems to work fine for me for now.
The link is here for anyone that wants a read & to try. I'm sure it wont be long before it is released officially (so try at your own peril!)

[https://bugs.launchpad.net/ubuntu/xenial/+source/pam-mysql/+bug/1574900/comments/23](https://bugs.launchpad.net/ubuntu/xenial/+source/pam-mysql/+bug/1574900/comments/23)

Thanks again folks

---

