---
title: "Installing procmail also installs postfix.  I don't want postfix"
date: 2022-07-26
forum: General Help
---

### Post by hpu3 on 2022-07-26
Running 22.04

 I wanted to install procmail.  I've used it for years.  But, when I try to install with apt it also wants to install postfix:

"sudo apt install procmail
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  postfix
Suggested packages:
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre postfix-lmdb postfix-sqlite
  sasl2-bin | dovecot-common resolvconf postfix-cdb postfix-mta-sts-resolver
  postfix-doc
The following NEW packages will be installed:
  postfix procmail
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,395 kB of archives.
After this operation, 4,507 kB of additional disk space will be used.
Do you want to continue? [Y/n] "

I really do not want to install postfix.  Why is it necessary to install postfix?  Procmail has always been a standalone 
application  and works with all the main mail clients. 

"aptitude show procmail" does not show any requirements other than "Depends: libc6 (>= 2.34)"
and recommends: "default-mta | mail-transport-agent | fetchmail"

No mention of postfix at all.

How can I install procmail without postfix?

---

### Post by deadflowr on 2022-07-26
default-mta is a virtual package which is provided by postfix, but anyway run the apt install command with the --no-install-recommends option like
```
sudo apt install --no-install-recommends procmail
```
Ubuntu sets apt to basically consider recommended packages as dependencies unless marked with the above command to not do so.

---

