---
title: "Busybox httpd help"
date: 2008-03-10
forum: General Help
---

### Post by I.You on 2008-03-10
Hello

I'd like to run the httpd to use cgi.
so I've installed the busybox.
and wrote httpd.conf and inetd.conf to /etc.
and mkdir /www/cgi-bin and ran httpd.
(document root is /www)

> ~# httpd
then I just tried to access to the server from a client (with brower).

> [http://ipaddress/cgi-bin/test.cgi](http://ipaddress/cgi-bin/test.cgi) (in browser)
of course, it doesn't work.

I'm a newbie in Busybox.
There are only binaries (httpd, inetd) in Busybox httpd
so I've no idea how to start (how to configure, which files to need, and so on).
Could you let me know what to do after installing busybox httpd?
or good references or sites?

Thanks in advance.

---

### Post by phrawzty on 2008-03-10
> **I.You said:**
> Could you let me know what to do after installing busybox httpd?
or good references or sites?

Since busybox httpd has very little - if anything - to do with Ubuntu specifically, i would highly suggest reading through the Busybox documentation and mailing list(s) :

[http://www.busybox.net/downloads/BusyBox.html](http://www.busybox.net/downloads/BusyBox.html)
[http://www.busybox.net/lists.html](http://www.busybox.net/lists.html)

If you're just looking for a lightweight HTTPd that's easy to set up and use, you may wish to forget Busybox altogether, and check out something like "lighttpd" :

[http://www.lighttpd.net/](http://www.lighttpd.net/)
[http://en.wikipedia.org/wiki/Lighttpd](http://en.wikipedia.org/wiki/Lighttpd)

It can be installed via apt as package "lighttpd" :

```
$ sudo apt-get install lighttpd lighttpd-doc
```

---

