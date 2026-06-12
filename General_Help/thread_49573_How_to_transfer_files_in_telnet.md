---
title: "How to transfer files in telnet??"
date: 2005-07-16
forum: General Help
---

### Post by danf_1979 on 2005-07-16
I'm logged from a friends linux to my ubuntu... and i need a file. How can i transfer it, without having any ftp server?? is this possible to do with telnet?
thanks.

---

### Post by evilghost on 2005-07-16
First of all, if you're really logged in via Telnet then shame on you and your friend, Telnet is huge security vulnerability as passwords and sensitive information are passed via cleartext.  If you really mean SSH, you can use scp or sftp to transfer the files.  If you're actually using telnet, please cease and instead using ssh. ;)

---

### Post by angkor on 2005-07-17
Please follow evilghost's advice and use ssh and scp.

to transfer a file securily:

```
scp [path-to-file] [user-name@[host]:/[path-to-destination]
```

---

### Post by lasombra on 2008-06-19
Guys, your security advice is ok and I understand this point. But the question is "how you tranfer files in telnet?". Can somebody answer this, cause me for example, I need to use telnet for testing purposes. So how I transfer files?

---

### Post by evilghost on 2008-06-19
> **lasombra said:**
> Guys, your security advice is ok and I understand this point. But the question is "how you tranfer files in telnet?". Can somebody answer this, cause me for example, I need to use telnet for testing purposes. So how I transfer files?

Install the lrzsz package and send the files using zmodem.

Read the man-pages for "rz" and "sz" after installing the package.

---

