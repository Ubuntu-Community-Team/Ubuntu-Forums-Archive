---
title: "sudo apt-get install lyx # returns error code 2"
date: 2006-07-03
forum: General Help
---

### Post by torfinn on 2006-07-03
I tried to install lyx as follows:
$ sudo apt-get install lyx
...
...
Get:9 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe lyx 1.3.7-0ubuntu4 [17.5kB]
Fetched 8316kB in 1m1s (135kB/s)
dpkg: parse error, in file `/var/lib/dpkg/available' near line 22311 package `language-pack-xh-base' :
 field name `
E: Sub-process /usr/bin/dpkg returned an error code (2)

I have kindly been informed that:
>This is not a bug in lyc, but your package file got corrupted. If you
>need help resotring that, you can file a support request or ask on the
>mailing list.

I read up on apt-get and tried:   $sudo apt-get clean lyx
but get the same error message when retrying my install.
How can I fix my corrupted package file?

---

