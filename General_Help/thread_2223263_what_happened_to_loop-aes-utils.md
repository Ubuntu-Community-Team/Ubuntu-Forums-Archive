---
title: "what happened to loop-aes-utils ?"
date: 2014-05-10
forum: General Help
---

### Post by rchr on 2014-05-10
hi guys,

I just upgraded 12.04 to 14.04 and during upgrade it removed f.e. "loop-aes-utils" package
and now this package is not even available in default repositories (!)

what happened with that tool ? will it be in repo again ?

I managed to download .deb somehere from web and it works but I really would like official support for this tool
I need it for mounting encrypted discs, it's pretty usefull stuff

best regards

---

### Post by Frogs Hair on 2014-05-10
I find a package named aes-pipe , but don't know if it is related.  

> aespipe is an encryption tool that reads from standard input and
writes to standard output. It uses the AES (Rijndael) cipher.

aespipe can be used for non-destructive in-place encryption
of existing disk partitions for use with the loop-AES encrypted
loopback kernel module.

It can also be used as an encryption filter to create and restore
encrypted tar/cpio backup archives and to read/write and convert
loop-AES compatible encrypted images.

Note that aespipe does not store any length information with the
encrypted images, so it cannot be used as general purpose filter
for encryption, but only for certain formats like tar.

---

### Post by rchr on 2014-05-10
aespipe is used to prepare encrypted iso, example:
```
mkisofs -t udf "folder" | aespipe -P "password.gpg" -e aes256 > "image.iso"
```

loop-aes-utils is used to mount iso already encrypted with aespipe:
```
mount -t udf -o loop,encryption=aes256 "image.iso" /media/iso
```

without this package it won't mount and throw an error like:
```
ioctl: LOOP_SET_STATUS: No such file or directory
```

---

