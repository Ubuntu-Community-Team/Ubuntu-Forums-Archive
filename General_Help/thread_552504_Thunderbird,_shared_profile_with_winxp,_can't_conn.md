---
title: "Thunderbird, shared profile with winxp, can't connect to ldap"
date: 2007-09-16
forum: General Help
---

### Post by admash on 2007-09-16
I am successfully using the same profile for Thunderbird 2/enigmail/gnupg in Ubuntu 7.04 and WinXP, except for one error:

Downloading of keys failed
gpg: refreshing 5 keys from ldap://keys.hush.com:389
gpg: requesting key DD91B73E from ldap server keys.hush.com
gpgkeys: unable to retrieve LDAP base: Can't contact LDAP server
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
gpg: keyserver internal error
gpg: keyserver refresh failed: keyserver error

For existing keys, the encryption/decryption works fine. But the above error happens on Ubuntu when I try and retrieve a new key.

I shouldn't need to set up an ldap server for this right? Or what am I missing?

---

