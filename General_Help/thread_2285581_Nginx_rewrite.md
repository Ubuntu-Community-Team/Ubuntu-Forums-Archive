---
title: "Nginx rewrite?"
date: 2015-07-07
forum: General Help
---

### Post by alex416 on 2015-07-07
Alright everyone, i'm new to Nginx and i want to change example.com/blah/blah.html to example.com/blah/blah
I'm brand new to Nginx, so in depth detail would be amazing! :D Thanks!

---

### Post by Plueonic on 2015-07-07
You can use 
```
try_files $uri.html $uri/ =404;
```
in the location block of your nginx.conf

You can read more about it here > [http://wiki.nginx.org/HttpCoreModule#try_files](http://wiki.nginx.org/HttpCoreModule#try_files)

---

