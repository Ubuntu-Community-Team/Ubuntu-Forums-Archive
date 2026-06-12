---
title: "Enabling root login and removing user from sudoers"
date: 2013-05-28
forum: General Help
---

### Post by shaaraddalvi on 2013-05-28
Hello everyone,
  I am having a single user account 'shaarad' and root account. Frankly, I do not understand the meaning of 'enabling' the root login, but once I went to sudo mode from user 'shaarad' and the typed #passwd and changed root password. So now i can type $su and then root password to get # mode. Now, I want to remove sudo permissions from 'shaarad' account. I want to operate all the things that need sudo by logging in to console as root user. 
Here is my sudoers file as shown by visudo : 




```

#
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


#includedir /etc/sudoers.d

```



And the output of command $groups shaarad is : 
```
 shaarad : shaarad adm cdrom sudo dip plugdev lpadmin sambashare 
```

so please tell me how to remove user 'shaarad' from sudoers as no group of 'shaarad' is there in sudoers file...

Thanks a lot... :)

---

### Post by Cheesemill on 2013-05-28
> **shaaraddalvi said:**
> so please tell me how to remove user 'shaarad' from sudoers as no group of 'shaarad' is there in sudoers file...

Your shaarad user is a member of the sudo group, which ***does*** have a declaration in the sudoers file.....
```
shaarad : shaarad adm cdrom [COLOR=#ff0000]sudo[/COLOR] dip plugdev lpadmin sambashare
```
```
#
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


[COLOR=#ff0000]# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL[/COLOR]


# See sudoers(5) for more information on "#include" directives:


#includedir /etc/sudoers.d
```

The easiest way to disable sudo privileges for your user is to remove it from the sudo group...
```
sudo deluser shaarad sudo
```

---

### Post by shaaraddalvi on 2013-05-28
Thanks a lot...worked.. :)

---

