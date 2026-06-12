---
title: "webmin"
date: 2005-05-05
forum: General Help
---

### Post by danip on 2005-05-05
I cannot log into webmin with either my username or the root username.  I have tried setting a password for root, sudo passwd still cant log in.  I also tried the following 

```
/usr/share/webmin/changepass.pl /etc/webmin root newpassword
```

It says that is an unknown command.  Any help on how to log in?

---

### Post by nad on 2005-05-05
Are any users listed in /etc/miniserv.users?

Try: sudo chmod u+x /usr/share/webmin/changepass.pl  and try the script again.

---

### Post by danip on 2005-05-05
no users are listed in there.  I tried the chmod still get the same error.

---

### Post by nad on 2005-05-05
This may be a bug in the package. By default webmin will install with a root user account and its' password. As ubuntu has no root account password by default, no account was set up. You can not use webmin.

Remove the package. sudo passwd root  to create a root password and reinstall the package.

If everything goes okay now, report the bug. You've got all the particulars.

---

### Post by danip on 2005-05-05
Hah i just tried that myself and it worked.  Thanks for your help.

---

### Post by naso on 2005-05-06
it does not seem to work with me  :-? 

are there any better options to remote control ubuntu?

i tried with VNC but i'm completely new and maybe iptables is blocking me out

---

### Post by nad on 2005-05-06
Telnet, ftp, ssh.

---

