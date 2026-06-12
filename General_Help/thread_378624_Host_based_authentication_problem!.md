---
title: "Host based authentication problem!"
date: 2007-03-07
forum: General Help
---

### Post by axrh on 2007-03-07
Hi,

I'm running into some problems with the client side of host based authentication.  I have my pub and priv keys and have added run ssh-add id_dsa.  However, when I use ssh it defaults back to the password prompt.  I turned verbosity on and saw this: it tried to use publickey authentication.  If "offered" my id_dsa file as the public key (shouldn't it offer id_dsa.pub?).  It then tried several private keys including identity and id_rsa and none of these were found (it did not try id_dsa).  The final message before popping up the password prompt was "wed did not send a packet, disable method".

Any ideas?

axrh

---

### Post by mitticus on 2008-02-13
Any answer to this? I have the same.

---

