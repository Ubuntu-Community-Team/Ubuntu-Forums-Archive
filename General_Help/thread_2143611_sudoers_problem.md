---
title: "sudoers problem"
date: 2013-05-09
forum: General Help
---

### Post by madnbri on 2013-05-09
Hi,
I've reinstalled all after upgrade to 13.04 failed and of course lost my all setups :(
It doesn't matter, I thought, but lost my own sudoers also and there is no usable help to solve this:
[http://paste.ubuntu.com/5648463/](http://paste.ubuntu.com/5648463/)
I want to:
[LIST]
[*]define User_Alias (which user can do: SHUTDOWN_USRS) 
[*]define Cmnd_Alias (SHUTDOWN_CMNDS) 
[*]enable to SHUTDOWN_USERS to SHUTDOWN_CMNDS with NOPASSWD option 
[/LIST]
Looks very simple, but doesn't work.
Thanks in advance,
m

---

### Post by dino99 on 2013-05-09
have you not set a separate /home partition to get your data/settings safe ?
[http://www.garron.me/en/linux/visudo-command-sudoers-file-sudo-default-editor.html](http://www.garron.me/en/linux/visudo-command-sudoers-file-sudo-default-editor.html)

---

### Post by madnbri on 2013-05-09
> **dino99 said:**
> have you not set a separate /home partition to get your data/settings safe ?
[http://www.garron.me/en/linux/visudo-command-sudoers-file-sudo-default-editor.html](http://www.garron.me/en/linux/visudo-command-sudoers-file-sudo-default-editor.html)

No. I've partioned everything again, and didn't made a failsafe, forgot sudoers :(

---

### Post by Cheesemill on 2013-05-09
You need to put your SHUTDOWN_USRS line at the bottom of your sudoers file.

---

### Post by madnbri on 2013-05-09
> **Cheesemill said:**
> You need to put your SHUTDOWN_USRS line at the bottom of your sudoers file.

I don't understand you. Can you post it?

---

### Post by matt_symes on 2013-05-09
Hi

As cheesemill said, add it to the bottom of your sudoers file.

```
matthew-S206:/home/matthew/thunar_dbus % sudo tail -n 10 /etc/sudoers
# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

# For diagnostics
**matthew ALL=(ALL) NOPASSWD: /usr/sbin/iotop, /usr/sbin/iftop, /usr/sbin/powertop**

matthew-S206:/home/matthew/thunar_dbus % 
```

There's a snippet of my sudoers file. I added what i needed to the bottom of the file.

Kind regards

---

### Post by Cheesemill on 2013-05-09
You just need to move the line to the bottom of the file so that it looks like this...
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
Defaults    mail_badpass
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification
User_Alias    SHUTDOWN_USRS        =    z

# Cmnd alias specification
Cmnd_Alias    SHUTDOWN_CMNDS    =    /sbin/shutdown,/sbin/halt,/sbin/reboot,/sbin/poweroff

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

SHUTDOWN_USRS    ALL=(ALL) NOPASSWD:    SHUTDOWN_CMNDS
```

---

### Post by madnbri on 2013-05-09
> **Cheesemill said:**
> You just need to move the line to the bottom of the file so that it looks like this...
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
Defaults    mail_badpass
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification
User_Alias    SHUTDOWN_USRS        =    z

# Cmnd alias specification
Cmnd_Alias    SHUTDOWN_CMNDS    =    /sbin/shutdown,/sbin/halt,/sbin/reboot,/sbin/poweroff

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d

SHUTDOWN_USRS    ALL=(ALL) NOPASSWD:    SHUTDOWN_CMNDS
```

OK. This is right.

---

