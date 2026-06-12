---
title: "Newbie file folder access rights"
date: 2020-08-07
forum: General Help
---

### Post by aboka on 2020-08-07
hi, i hv install Ubuntu 20.04 LTS on a vps and login as root by default. I use the command below to install & generate a certificate:

```

sudo apt install certbot python3-certbot-apache
sudo certbot --apache

```

but when i point my Shadowsocks to the path, it will give errors file cant be open. i hv confirm(by using ls), that the pem file is in there, and tried the value below-
/etc/letsencrypt/archive/mydomain/fullchain1.pem
/etc/letsencrypt/live/mydomain/fullchain.pem

so jus to be sure, its bcoz 'not authorize' issue, i copy the file into root, and it will give the same error. then i create a new folder '/var/pp/fullchain.pem' and it starts working. pls advice on how to fix this as this 'hack' is not proper way to run a program, especially when its updating the certificate


p/s - here is the default account im logon and using
root@SHADOW:~# whoami
root


thanks in advance,

---

### Post by aboka on 2020-08-07
here is the rights for both of them-
```

/etc/letsencrypt/archive/mydomain/fullchain1.pem:
drwxr-xr-x  96 root root  4096 Aug  7 20:32 etc
drwxr-xr-x  9 root root       4096 Aug  7 10:10 letsencrypt
drwx------  3 root root 4096 Aug  6 16:13 archive
drwxr-xr-x 2 root root 4096 Aug  6 16:13 mydomain
-rw-r--r-- 1 root root 3542 Aug  6 16:13 fullchain1.pem

```

```

/etc/letsencrypt/live/mydomain/fullchain.pem:
drwxr-xr-x  96 root root  4096 Aug  7 20:32 etc
drwxr-xr-x  9 root root       4096 Aug  7 10:10 letsencrypt
drwx------  3 root root 4096 Aug  6 16:13 live
drwxr-xr-x 2 root root 4096 Aug  6 16:13 mydomain
lrwxrwxrwx 1 root root   38 Aug  6 16:13 fullchain.pem -> ../../archive/mudomain/fullchain1.pem

```

i think i chmod 755 on the live fullchain earlier. and i hv read online rgd this, and it say we need to hv execute rights from the top folder down. but would doing that be risky? would be great if the installer hv set them initially

thank you,

---

### Post by aboka on 2020-08-11
well manage to solve it by adding User=root in the unitfile

---

