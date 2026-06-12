---
title: "Debconf Error"
date: 2006-07-03
forum: General Help
---

### Post by souled on 2006-07-03
Something seems to have happened to my debconf package. Whenever I try to install anything, debconf tries to get configured. Here's what I get when I try sudo apt-get install debconf

```
 1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up debconf (1.5.2ubuntu1) ...
Compiling /usr/lib/python2.4/site-packages/twisted/test/stdio_test_halfclose.py ...
  File "/usr/lib/python2.4/site-packages/twisted/test/stdio_test_halfclose.py", line 20
    ???
    ^
SyntaxError: invalid syntax

dpkg: error processing debconf (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 debconf
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
```

Can anyone help me?

---

### Post by souled on 2006-07-04
Anyone have any thoughts?

---

