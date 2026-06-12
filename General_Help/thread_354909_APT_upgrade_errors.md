---
title: "APT: upgrade errors"
date: 2007-02-06
forum: General Help
---

### Post by limaunion on 2007-02-06
Hi! Since I upgraded my system to Ubuntu Edgy I've been getting these errors every time I issue 'apt-get upgrade':

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  hpijs python-adns python-clientcookie python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-htmlgen python-jabber python-ldap
  python-mysqldb python-pam python-pexpect python-pylibacl python-pyopenssl python-pyxattr python-reportlab python-simpletal python-sqlite python-xmpp

Any idea on how to solve this ?
Thanks in advance.
JC

---

### Post by LotsOfPhil on 2007-02-06
I had the same problem with this and with cups. I fixed it by uninstalling those packages and then reinstalling python.

It isn't perfect and I have no explanation, so do this at your own discretion.

---

