---
title: "After sshd update, some sshd_config entries are deprecated and I lost access..."
date: 2019-04-26
forum: General Help
---

### Post by trancephorm on 2019-04-26
EDIT: forget it..... I was connected to wrong WIFI :))

Noticed from syslog that these entries are deprecated:
UsePrivilegeSeparation
KeyRegenerationInterval
ServerKeyBits
RSAAuthentication
RhostsRSAAuthentication

Which seems that it affected my passwordless logins from another machine in the same network on which I use sshfs to locally map partition from the machine that runs sshd server in question. Don't ask me how I managed to setup that no password is needed, I remember there was some importing of security keys and allowing them specially, it was painful but it worked in the end.

After update today or yesterday, that does not work anymore. Can anyone help me? Thanks!

---

