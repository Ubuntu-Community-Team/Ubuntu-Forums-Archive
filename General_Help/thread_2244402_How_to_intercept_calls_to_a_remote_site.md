---
title: "How to intercept calls to a remote site?"
date: 2014-09-16
forum: General Help
---

### Post by sim085 on 2014-09-16
Hello,

I do not know if this is a linux or browser question; When I am working on a website I load some items from a remote server. However this means that such resources cannot be accessed if I do not have Internet access. Is there a way how I can capture any request for [http://example.com/image.png](http://example.com/image.png) and instead load this from /home/<user>/resources/image.png?

---

### Post by btindie on 2014-09-16
You can intercept the requests for example.com on your local machine by editing your /etc/hosts file, this will override what example.com resolves to and take precedence over the DNS result.
```
127.0.0.1        example.com
```

Then install nginx (sudo apt-get install nginx-light) and create a config for it under /etc/nginx/sites-available/example.com
```
server {
        server_name     example.com;
        listen          80;
        root            /home/USER/resources;
        location / {
               try_files $uri;
               allow    127.0.0.1;
               deny     all;
        }
}
```

Then enable the site and reload nginx.
```
sudo ln -sf /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/example.com
sudo service nginx reload
```

You may already be running something locally so you'd need to tailor to your needs.

---

### Post by sim085 on 2014-09-16
Thanks for the help. That is what I was looking for :)

---

