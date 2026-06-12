---
title: "GPG gpg --gen-key fails"
date: 2006-10-12
forum: General Help
---

### Post by joff13 on 2006-10-12
Hi,

I'm trying to generate a gpg key with
```
gpg --gen-key
```
but i receive a message like (transtation):

writable public keyring not found : eof

what i'm supposed to do?

tnx

[EDIT]

Was enough to do 

```
$ rm -rf  ~/.gnupg
$ mkdir ~/.gnupg
$ chmod 700 ~/.gnupg
$ gpg --gen-key
```

---

### Post by moore.bryan on 2006-10-12
*isn't it ```
gpg --genkey
```*

---

