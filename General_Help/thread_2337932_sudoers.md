---
title: "sudoers"
date: 2016-09-22
forum: General Help
---

### Post by kurogane2 on 2016-09-22
Hello,

I've a problem with [COLOR=#333333][FONT=Menlo]sudoers and no password

Here what i have:

# [/FONT][/COLOR]/etc/sudoers

```

#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        mail_badpass
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"


# Host alias specification


# User alias specification


# Cmnd alias specification


# User privilege specification
root    ALL=(ALL:ALL) ALL


# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL


# See sudoers(5) for more information on "#include" directives:


#includedir /etc/sudoers.d

```

# visudo -f /etc/sudoers.d/nginx[COLOR=#333333][FONT=Menlo]

[/FONT][/COLOR]```
# Nginx Commands
Cmnd_Alias NGINX_RESTART = /usr/sbin/service nginx restart
Cmnd_Alias NGINX_RELOAD  = /usr/sbin/service nginx reload


# No-Password Commands
user1 ALL=NOPASSWD: NGINX_RESTART, NGINX_RELOAD
[COLOR=#333333][FONT=Menlo]
[/FONT][/COLOR]
```
[COLOR=#333333][FONT=Menlo]
[/FONT][/COLOR]When i run this[COLOR=#333333][FONT=Menlo]

[/FONT][/COLOR]```
$ sudo /usr/sbin/service nginx reload
[sudo] password for user1:

```

Why asking a password? how i can solve it?

---

### Post by yetimon_64 on 2016-09-23
```
# Nginx Commands 
Cmnd_Alias NGINX_RESTART = /usr/sbin/service nginx restart
Cmnd_Alias NGINX_RELOAD  = /usr/sbin/service nginx reload


# No-Password Commands
user1 ALL=**(ALL) **NOPASSWD: NGINX_RESTART, NGINX_RELOAD
```

Try by adding what I have above in bold "(ALL) ". I suspect your problem is only a simple syntax error in the last line.
I am basing that off the syntax I am using here in a similar file (that works perfectly) in /etc/sudoers.d/; although I am not using the command aliases, just straight commands in the file. 

For example ...
```
# No-Password Commands
yetiman ALL=(ALL) NOPASSWD: /usr/bin/fbcat
yetiman ALL=(ALL) NOPASSWD: /sbin/shutdown
```

Note how I don't use the command aliases, just the commands with a new complete entry on each line. Which is slightly different to how you are setting out your file.

Regards, yeti.

---

