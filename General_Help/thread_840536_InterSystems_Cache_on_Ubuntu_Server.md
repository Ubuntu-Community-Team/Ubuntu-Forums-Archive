---
title: "InterSystems Cache on Ubuntu Server"
date: 2008-06-25
forum: General Help
---

### Post by spurty on 2008-06-25
This is a bit of 'self help' rather than a problem. 

**Caveat lector** - This is how I fixed a problem, not an authorized solution. Use your common sense.

I'm posting this as I didn't find this issue in these pages and someone sooner or later is going to trip over it as well.

I had an issue installing Cache on a Ubuntu server and as its not an officially supported Linux platform, resorted to solving it myself.

The solution is very simple (albeit a bit of a dirty hack).

Installation fails to configure the management portal as httpd (the one they ship for their private apache webserver) is linked against libexpat.so.0 which on my system is not installed.

So, I did the following:

```
$ cd /usr/lib/

$ sudo ln -s libexpat.so.1 libexpat.so.0
```

then re-run the install.

Please don't go and do this on a production system.

---

