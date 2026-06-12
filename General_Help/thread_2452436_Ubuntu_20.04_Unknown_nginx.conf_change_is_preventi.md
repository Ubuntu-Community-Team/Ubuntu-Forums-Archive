---
title: "Ubuntu 20.04: Unknown nginx.conf change is preventing access from internet"
date: 2020-10-22
forum: General Help
---

### Post by blackagave2 on 2020-10-22
EDIT: RESOLVED! External IP address changed.

Running Ubuntu 20.04

Router is at the boundary has this set up for port forwarding(using 123.4.5.678)

```

FTP_ALG Server        2021        123.4.5.678    BOTH            
FTP Server            20,21    21    123.4.5.678    BOTH            
HTTP Server            80            123.4.5.678    BOTH            
HTTPS Server        443            123.4.5.678    BOTH       
40000:50000                        123.4.5.678    TC

```

running ufw
```

sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
20/tcp                     ALLOW       Anywhere                  
21/tcp                     ALLOW       Anywhere                  
990/tcp                    ALLOW       Anywhere                  
40000:50000/tcp            ALLOW       Anywhere                  
Samba                      ALLOW       Anywhere                  
Nginx Full                 ALLOW       Anywhere                  
Nginx HTTP                 ALLOW       Anywhere                  
80                         ALLOW       Anywhere                  
20/tcp (v6)                ALLOW       Anywhere (v6)             
21/tcp (v6)                ALLOW       Anywhere (v6)             
990/tcp (v6)               ALLOW       Anywhere (v6)             
40000:50000/tcp (v6)       ALLOW       Anywhere (v6)             
Samba (v6)                 ALLOW       Anywhere (v6)             
Nginx Full (v6)            ALLOW       Anywhere (v6)             
Nginx HTTP (v6)            ALLOW       Anywhere (v6)             
80 (v6)                    ALLOW       Anywhere (v6)             

```

nginx.conf
```

user www-data;
worker_processes auto;
pid /run/nginx.pid;
include /etc/nginx/modules-enabled/*.conf;

events {
    worker_connections 768;
    # multi_accept on;
}

http {

    ##
    # Basic Settings
    ##

    sendfile on;
    tcp_nopush on;
    tcp_nodelay on;
    keepalive_timeout 65;
    types_hash_max_size 2048;
    # server_tokens off;

    server_names_hash_bucket_size 64;
    # server_name_in_redirect off;

    include /etc/nginx/mime.types;
    default_type application/octet-stream;

    ##
    # SSL Settings
    ##

    ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3; # Dropping SSLv3, ref: POODLE
    ssl_prefer_server_ciphers on;

    ##
    # Logging Settings
    ##

    access_log /var/log/nginx/access.log;
    error_log /var/log/nginx/error.log;

    ##
    # Gzip Settings
    ##

    gzip on;

    # gzip_vary on;
    # gzip_proxied any;
    # gzip_comp_level 6;
    # gzip_buffers 16 8k;
    # gzip_http_version 1.1;
    # gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;

    ##
    # Virtual Host Configs
    ##

    include /etc/nginx/conf.d/*.conf;
    include /etc/nginx/sites-enabled/*;
}

```

site-available definition
```

server {
        listen 80;
        listen [::]:80;

        root /var/www/example.co/html;
        index index.html index.htm index.nginx-debian.html;

        server_name example.co ntls.example.co;

        location / {
                try_files $uri $uri/ =404;
        }
}


```

I'm attempting to set up a basic website and ftp ran off this computer. I had this "working" but it was using xip.io and I've switched to a full domain. Does anything jump out to anyone?

---

