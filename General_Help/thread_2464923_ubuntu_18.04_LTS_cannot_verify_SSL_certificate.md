---
title: "ubuntu 18.04 LTS cannot verify SSL certificate"
date: 2021-07-16
forum: General Help
---

### Post by rmstock2 on 2021-07-16
```

stock@bella:~/temp$ wget https://rmstock.files.wordpress.com/2021/07/letter-to-president-trump.pdf
--2021-07-16 15:26:08--  https://rmstock.files.wordpress.com/2021/07/letter-to-president-trump.pdf
Resolving rmstock.files.wordpress.com (rmstock.files.wordpress.com)... 192.0.72.16, 192.0.72.17
Connecting to rmstock.files.wordpress.com (rmstock.files.wordpress.com)|192.0.72.16|:443... connected.
ERROR: cannot verify rmstock.files.wordpress.com's certificate, issued by ‘CN=Sectigo RSA Domain Validation Secure Server CA,O=Sectigo Limited,L=Salford,ST=Greater Manchester,C=GB’:
  Unable to locally verify the issuer's authority.
To connect to rmstock.files.wordpress.com insecurely, use `--no-check-certificate'.
stock@bella:~/temp$ cat /etc/issue
Ubuntu 18.04.5 LTS \n \l

stock@bella:~/temp$ 

```

This only happens currently in Ubuntu 18.04.5 LTS. Another example :
```

stock@bella:~/temp$ youtube-dl -F https://www.youtube.com/watch?v=QN35PbqODTk 
[youtube] QN35PbqODTk: Downloading webpage
WARNING: Unable to download webpage: <urlopen error [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:727)>
[youtube] QN35PbqODTk: Downloading API JSON
ERROR: Unable to download API page: <urlopen error [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:727)> (caused by URLError(SSLError(1, u'[SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:727)'),))
stock@bella:~/temp$ 

```

---

### Post by ActionParsnip on 2021-07-16
Are you using a proxy for web access?

---

### Post by rmstock2 on 2021-07-16
> **ActionParsnip said:**
> Are you using a proxy for web access?

You made a good guess, the maintainer of that machine apparently installed a packettracer .. :

```

Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 5.4.0-65-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

2 updates can be applied immediately.
1 of these updates is a standard security update.
To see these additional updates run: apt list --upgradable

New release '20.04.2 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

Your Hardware Enablement Stack (HWE) is supported until April 2023.
You have new mail.
Last login: Fri Jul 16 18:58:20 2021 
stock@bella:~$ ldd /usr/bin/wget
        linux-vdso.so.1 (0x00007ffd6057a000)
        libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f4a44d87000)
        libuuid.so.1 => /lib/x86_64-linux-gnu/libuuid.so.1 (0x00007f4a44b80000)
        libidn2.so.0 => /usr/lib/x86_64-linux-gnu/libidn2.so.0 (0x00007f4a44963000)
        libssl.so.1.1 => /opt/pt/bin/libssl.so.1.1 (0x00007f4a446cf000)
        libcrypto.so.1.1 => /opt/pt/bin/libcrypto.so.1.1 (0x00007f4a44251000)
        libpsl.so.5 => /usr/lib/x86_64-linux-gnu/libpsl.so.5 (0x00007f4a44043000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f4a43c52000)
        libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f4a43a33000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f4a4527a000)
        libunistring.so.2 => /usr/lib/x86_64-linux-gnu/libunistring.so.2 (0x00007f4a436b5000)
        libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f4a434b1000)
stock@bella:~$ dpkg -S /opt/pt/bin/libssl.so.1.1 
packettracer: /opt/pt/bin/libssl.so.1.1
stock@bella:~$ dpkg -l packettracer
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  packettracer   7.3.1        amd64        Cisco PacketTracer 7.3.1 installa
stock@bella:~$ 

```

---

