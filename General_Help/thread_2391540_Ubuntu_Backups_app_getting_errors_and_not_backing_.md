---
title: "Ubuntu Backups app getting errors and not backing up"
date: 2018-05-10
forum: General Help
---

### Post by mike370 on 2018-05-10
I am running Ubuntu 17.10 and been using the Backups app to maintain a backup of my home folder on an external drive. 
Last week I started getting an error when it tries to run a backup. I also get the error when I try to create a new backup. 
It also backs up too other home folders on the same machine. Is it possible those are causing this error?

This is the error I get, any advice would be most appreciated. 


```
GPGError: GPG Failed, see log below:

===== Begin GnuPG log =====

gpg: WARNING: "--no-use-agent" is an obsolete option - it has no effect
gpg: AES encrypted data
gpg: gcry_kdf_derive failed: Invalid data
gpg: encrypted with 1 passphrase
gpg: decryption failed: No secret key

===== End GnuPG log =====




```

---

### Post by Xian on 2018-05-10
When I was on openSUSE users had to install the python-oauth package to fix this issue.

$ sudo apt-get install python-oauth

---

