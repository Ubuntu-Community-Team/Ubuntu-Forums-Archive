---
title: "service lightdm start without password"
date: 2015-04-17
forum: General Help
---

### Post by chris352 on 2015-04-17
I'm trying to edit my sudoers file so that I can use the 'service lightdm start' command from the terminal to bring up the Unity interface without having to enter my password. Unfortunately, I'm not having any success. Here's what my edited /etc/sudoers file looks like:

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

# Cmnd alias specification
Cmnd_Alias LIGHTDM_CMDS = /usr/sbin/lightdm
# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%admin ALL= NOPASSWD: LIGHTDM_CMDS
# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
```

Can anyone tell me what I've got wrong?

---

### Post by papibe on 2015-04-17
Hi chris352.

No password for the sudo command on the terminal, or no password at lightdm login?

In case is for the command line, when you do:
```
sudo service lightdm start
```
The 'lightdm' reference there is not '/usr/sbin/lightdm', but the init script located at /etc/init.d:
```
/etc/init.d/lightdm
```
Does that help? Let us know how that goes.
Regards.

---

### Post by chris352 on 2015-04-17
> **papibe said:**
> Hi chris352.

No password for the sudo command on the terminal, or no password at lightdm login?

From the terminal. I want to boot into the terminal and only crank up Unity when I need it.

> In case is for the command line, when you do:
```
sudo service lightdm start
```
The 'lightdm' reference there is not '/usr/sbin/lightdm', but the init script located at /etc/init.d:
```
/etc/init.d/lightdm
```
Does that help? Let us know how that goes.
Regards.

Alas, no. I edited the file to include '/etc/init.d/lightdm', but when I enter 'sudo service lightdm start' it still requires a password. If I don't use 'sudo', it tells me that only root is permitted to start lightdm.

---

### Post by steeldriver on 2015-04-17
IIRC you need to be absolutely specific about the command you intend to run (including arguments); for example, this appears to work for me:

```

%sudo   ALL=(ALL) NOPASSWD: /usr/sbin/service lightdm start

```

Note I am using the sudo group as the (legacy) admin group is not created by default on 14.04

Note also that you need the full path to the service executable even though it's on the sudoers secure_path (you will get a syntax error otherwise, and visudo will refuse to write the file)

---

### Post by chris352 on 2015-04-17
That did the trick, thanks!

---

