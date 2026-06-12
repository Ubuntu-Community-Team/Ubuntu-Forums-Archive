---
title: "What do you do check SSH server user Password in Ubuntu Server 12.04LTS ??"
date: 2013-12-23
forum: General Help
---

### Post by agerpark on 2013-12-23
sudo ssh  server@IP_Addr
server@IP_Addr's Password : written root password

Can not log-in SSH...Can you know password and check password..?
i'm not see ssh password setting during Ubuntu Server 12.04LTS 64bit installing..
i was only check root password.

---

### Post by bashiergui on 2013-12-23
If you didn't set up a password when you installed ssh then try logging in and leavig the password blank.

---

### Post by steeldriver on 2013-12-23
There is no "ssh password" - if you are using password authentication in ssh, then the password is the regular password for the user account which you're connecting as i.e. if you connect as server@ipaddr then you need the password for the user account named 'server'

---

### Post by devine.steve on 2013-12-23
In Ubuntu root is not normally allowed to login via ssh. Generally you login with a unprivileged user and then use the sudo command to run the dangerous commands. :)

---

