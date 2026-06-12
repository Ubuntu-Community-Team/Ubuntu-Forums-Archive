---
title: "Is OwnCloud safe to install"
date: 2015-01-06
forum: General Help
---

### Post by DiogoSaraiva on 2015-01-06
Hi,
I heard about that ownCloud is little insecure... is this true?
I want install it, should I modify my firewall or so?  how?

I have apache websites in the same computer...


Thank you very much and have a nice day...
Diogo

---

### Post by DiogoSaraiva on 2015-01-11
anyone???

---

### Post by dragonfly41 on 2015-01-11
I have no experience with OwnCloud .. but a few minutes searching shows these which might answer your question ...

[http://www.cvedetails.com/vulnerability-list/vendor_id-11929/Owncloud.htm](http://www.cvedetails.com/vulnerability-list/vendor_id-11929/Owncloud.htm)

[http://www.webupd8.org/2014/10/owncloud-ubuntu-package-affected-by.html](http://www.webupd8.org/2014/10/owncloud-ubuntu-package-affected-by.html)

---

### Post by starkruzr1701 on 2015-01-11
It's just the package. Installing from source is fine.

---

### Post by Irihapeti on 2015-01-11
The specific version that's in the repos is insecure. Get the latest version from the source and you should be OK. There's also a PPA which should make keeping updated a little easier.

---

### Post by DiogoSaraiva on 2015-01-11
One thing more: how can I install from source without kepping a folder in my user (~/) directory or so
When I install from source like this:
```

cd ~/example-app
./configure
make 
sudo make install

```
I keep always the folder itself, is it correct or can I delete it?

Or any way to make a package .deb from the source files?

by the way 

you said 
"There's also a PPA which should make keeping updated a little easier."
What is the PPA?

Thank you very much and have a nice day

---

### Post by Irihapeti on 2015-01-12
Instructions for using the ownCloud PPA are here:

[http://software.opensuse.org/download/package?project=isv:ownCloud:community&package=owncloud](http://software.opensuse.org/download/package?project=isv:ownCloud:community&package=owncloud)

I've not used it myself.

By the way, the tar.bz2 file isn't source in the traditional sense (that needs to be compiled). It is installed as is into the directory that you're using. See the [ownCloud site]("https://owncloud.org/install/") for further instructions.

---

