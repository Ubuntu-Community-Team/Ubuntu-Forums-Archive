---
title: "Restricting logins"
date: 2007-04-18
forum: General Help
---

### Post by navilon on 2007-04-18
I need to have a few accounts only accessible from 5pm to 9pm

is this possible?

---

### Post by leibowitz on 2007-04-18
Sure. You have to check pam authentification modules, called pam_time. [1] 

The configuration file is located at /etc/security/time.conf

First you need to add or uncomment a line in this file. In your case it will be something like this:
services;*;user1|user2|user3;Al1700-2100
See the time.conf file for more details/examples.

Next you will need to activate the pam_time module in the /etc/pam.d/* configuration files[2]. Here I'm not totaly sure about what file to edit, and what to put in it. I would recommend a test machine for that, because if you do something wrong, you can easily exclude yourself from future logins...

A tip: connect an administrator account onto the machine, backup the configuration files _before_ editing anything, then edit the files. To test the configuration, keep the administrator logged in, and login a new user to see if it's working. Try to login with other account aswell. When everything is ok, you can logout from your administrator account.

[1] [http://www.die.net/doc/linux/man/man8/pam_time.8.html](http://www.die.net/doc/linux/man/man8/pam_time.8.html)
[2] [http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-configuration-file.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-configuration-file.html)
[3] [http://www.linuxdevcenter.com/pub/a/linux/2001/09/27/pamintro.html?page=2](http://www.linuxdevcenter.com/pub/a/linux/2001/09/27/pamintro.html?page=2)

---

