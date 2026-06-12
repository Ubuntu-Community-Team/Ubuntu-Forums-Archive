---
title: "two bad files in whatever package"
date: 2021-07-10
forum: General Help
---

### Post by Skaperen on 2021-07-10
while running tests for a Python script i wrote (hashes the decompression of files in a directory tree) on [FONT=courier new]/usr[/FONT] (just to give it another tree to try) it encounter errors in these two files:
```

t2a/forums /home/forums 7> ls -dl --full-time /usr/lib/python2.7/dist-packages/wstools/tests/*.gz
-rw-r--r-- 1 root root 68874 2013-04-18 06:30:09.000000000 -0400 /usr/lib/python2.7/dist-packages/wstools/tests/schema.tar.gz
-rw-r--r-- 1 root root 15209 2013-04-18 06:30:09.000000000 -0400 /usr/lib/python2.7/dist-packages/wstools/tests/xmethods.tar.gz

```
this is on bionic 18.04 LTS but given file dates in 2013 they could be in other versions, very likely all from 13.04 and up.  anyone with 20.04 LTS and higher that try to decompress both of these?  i have these checksums:
```

lt2a/forums /home/forums 8> sha256sum -b /usr/lib/python2.7/dist-packages/wstools/tests/*.gz
fd0eef0fca6f718a9023b6520e458163f3bc94ff3abab49a93daf0b9441b9217 */usr/lib/python2.7/dist-packages/wstools/tests/schema.tar.gz
802bf0c107b131e1b50bee48da037b2f345984e9559ce8366688eba753e71cb0 */usr/lib/python2.7/dist-packages/wstools/tests/xmethods.tar.gz

```
```

lt2a/forums /home/forums 10> (gunzip|wc -c) </usr/lib/python2.7/dist-packages/wstools/tests/schema.tar.gz

gzip: stdin: invalid compressed data--format violated
884736
lt2a/forums /home/forums 11> (gunzip|wc -c) </usr/lib/python2.7/dist-packages/wstools/tests/xmethods.tar.gz

gzip: stdin: invalid compressed data--crc error

gzip: stdin: invalid compressed data--length error
161787
lt2a/forums /home/forums 12> 

```

---

### Post by norobro on 2021-07-11
Downloaded the source from here: [https://packages.ubuntu.com/bionic/python-wstools](https://packages.ubuntu.com/bionic/python-wstools)

Same results:```
user@Ubuntu:/tmp/wstools-0.4.3/src/wstools/tests$ sha256sum -b *.gz 
fd0eef0fca6f718a9023b6520e458163f3bc94ff3abab49a93daf0b9441b9217 *schema.tar.gz
802bf0c107b131e1b50bee48da037b2f345984e9559ce8366688eba753e71cb0 *xmethods.tar.gz


user@Ubuntu:/tmp/wstools-0.4.3/src/wstools/tests$ gunzip xmethods.tar.gz 


gzip: xmethods.tar.gz: invalid compressed data--crc error


gzip: xmethods.tar.gz: invalid compressed data--length error


user@Ubuntu:/tmp/wstools-0.4.3/src/wstools/tests$ gunzip schema.tar.gz 


gzip: schema.tar.gz: invalid compressed data--format violated


user@Ubuntu:/tmp/wstools-0.4.3/src/wstools/tests$ lsb_release -d
Description:    Ubuntu 21.04
```

---

### Post by Skaperen on 2021-07-11
i guess it is obsolete, now. it's only in *Python2*, which has been *EoL* for a while.  *Python3* doesn't have it or it's under another name.  i guess i can just purge that package (and most other things for *Python2*).

---

### Post by dragonfly41 on 2021-07-12
If you view the download site there is this ..

[h=3]Similar packages:[/h]
[LIST]
[*][libxml-compile-wsdl11-perl]("https://packages.ubuntu.com/libxml-compile-wsdl11-perl")
[*][python-pefile]("https://packages.ubuntu.com/python-pefile")
[*][python3-pefile]("https://packages.ubuntu.com/python3-pefile")
[*][python3-requirement-parser]("https://packages.ubuntu.com/python3-requirement-parser")
[*][python-nameparser]("https://packages.ubuntu.com/python-nameparser")
[*][python3-ua-parser]("https://packages.ubuntu.com/python3-ua-parser")
[*][python3-nameparser]("https://packages.ubuntu.com/python3-nameparser")
[*][libpod-wsdl-perl]("https://packages.ubuntu.com/libpod-wsdl-perl")
[*][python-dpkt]("https://packages.ubuntu.com/python-dpkt")
[*][python3-dpkt]("https://packages.ubuntu.com/python3-dpkt")
[*][python-pexif]("https://packages.ubuntu.com/python-pexif")
[/LIST]

---

### Post by Skaperen on 2021-07-12
the ones that begin with "python-" are for Python2.  everything should be using Python3 by now (10 years of dual-availability to make the transition).  while i'm not quite ready to deleted Python2, i may move it into a special testing container, and i don't need special packages for it, any more.  my next Ubuntu upgrade will be without it.

---

### Post by norobro on 2021-07-12
For whatever reason the wstools package is not being maintained any more for Ubuntu/Debian: [https://tracker.debian.org/pkg/python-wstools](https://tracker.debian.org/pkg/python-wstools)

If you need it a Python3 version is available through the Python package manager pip. [https://pypi.org/project/wstools-py3/](https://pypi.org/project/wstools-py3/)

---

### Post by Skaperen on 2021-07-13
don't need it.  if i did, i'd have gotten with pip a while back.  i have a bunch of other packages i get that way so i can have the latest versions ASAP. such *awscli* and *boto3*.  but, who knows, i might find a use for it in the future.

---

