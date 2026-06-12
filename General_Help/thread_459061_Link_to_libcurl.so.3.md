---
title: "Link to libcurl.so.3"
date: 2007-05-30
forum: General Help
---

### Post by Kuraudo on 2007-05-30
I get the error "error while loading shared libraries: libcurl.so.3: cannot open shared object file: No such file or directory"

I found this FAQ, [http://curl.haxx.se/docs/faq.html#5.8](http://curl.haxx.se/docs/faq.html#5.8) so I know what my problem is but I don't know how to solve it. How can I link it right so it finds the library?

---

### Post by kaamos on 2007-05-30
Have you installed the package libcurl3 ?

---

### Post by Kuraudo on 2007-05-30
> **kaamos said:**
> Have you installed the package libcurl3 ?

Yes it's installed.

```
$ sudo apt-get install libcurl3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcurl3 is already the newest version.
```

```
$ curl --version
curl 7.15.5 (x86_64-pc-linux-gnu) libcurl/7.15.5 OpenSSL/0.9.8c zlib/1.2.3 libidn/0.6.5
Protocols: tftp ftp telnet dict ldap http file https ftps 
Features: GSS-Negotiate IDN IPv6 Largefile NTLM SSL libz
```

Edit: Okay I tried to extend my search path by.
```
$ export LD_LIBRARY_PATH=/usr/lib
```

But now I get the error *"error while loading shared libraries: libcurl.so.3: wrong ELF class : ELFCLASS64"*.
My guess is that I need the 32-bit version because the program (qbittorrent) I'm trying to run was installed with --force-architecture since I run amd64.

Should this mean I need to install the 32-bit version of libcurl3? How do I do that?

---

### Post by Virgilius on 2007-06-04
I am having similar problems with my libcurl library, the terminal spits out the following:

```
configure: error:  *** Unable to find CURL library (http://curl.haxx.se/) 

``` I have version 7 of libcurl. Help me out here please!

---

