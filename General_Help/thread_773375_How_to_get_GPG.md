---
title: "How to get GPG?"
date: 2008-04-28
forum: General Help
---

### Post by Jongi on 2008-04-28
when I run an apt-get update I get the following

```

W: GPG error: http://za.archive.ubuntu.com hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems
```

The relevant sources.list entry is

```

deb-src http://za.archive.ubuntu.com hardy universe
```

I also used

```

deb-src http://za.archive.ubuntu.com/ubuntu hardy universe
```
with the same result.

Am I missing something here?

---

### Post by bodhi.zazen on 2008-04-28
First run :

```
sudo apt-get update
```

If that fails let us know and we will walk you through manually updating the key.

FYI: You can still install, you will just get a warning.

---

### Post by Jongi on 2008-04-29
That a result of running apt-get update.

---

### Post by zvacet on 2008-04-29
Type in terminal 

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 40976EAF437D05B5
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -

---

### Post by wmtmanjula on 2008-06-10
Thanks. This one works for me.:)
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys
gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -[/B]

---

