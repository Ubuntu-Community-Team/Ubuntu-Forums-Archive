---
title: "nginx reverse proxy help"
date: 2017-09-25
forum: General Help
---

### Post by shoeleshunter78 on 2017-09-25
I am using Ubuntu 17.04.

I am trying to use nginx to proxy requests to a ghost blog running on port 2368.

When I visit mydomain.com:2368, I see the site is up and running.

Here is the configuration of /etc/nginx/sites-available/ghost:

server {
    listen 0.0.0.0:80;
    server_name mydomain.com;
    access_log /var/log/nginx/mydomain.log;


    location / {
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header HOST $http_host;
        proxy_set_header X-NginX-Proxy true;


        proxy_pass [http://127.0.0.1:2368;](http://127.0.0.1:2368;)
        proxy_redirect off;
    }
}

This is linked to /etc/nginx/sites-enabled/ghost.

But, when I visit [http://mydomain.com](http://mydomain.com), I get the nginx welcome page instead.

Ideas?

---

