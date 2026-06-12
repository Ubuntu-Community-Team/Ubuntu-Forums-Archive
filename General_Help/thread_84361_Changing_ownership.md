---
title: "Changing ownership"
date: 2005-10-30
forum: General Help
---

### Post by phil66 on 2005-10-30
How do I change ownership of "/etc/sudoers" from user to root and group to root

Thanks
Ray

---

### Post by Xian on 2005-10-31
Use this command:

```
# sudo chown root:root /etc/sudoers
```

If it gives you a message about a wrong gid number then you'll 
have to boot into recovery mode and issue the command
from that shell.

---

### Post by phil66 on 2005-10-31
Hi xian

Using sudo -v root:root /etc/sudoers

Returns the message

sudo:/etc/sudoers is owned by uid 1000,should be 0

Reboot to recovery mode when I get to enter root password or Control-D
Neither one will let me enter 
Message above "Temporary failure in name resolution"

Try to enter kuser and get message
"error"kde su returned with an error"

chmod or chrgp returns same error as chown

Any farther suggestions will be appreciated
Ray

---

### Post by Xian on 2005-10-31
[QUOTE=phil66]Reboot to recovery mode when I get to enter root password or Control-D[/quote]

You should only get that message if you set a root password.
Are you sure you didn't to this?

If you did then you can su from a terminal and issue the 
chown command again to reset the permissions.

Otherwise, you'll have to use a LiveCD or similar to do the same.

---

### Post by phil66 on 2005-11-01
Thanks for the reply

No root password set

Live cd of ubuntu did not solve problem

Did clean uninstall and reinstalled

All systems okay now.

Thanks for the advice
Ray

---

