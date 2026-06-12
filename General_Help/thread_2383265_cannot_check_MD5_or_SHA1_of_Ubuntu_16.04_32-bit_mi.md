---
title: "cannot check MD5 or SHA1 of Ubuntu 16.04 32-bit mini.iso"
date: 2018-01-22
forum: General Help
---

### Post by ardouronerous on 2018-01-22
I downloaded the mini.iso from here: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

This is the results of MD5 and SHA1 checksums:
```
md5sum -c mini.iso
md5sum: mini.iso: no properly formatted MD5 checksum lines found
sha1sum -c mini.iso
sha1sum: mini.iso: no properly formatted SHA1 checksum lines found
```

---

### Post by papibe on 2018-01-22
Hi ardouronerous.

Don't use the -c option. Just like this:
```
md5sum  mini.iso
```
or
```
sha1sum mini.iso
```
And then compare the results with the ones the link.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by ardouronerous on 2018-01-22
Okay that worked thanks :)

what does the -c option suppose to do? I read some instructions on checking MD5/SHA1 with these options.

---

### Post by papibe on 2018-01-22
Good to know :)

You can save the sums in a file, and make the file available, so people can check the sums offline.

For example:
```
$ md5sum crontab.txt 
9f8759418bf7943615b27b19f20f9415  crontab.txt

$ md5sum crontab.txt > files.md5
```
then on the other end, when both files are downloaded:
```
$ ls crontab.txt files.md5 
crontab.txt  files.md5

$ md5sum -c files.md5 
crontab.txt: OK

```
the -c option is going through files.md5, making the sum of the file listed there, and checking that fresh value with the one is on the file. 

Hope it helps.
Regards.

---

### Post by ardouronerous on 2018-01-23
Thanks for explaining :)

---

