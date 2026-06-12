---
title: "Error with curl"
date: 2013-10-16
forum: General Help
---

### Post by davidtuti2 on 2013-10-16
Hi 

I'm trying to get source code of a url but it gives me an error. Could you help me please?

```
curl -v http://www.segundamano.es/anuncios-madrid/ -m 10* About to connect() to www.segundamano.es port 80 (#0)
*   Trying 195.77.179.69...
* Connected to www.segundamano.es (195.77.179.69) port 80 (#0)
> GET /anuncios-madrid/ HTTP/1.1
> User-Agent: curl/7.29.0
> Host: www.segundamano.es
> Accept: */*
>
* Empty reply from server
* Connection #0 to host www.segundamano.es left intact
curl: (52) Empty reply from server



```

Any help please?
Many thanks and sorry for my english!

---

### Post by fantab on 2013-10-16
I think there's some problem with the website: 
[http://www.segundamano.es/anuncios-madrid/](http://www.segundamano.es/anuncios-madrid/)

---

### Post by Lars Noodén on 2013-10-16
I'm getting this error when trying to connect:  502 Bad Gateway
So the problem is probably  not with how you are trying to use curl.

---

