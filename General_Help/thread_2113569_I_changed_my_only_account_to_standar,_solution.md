---
title: "I changed my only account to standar, solution?"
date: 2013-02-07
forum: General Help
---

### Post by rilesac on 2013-02-07
I changed my only account to standard. Now when I try to change it I can't because I'm not administrator, this have a solution for fix it or I need to back up all my important things and install Ubuntu again?

Thanks! :D

---

### Post by steeldriver on 2013-02-07
You should be able to fix it from the recovery console:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by rilesac on 2013-02-07
I don't understand how to do one of this:

[LIST]
[*]the /etc/sudoers file has been altered to no longer allow users in the *admin* group to escalate privilege
[*]the permissions on the /etc/sudoers file are changed to something other than 0440
[*]a user who should not have been has been taken out of the *admin* group
[/LIST]
I already opened sudoers file, then what should I change? The following code is the content of sudoers file.


[HTML]#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d[/HTML]

Thanks cause the answer! :D

---

### Post by steeldriver on 2013-02-07
If the ONLY thing you did was change your account to 'Standard', then the ONLY thing you need to do is add the account back to the 'sudo' group (the 'adduser *username* sudo' part of the instructions I linked) - there should be no need to edit the /etc/sudoers file

---

### Post by Cheesemill on 2013-02-07
You don't need to edit the sudoers file as that isn't where your problem is. You just need to add your user back to the sudo group instead. The command for this is...
```
gpasswd -a user sudo
```
replacing user with your actual username.

---

### Post by rilesac on 2013-02-07
Now this is solved!

I did the following command:

```
gpasswd -a user sudo
```

I'm really grateful for the answers!  steeldriver & Cheesemill

Greetings! and Thanks! (:

---

### Post by rilesac on 2013-02-07
Btw, Ubuntu is more "secure" if I use a standard account? Or is just the same?

Thanks again! :D

---

### Post by sudodus on 2013-02-07
> **rilesac said:**
> Btw, Ubuntu is more "secure" if I use a standard account? Or is just the same?

Thanks again! :D

I don't think it makes a big difference if you make your account a  standard one. But you should use sudo only when necessary. You saw how  easy it was to get back the sudo permission, when you know how to do it,  but it is inconvenient to do that every time you need to do something  to the system.

Have a look at this link
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

