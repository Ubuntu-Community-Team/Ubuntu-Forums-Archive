---
title: "libpcsclite1, libraries are missing?"
date: 2013-06-07
forum: General Help
---

### Post by bjorntj on 2013-06-07
Just installed libpcsclite1 because I need Java to access my smartcard reader... But I can not find any library that start with libpcsclite* after the install...
Is there something wrong with the package or am I missing something else?

btw, I am using Ubuntu 13.04...

Regards,

BTJ

---

### Post by Frogs Hair on 2013-06-07
I find it to be installed when I check synaptic on my 13.04 installation.

---

### Post by bjorntj on 2013-06-08
Yes, it is installed... But when I do this..:

find /usr -name 'libpcsc*'


the search come up empty...



BTJ

---

### Post by Frogs Hair on 2013-06-08
I get permission denied without sudo , but here is the output .

```
sudo find /usr -name 'libpcsc*'[sudo] password for david: 
/usr/share/doc/libpcsclite

```

---

### Post by bjorntj on 2013-06-08
Yes, but that it just the docs and not the needed libraries, that should be in /usr/lib...

BTJ

---

### Post by steeldriver on 2013-06-08
Did you check /lib? there are several hits on the web suggesting it got moved there for compatibility with Debian (something about needing the library to be available before /usr is mounted)

---

### Post by Frogs Hair on 2013-06-08
I find what appear to be scripts in /var/lib/dpkg/info . This is not my computer and was upgraded so I hope the location  is the same. Strange , that it was located with the Gnome search tool. I see no other locations for this package.

---

### Post by bjorntj on 2013-06-08
> **steeldriver said:**
> Did you check /lib? there are several hits on the web suggesting it got moved there for compatibility with Debian (something about needing the library to be available before /usr is mounted)

Hmmm... It didn't occur to me to check there... But there it was..... Thx... :)

BTJ

---

