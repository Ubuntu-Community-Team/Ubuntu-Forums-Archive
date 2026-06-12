---
title: "Unsecure ownership of .gnupg/gpg.conf"
date: 2007-11-22
forum: General Help
---

### Post by knutschr on 2007-11-22
I try installing key from Opera.
```
sudo gpg --keyserver subkeys.pgp.net --recv-key 6A423791
```
I then is told that the ownership of the file is unsecure, so external program calls therefore are disabled.
This happens both when owner is set to me and to root.

What do I do wrong?

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-22
I think the permission for ".gnupg/gpg.conf" file is "world readable", which means the bit "others" have read permission, is it?

If so you can use chmod to remove the permission of "others" to none:
```

chmod o-rw ~/.gnupg/gpg.conf

```

---

### Post by knutschr on 2007-11-22
I changed ownership like you said, but error is still the same.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-22
Can you see the permission of "~/.gnupg" directory?
Or post the output of this command:
```

ls -al ~/.gnupg

```

---

### Post by knutschr on 2007-11-22
I get:
> knut@Knut:~$ ls -al ~/.gnupg
totalt 40
drwx------  3 knut knut 4096 2007-11-07 15:54 .
drwxr-xr-x 89 knut knut 4096 2007-11-22 21:54 ..
-rw-r--r--  1 knut knut   74 2007-11-21 16:09 gpg-agent-info-Knut
-rw-------  1 knut knut 9417 2007-11-06 23:46 gpg.conf
drwx------  2 knut knut 4096 2007-11-07 15:54 private-keys-v1.d
-rw-------  1 knut knut 1607 2007-11-06 23:46 pubring.gpg
-rw-------  1 knut knut 1607 2007-11-06 23:46 pubring.gpg~
-rw-------  1 knut knut    0 2007-11-06 23:46 secring.gpg
-rw-------  1 knut knut 1200 2007-11-06 23:46 trustdb.gpg

private-keys-v1.d
is colored blue.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-22
knutschr, try executing with --no-permission-warning
```

sudo gpg **--no-permission-warning** --keyserver subkeys.pgp.net --recv-key 6A423791

```

---

### Post by knutschr on 2007-11-22
I came further, yes!
But I was answered, after a while, that server subkeys.pgp.net did not answer in time :-(

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-22
Could it because the connection is down?
I tried from my machine, get this output:
```

> sudo gpg --no-permission-warning --keyserver subkeys.pgp.net --recv-key 6A423791
gpg: requesting key 6A423791 from hkp server subkeys.pgp.net
gpg: key 6A423791: "Opera Software Archive Automatic Signing Key <hostmaster@opera.com>" imported
gpg: Total number processed: 1
gpg:              unchanged: 1

```
which I assumed the keys is retrieved. 
Maybe you should try a few moment later?

I'm sorry if I misunderstood you, I'm still learning English :) .

---

### Post by knutschr on 2007-11-22
I have  never achieved connection to that server.
I also now watch national TV by [www.zattoo.com](www.zattoo.com), so my connection works.

(Btw:Your English is excellent)

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-22
AFAIK, you can install software from "untrusted" (un-imported) apt-source's GPG key.
But you must answer "yes" when apt-get ask for your confirmation.

If you want to install opera, I think you can do that without importing gpg key, as long as you've added opera's repository to your /etc/apt/sources.list file.

Thank you for your compliment, sometimes I just get a hard time understanding English.

---

