---
title: "Apache question... non-root user? I'm trying install lamp server"
date: 2015-01-12
forum: General Help
---

### Post by DiogoSaraiva on 2015-01-12
Hi,
I saw where i don't remember where, something like that I have to create a non root user with less root privileges to manage my virtual hosts, etc..., is this true?


Other question when I try to install lamp server..
appears this:


```
150112 20:17:03 [Warning] Using unique option prefix key_buffer instead of key_buffer_size is deprecated and will be removed in a future release. Please use the full name instead.
mysql start/running, process 6122

```

with ```
apt-get install lamp-server^
``` as well when I install php and mysql separately...


I have already apache....

By the way can you verify if my website is secure for me
[dxcluster.cr7akg.com]("http://dxcluster.cr7akg.com")

Another question:

How can my website access a the content of a folder named "icons" like this one: 
http://dxcluster.cr7akg.com/icons/ubuntu-logo.png


Thank you very much in advance and have a nice day...

---

### Post by CharlesA on 2015-01-12
Apache already runs as the www-data user, which has limited privileges.

As far as securing Apache, there are a ton of different guides online, but Apache should be fairly secure out of the box.

No one can tell you if your site is secure or not. It all depends on your web server, what language the site is written in and if you are running and software on top of the web server (WordPress, etc).

That png looks to be accessible from your home page.

---

