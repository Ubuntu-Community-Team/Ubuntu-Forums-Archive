---
title: "[SOLVED] Cannot complete winbind setup (`getent passwd` does not returns doamin accou"
date: 2007-11-14
forum: General Help
---

### Post by Yakov Hrebtov on 2007-11-14
I've set up winbind so it successfuly lists my domain users and groups with

wbinfo -u
wbinfo -g

But `getent passwd` and `getent group` returns only local posix accounts.

my /etc/nsswitch.conf contains:

passwd:         compat winbind
group:          compat winbind
shadow:         compat

What I must do to complete winbind integration?
(I'm using ubuntu-7.10-server edition)

Thanks is advance.

---

### Post by Yakov Hrebtov on 2007-11-15
Shame to me...
I just forgot to uncomment:

   idmap uid = 10000-20000
   idmap gid = 10000-20000
   winbind enum groups = yes
   winbind enum users = yes

in smb.conf :oops:

---

