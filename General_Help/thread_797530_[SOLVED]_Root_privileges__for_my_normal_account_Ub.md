---
title: "[SOLVED] Root privileges  for my normal account? Ubuntu 8.04"
date: 2008-05-17
forum: General Help
---

### Post by ThePHPguy on 2008-05-17
Hello, I just installed Xampp for Linux on Ubuntu 8.04 but I can't make new folders in the htdocs or save files. It gives me the error "You don't have permission ect..."

If there is a way to give my account permission to the folder

(/opt/lampp/ *) the star meaning all folders inside of lampp

I can log in as "root" if I need to.

---

### Post by aysiu on 2008-05-17
These two links should help you out:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by ThePHPguy on 2008-05-17
Thank you for the links it helps but now I can't save the file after I'm done editing.


I'm typing ("sudo visudo") and then it runs some code and ask me if I want to run some code or press enter.

When I press enter it shows me this.
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


```

I'm wanting to change it to the following
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
my username ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


```

I can change it but I can't save it.

Thanks in advance

---

### Post by Monicker on 2008-05-17
I do not understand why you are editing /etc/sudoers in this case.  Your account should already be in the admin group, and thus already able to use to sudo command to perform actions as root.

Type this at the console:

```
groups
```

Is admin listed in the output?


To change permissions on files or directories, just prefix the command with sudo, and then enter your password when prompted.
```

sudo chown username /some/dir
sudo chmod -R 644 /some/dir
```


Read the links given previously very carefully before changing permissions on system directories and files.

---

### Post by ibuclaw on 2008-05-17
Ah! Vim has struck again! (hehe)

Type in these commands:
```

export EDITOR=nano
sudo -E visudo

```
That will help solve your problem handling the confusing nature of the Vim text editor.

Make your alteration, then hit "Ctrl+X" to quit. Then press "Y" to save the changes.

Visudo will check that everything is in order (if there is an error, it will tell you and refuse to save the file).

Regards
Iain

---

### Post by ThePHPguy on 2008-05-17
Thank You Both so much. I now have it working.

---

