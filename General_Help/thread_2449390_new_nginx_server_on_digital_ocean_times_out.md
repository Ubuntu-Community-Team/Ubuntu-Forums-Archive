---
title: "new nginx server on digital ocean times out"
date: 2020-08-25
forum: General Help
---

### Post by ELMIT on 2020-08-25
(maybe I am just impatient, ...)

I followed [https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-ubuntu-20-04) setup receipt.
uname -a
```
Linux courses 5.4.0-42-generic #46-Ubuntu SMP Fri Jul 10 00:24:02 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

If I use in my browser the IP address, then I get the Welcome to Nginx screen. That shows me that the firewall is ok, and that the default nginx conf is ok.
If I use the host name  abc.example.com  I get time out.

If I use on DigitalOcean host abc.example.com  I get 
```
abc.example.com  has address 127.0.1.1
```

resolvectl status  shows me the default dns as 67.207.67.3

host abc.example.com 67.207.67.3

```
Using domain server:
Name: 67.207.67.3
Address: 67.207.67.3#53
Aliases: 

abc.example.com has address aaa.bbb.ccc.ddd
abc.example.com has IPv6 address AAAA:BBBB:DDDD:EEEE::HHHH:7001

```
cat /etc/nginx/sites-available/abc.example.com 
```
server {
    listen 80;
    server_name abc.example.com;
    root /var/www/abc.example.com;

    index index.html index.htm index.php;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
     }

    location ~ /\.ht {
        deny all;
    }

}
```

ls -la /var/www/abc.example.com
```
total 16
drwxr-xr-x 2 root   root   4096 Aug 25 14:04 .
drwxr-xr-x 4 root   root   4096 Aug 25 13:33 ..
-rw-rw-r-- 1 ronald ronald  200 Aug 25 13:56 index.html
-rw-rw-r-- 1 ronald ronald   17 Aug 25 14:04 info.php
```


What do I miss?

---

### Post by QIII on 2020-08-25
I doubt that abc.example.com will be resolved to your website by DNS servers since it is likely not registered -- even less so registered with your IP address.

For testing, you will need to use the IP address.  You can, however, add something like the following to /etc/hosts:

```
123.456.7.89 flibbertygibbits.com
```

---

### Post by ELMIT on 2020-08-25
abc.example.com is not the host I use, ...

---

### Post by QIII on 2020-08-26
That's an example, as was flibbertygibbits.com.

If you have anything, say thisismywebsiteondigitalocean.com, it will not be resolved if there are no A Record, for example, for a DNS server to find an IP address associated with it.

Have you set up your DNS records?

The alias for you to use your browser has to be in the hosts file on your machine.

---

### Post by ELMIT on 2020-08-26
I found it!

I must admit it was a little bit tricky!

On Digital Ocean I have the luxury to have IPv6. For IPv4 you need just listen 80;
However, I did not set up for listening on IPv6. The missing part was: listen [::]:80;

---

