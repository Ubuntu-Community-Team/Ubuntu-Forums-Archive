---
title: "launchpad-getkeys: a problem and a workaround"
date: 2012-10-18
forum: General Help
---

### Post by pwabrahams on 2012-10-18
When I try to run **launchpad-getkeys**, I get HTTP Error 7:
```
gpg: requesting key BB901940 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

``` 
But this does work:```
root@Lenovo-Z580:/etc/apt# launchpad-getkeys -k 91.189.89.49:80

Please wait... launchpad-getkeys is running an update so 
it can detect the missing GPG keys

Trying to import all the missing keys
gpg: requesting key BB901940 from hkp server 91.189.89.49
gpg: key BB901940: public key "Launchpad Daily Build" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

```
Here **91.189.89.49** is the IP address of **keyserver.ubuntu.com**.

Of course, this shouldn't be necessary.  The problem seems to lie in how **launchpad-ketkeys** resolves the URL of its keyserver.  BUG!!!

---

