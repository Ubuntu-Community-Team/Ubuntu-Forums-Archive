---
title: "SSSD with and without network"
date: 2023-03-22
forum: General Help
---

### Post by R. M. Frank on 2023-03-22
I have set up an Ubuntu 22.04LTS laptop and all is looking good.
I'm using sssd to verify the password of registered users (users are listed in /etc/passwd). 
The sssd config is solid and all communications are working as expected, if and only if the laptop is connected to the network (via wired network).
The config options 
  cache_credentials = True
  krb5_store_password_if_offline = True
are explicitly set.
Kerberos tickets are properly obtained.

If I unplug the network, then lock or sleep the laptop, I can (wake and) login again using the password.
If I sleep or lock the laptop, then unplug the network I can't login again. If I wait long enough (at least 20mins), I can again login.

The ssd logs contain many backtraces, most of which are successful.
However, when the authentication fails, I get an entry which claims that the user is not found in the negative cache, as well as nss messages of the kind
Could not get account info [110]: Connection timed out
which make sense, as the network is unplugged.

I'm quite stumped on this matter.
Has anyone had something similar who could point me in the right direction of debugging this situation?

Many thanks in advance
Robert

---

### Post by MAFoElffen on 2023-03-22
Hmmm. Coincidentally seems to be the same as this Bug : [https://bugs.launchpad.net/ubuntu/+source/sssd/+bug/1928954](https://bugs.launchpad.net/ubuntu/+source/sssd/+bug/1928954)

---

