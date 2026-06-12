---
title: "how to encrypt file with password and AES?"
date: 2007-03-15
forum: General Help
---

### Post by Martin01 on 2007-03-15
Hi,

I would like to encrzypt bzip2 file with passphrase. How could this be done?
I would prefer to use passphraze, not key pairs. Command line tool would be great.

BTW., how safe is it, when my passphraze  is something like "s8fd7fg67fdg6".

Thansk a lot.

---

### Post by Frosty Cold Drink on 2007-03-15
Try using [AES Crypt]("http://www.aescrypt.com/") for encryption.

I'm going to ignore the sample password you've given since you just mashed
on your keyboard. However, 13 characters from the set [a-z0-9] would yeild 170,581,728,179,578,208,256 possible combinations. Brute force would take quite a while...

---

### Post by Martin01 on 2007-03-15
Thank you. AES Crypt seems to be exactly what I need, but...

isn't it insecure to use software which isn't opensourced? Is there some other tool like GPG, which can do the same? Maybe even GPG itself, but I don't know how to use it without keys, with passhraze only:(

---

### Post by Frosty Cold Drink on 2007-03-15
> **Martin01 said:**
> Thank you. AES Crypt seems to be exactly what I need, but...

isn't it insecure to use software which isn't opensourced? Is there some other tool like GPG, which can do the same? Maybe even GPG itself, but I don't know how to use it without keys, with passhraze only:(

There is nothing about proprietary software that makes it inherently insecure. Predisposition is a different, and complicated discussion (read: flamewar).

Source for AES Crypt is available.

---

### Post by viktro on 2007-04-26
I had a quick look in Synaptic and found **aespipe** (in the Universe repository on Edgy), maybe the free tool that we need.

[INDENT]**AES-encryption tool with loop-AES support**
aespipe is an encryption tool that reads from standard input and
writes to standard output. It uses the AES (Rijndael) cipher.

It can be used as an encryption filter, to create and restore
encrypted tar/cpio backup archives and to read/write and convert
loop-AES compatible encrypted images.

aespipe can be used for non-destructive in-place encryption
of existing disk partitions for use with the loop-AES encrypted
loopback kernel module.[/INDENT]

---

