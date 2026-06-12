---
title: "Squid3 setup , no internet"
date: 2016-09-05
forum: General Help
---

### Post by barbudaniel on 2016-09-05
Hello forum :)
I have a problem regarding my squid setup.
The use of the proxy server will be for external clients and not local.
After I installed Squid3 and configured everything I get only " No Internet Connection" from all the ip's.
My setup has a XXX.XXX.XXX.XXX/24 subnet and at the moment just one client with an external ip .

The port 3128 is by default because there is no problem with that
I attached my config file if that helps :)

[http://pastebin.com/r3nBnSzQ](http://pastebin.com/r3nBnSzQ)

---

### Post by SeijiSensei on 2016-09-05
The squid.conf file has so many comments that it is difficult to debug.  Try this.
```
grep -v '^#' < squid.conf | grep -v '^$' > squid.conf.cleaned
```
Then post the contents of squid.conf.cleaned inside [noparse]```

```[/noparse] tags like I just used.

---

