---
title: "How to compile Filezilla (latest beta)?"
date: 2007-02-17
forum: General Help
---

### Post by Poka64 on 2007-02-17
Well, how do I compile the latest beta of filezilla so I can use it on edgy?
I managed to compile the latest wxwidgets but the problem is libgnutls, it needs to be newer version. The thing is that I have already compiled the latest libgnutls package out there :(

```
checking for libgnutls - version >= 1.5.4... 
*** 'libgnutls-config --version' returned 1.7.6, but LIBGNUTLS (1.4.0)
*** was found! If libgnutls-config was correct, then it is best
*** to remove the old version of LIBGNUTLS. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If libgnutls-config was wrong, set the environment variable LIBGNUTLS_CONFIG
*** to point to the correct copy of libgnutls-config, and remove the file config.cache
*** before re-running configure
configure: error:
***
*** libgnutls was not found. You may want to get it from
*** ftp://ftp.gnutls.org/pub/gnutls/
```

I can't uninstall the version that is already installed because that will uninstall many other packages that dependes on lignutls 1.4.0

---

### Post by rko618 on 2007-02-17
I was under the impression that filezilla is a Windows app only?

EDIT: Ah never mind, I just checked their website and see that the next version will be platform independent! Sweet

However I still cannot help you with your problem sorry.

---

### Post by aysiu on 2007-02-17
[FileZilla is available through the Edgy backports](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=filezilla&searchon=name&subword=1&version=all&release=all). No need to compile it.

---

### Post by Poka64 on 2007-02-17
aysiu: that's an old beta that has been backported

---

### Post by rko618 on 2007-02-21
> **aysiu said:**
> [FileZilla is available through the Edgy backports](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=filezilla&searchon=name&subword=1&version=all&release=all). No need to compile it.

poka64 is right.  Any chance of getting the latest beta, beta6 in the backports?

---

### Post by Poka64 on 2007-02-22
> **rko618 said:**
> poka64 is right.  Any chance of getting the latest beta, beta6 in the backports?

I don't think it will backported because it needs a newer version of Gnutls and wxWIidgets :(

---

