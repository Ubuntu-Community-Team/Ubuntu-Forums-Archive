---
title: "NOPASSWD option is not working via VISUDO"
date: 2013-09-06
forum: General Help
---

### Post by kschiff on 2013-09-06
I'm trying to execute the TeamViewer daemon via Startup Applications and have attempted to make the folder where the script resides work without a SUDO password... I used Visudo to access the sudoers file... I noticed when I open Visudo it defaults to /etc/sudoers.tmp when I WriteOut I wrote to /etc/sudoers

I clearly must be doing something wrong here. Here are the contents of my sudoers file. I only modified the last line.

```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset,pwfeedback
Defaults        mail_badpass
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:$


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
muser ALL=(muser:muser) NOPASSWD: /opt/teamviewer8/tv_bin/script

```

---

### Post by bluefrog on 2013-09-07
your config may be different than mine, if not, just add /usr/bin/teamviewer to the startup applications command and it will be launched when you log in.

and if not mistaken, you need to point to a file in the sudoers not to a directory

---

### Post by kschiff on 2013-09-08
Two issues for me... one is that it my config one appears to need sudo to launch the teamviewer daemon and regardless of what I've done, this won't launch at startup without sudo. Also, i don't want to launch TV, but rather just the daemon as I used this for meetings and remote session with others (no one connects to my machine directly). I've sent me logs over to TV to see if they can shed some light on the subject.

---

