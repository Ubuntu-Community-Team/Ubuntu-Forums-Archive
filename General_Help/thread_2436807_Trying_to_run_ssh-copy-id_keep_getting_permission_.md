---
title: "Trying to run ssh-copy-id keep getting permission denied"
date: 2020-02-13
forum: General Help
---

### Post by mlouly on 2020-02-13
hi all,

i hope i can get some help with this one.  i am basically trying to copy ssh key from one server tor.  o another ubuntu 18.04 and keep getting this error

ssh-copy-id root@192.168.1.142
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/root/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
root@192.168.1.142's password:
Permission denied, please try again.
root@192.168.1.142's password:

Thank you in advance all!!

---

### Post by TheFu on 2020-02-13
Don't use root. 

Ubuntu doesn't enable the root account.  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mlouly on 2020-02-13
Thank you!  That resolved it all for me, TheFu!

---

