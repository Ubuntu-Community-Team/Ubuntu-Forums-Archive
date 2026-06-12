---
title: "openssl library and header different with the upgrade openssl version"
date: 2018-12-03
forum: General Help
---

### Post by edicande0477 on 2018-12-03
Hi all,

my office server is running old ubuntu 10.04 LTS and I just upgraded openssl version from 0.9.8k to 1.0.2k a month ago, no crash issue or error issue,
but when I check from 'checkphp.php' it still show the old version:
[TABLE="width: 600"]
[TR]
[TD="class: e, bgcolor: #CCCCFF"]OpenSSL support[/TD]
[TD="class: v, bgcolor: #CCCCCC"]enabled[/TD]
[/TR]
[TR]
[TD="class: e, bgcolor: #CCCCFF"]OpenSSL Library Version[/TD]
[TD="class: v, bgcolor: #CCCCCC"]OpenSSL 0.9.8k 25 Mar 2009[/TD]
[/TR]
[TR]
[TD="class: e, bgcolor: #CCCCFF"]OpenSSL Header Version[/TD]
[TD="class: v, bgcolor: #CCCCCC"]OpenSSL 0.9.8k 25 Mar 2009[/TD]
[/TR]
[/TABLE]

but if check it from terminal: 
$ openssl version
the output is: OpenSSL 1.0.2k 26 Jan 2017  -(updated version)

so it means there are 2 openssl verison installed on my ubuntu now.

$ /usr/bin/openssl version
OpenSSL 0.9.8k 25 Mar 2009

$ /usr/local/ssl/bin/openssl version
OpenSSL 1.0.2k 26 Jan 2017

I install the new openssl 1.0.2k follow this instruction by S.Gordon:
 $ wget [http://www.openssl.org/source/openssl-1.0.0k.tar.gz](http://www.openssl.org/source/openssl-1.0.0k.tar.gz)
$ tar xzvf openssl-1.0.0k.tar.gz
$ cd openssl-1.0.0k
$ ./config
$ make
$ make test
$ sudo make install

edit /etc/manpath.config: MANPATH_MAP     /usr/local/ssl/bin      /usr/local/ssl/man
edit /etc/environment: PATH="/usr/local/sbin:/usr/local/bin:/usr/local/ssl/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

$ openssl version
OpenSSL 1.0.0k 26 Jan 2017


Any way that I can update or change the openssl library and header in checkphp.php become to a new version 1.0.2k?

appreciate for any help from you.

---

