---
title: "python-mutagen problem"
date: 2007-03-04
forum: General Help
---

### Post by mykalreborn on 2007-03-04
i wanted to install the brand new exaile 2.9b and after i apt-get-ed the dependencies it gave me an error :
```
Errors were encountered while processing:
 python-mutagen
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python-mutagen (1.7.1-0ubuntu1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/mutagen/_constants.py
pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/mutagen/_constants.py
dpkg: error processing python-mutagen (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-mutagen
mykal@acasa:~$ 

```

oddly enough, exaile still worked. i got this error twice more, when i had to install a software but both times the program worked. also i've tried to reinstall python-mutagen, but i keep getting the same thing.
is this a big problem? and how can i fix it?
thanks! cheers!

---

### Post by Kuoi on 2007-04-19
I had about the same problem with Listen.

I did a full uninstall in 'aptitude' of Phyton-mutagen.
It did uninstall Listen and Exaile too.

After this I installed Phyton-mutagen again in 'aptitude'.
After this I installed Listen again , and now all is working well.

Hope this helps for you too.

Kuoi

---

