---
title: "Zero Install Problem"
date: 2008-02-12
forum: General Help
---

### Post by Mark76 on 2008-02-12
Every time I try to use the zeroinstall injector I keep getting this

Error fetching 'AE07828059A53CC1.gpg':

No valid signatures found. Signatures:
- ERROR signature by AE07828059A53CC1: Unknown key. Try 'gpg --recv-key AE07828059A53CC1'

It's really annoying me, because I can't find any solution.. :mad:

---

### Post by Mark76 on 2008-02-12
I tried adding the extra gutsy repos. installing it again and got this

E: zeroinstall-injector: subprocess post-installation script returned error exit status 1

---

### Post by zvacet on 2008-02-12
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -

In terminal

gpg --keyserver hkp://subkeys.pgp.net --recv-keys AE07828059A53CC1
 gpg --export --armor  AE07828059A53CC1  | sudo apt-key add -

---

### Post by Mark76 on 2008-02-12
Got this running the first command

> gpg --keyserver hkp://subkeys.pgp.net --recv-keys AE07828059A53CC1
gpg: requesting key 59A53CC1 from hkp server subkeys.pgp.net
gpg: can't open `/home/mark/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0


---

