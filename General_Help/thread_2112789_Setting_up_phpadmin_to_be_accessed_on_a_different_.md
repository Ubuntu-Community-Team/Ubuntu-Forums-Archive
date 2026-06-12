---
title: "Setting up phpadmin to be accessed on a different port using nginx"
date: 2013-02-05
forum: General Help
---

### Post by miocene on 2013-02-05
So I'm running Ubuntu on my VPS for the purpose of being a webserver and am trying to set up phpmyadmin to be accessed on port 8084. As a novice with this type of thing I'm following [this guide]("http://www.wpmayor.com/step-by-step/ultimate-guide-setting-wordpress-vps-part-2/"). Everything has worked so far except for 2 things:
1. in  order to get php to work I had to uncomment this line in *[FONT="Courier New"]/etc/nginx/sites-available/default[/FONT]*: ```
fastcgi_pass unix:/var/run/php5-fpm.sock;
``` rather than the line it said to: ```
fastcgi_pass 127.0.0.1:9000;
```

I then installed MySQL and phpmyadmin and followed the instructions until the point where it describes how to get phpmyadmin running through a different port. Here I edited the phpmyadmin file in sites-available to the following:
```

server {
    listen   8084;
    server_name 95.142.166.209;
    access_log /var/log/nginx/localhost.access.log;
    root   /usr/share/phpmyadmin;
    index  index.php;
    location / {
        try_files $uri $uri/ @phpmyadmin;
    }
    location @phpmyadmin {
        fastcgi_pass 127.0.0.1:9000;
        fastcgi_param SCRIPT_FILENAME /usr/share/phpmyadmin/index.php;
        include /etc/nginx/fastcgi_params;
        fastcgi_param SCRIPT_NAME /index.php;
    }
    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    location ~ \.php$ {
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_index  index.php;
        fastcgi_param  SCRIPT_FILENAME  /usr/share/phpmyadmin$fastcgi_script_name;
        include        fastcgi_params;
    }
}
```

I tried visiting my server on port 8084 as it descibes by going to [http://95.142.166.209:8084](http://95.142.166.209:8084) but I get a [COLOR="Navy"]502 Bad Gateway[/COLOR] page.

Normal php files in the web root work fine. E.g. I made a test php file, hello.php, which contains a [COLOR="Green"]*hello world*[/COLOR] script and [COLOR="Green"]*phpinfo()*[/COLOR] function and it works fine when visiting [http://95.142.166.209/hello.php](http://95.142.166.209/hello.php).

Any ideas how to get phpmyadmin working the way I describe?

Edit: here is my error log:
```
2013/02/05 00:15:09 [info] 6676#0: Using 32768KiB of shared memory for push module in /etc/nginx/nginx.conf:73
2013/02/05 00:35:53 [info] 6723#0: Using 32768KiB of shared memory for push module in /etc/nginx/nginx.conf:73
2013/02/05 00:35:57 [error] 6728#0: *1 connect() failed (111: Connection refused) while connecting to upstream, client: 81.107.86.251, server: 95.142.166.209, request: "GET / HTTP/1.1", upstream: "fastcgi://127.0.0.1:9000", host: "95.142.166.209:8084"
2013/02/05 00:36:08 [error] 6728#0: *1 connect() failed (111: Connection refused) while connecting to upstream, client: 81.107.86.251, server: 95.142.166.209, request: "GET / HTTP/1.1", upstream: "fastcgi://127.0.0.1:9000", host: "95.142.166.209:8084"
2013/02/05 00:39:24 [error] 6728#0: *9 connect() failed (111: Connection refused) while connecting to upstream, client: 81.107.86.251, server: 95.142.166.209, request: "GET / HTTP/1.1", upstream: "fastcgi://127.0.0.1:9000", host: "95.142.166.209:8084"
2013/02/05 00:45:14 [error] 6728#0: *14 connect() failed (111: Connection refused) while connecting to upstream, client: 81.107.86.251, server: 95.142.166.209, request: "GET / HTTP/1.1", upstream: "fastcgi://127.0.0.1:9000", host: "95.142.166.209:8084"
2013/02/05 00:56:40 [error] 6728#0: *16 connect() failed (111: Connection refused) while connecting to upstream, client: 81.107.86.251, server: 95.142.166.209, request: "GET / HTTP/1.1", upstream: "fastcgi://127.0.0.1:9000", host: "95.142.166.209:8084"
2013/02/05 00:58:21 [error] 6728#0: *19 connect() failed (111: Connection refused) while connecting to upstream, client: 81.107.86.251, server: 95.142.166.209, request: "GET / HTTP/1.1", upstream: "fastcgi://127.0.0.1:9000", host: "95.142.166.209:8084"
2013/02/05 00:58:21 [error] 6728#0: *19 connect() failed (111: Connection refused) while connecting to upstream, client: 81.107.86.251, server: 95.142.166.209, request: "GET / HTTP/1.1", upstream: "fastcgi://127.0.0.1:9000", host: "95.142.166.209:8084"
2013/02/05 10:34:49 [error] 6728#0: *51 connect() failed (111: Connection refused) while connecting to upstream, client: 97.92.32.40, server: 95.142.166.209, request: "GET / HTTP/1.1", upstream: "fastcgi://127.0.0.1:9000", host: "95.142.166.209:8084"
2013/02/05 11:06:08 [error] 6728#0: *62 connect() failed (111: Connection refused) while connecting to upstream, client: 87.213.105.124, server: 95.142.166.209, request: "GET / HTTP/1.1", upstream: "fastcgi://127.0.0.1:9000", host: "95.142.166.209:8084"
2013/02/05 13:55:50 [error] 6728#0: *65 FastCGI sent in stderr: "Primary script unknown" while reading response header from upstream, client: 58.218.199.250, server: localhost, request: "GET http://www.travelimgusa.com/ip.php HTTP/1.1", upstream: "fastcgi://unix:/var/run/php5-fpm.sock:", host: "www.travelimgusa.com"
2013/02/05 19:49:52 [error] 6728#0: *90 connect() failed (111: Connection refused) while connecting to upstream, client: 81.107.86.251, server: 95.142.166.209, request: "GET / HTTP/1.1", upstream: "fastcgi://127.0.0.1:9000", host: "95.142.166.209:8084"

```

---

### Post by ne0genius on 2013-04-09
miocene,

I see you resolved this issue, and I happen to have a similar setup and have followed the exact same tutorial and run into the identical issue. Can you please post the updates you made to fix this issue? Thanks!

---

### Post by miocene on 2013-04-11
The answer to resolving this is to use 
```
fastcgi_pass unix:/var/run/php5-fpm.sock;
```
instead of 
```
fastcgi_pass 127.0.0.1:9000;
```
in the nginx config file for the site.

This is the method Nginx uses to connect to fastCGI. Apparently there is not a lot in it which one you use. It seems the TCP method is broken on my server and I don't know how to fix it so I just use the bind to socket file method instead.

---

### Post by ne0genius on 2013-04-11
Thanks so much. Turned out I was having firewall issues, which I have since resolved. But thank you for taking the time to respond.

---

