---
title: "multiple nginx reverse proxy"
date: 2015-11-27
forum: General Help
---

### Post by poliz8z on 2015-11-27
hello
i am trying to setup multiple nginx reverse proxy 
current i have 1 reverse proxy 
example:
[IMG]http://i.imgur.com/CPGbvnc.png?1[/IMG]

example.com point to reverse proxy ip 
and this is the config in reverse proxy server
[FONT=Arial]server {
  listen 80;
  server_name example.com;
  access_log off;
  error_log off;
  location / {
  proxy_pass [http://ip/;](http://ip/;) = the ip the website where website files are located 
    proxy_set_header Host      $host;
    proxy_set_header X-Real-IP $remote_addr;
    access_log  off;
    log_not_found   off;

[FONT=Arial]} }[/FONT]





[/FONT]

---

