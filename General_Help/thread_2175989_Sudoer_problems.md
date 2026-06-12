---
title: "Sudoer problems:"
date: 2013-09-22
forum: General Help
---

### Post by CkDGTAT on 2013-09-22
Hi,

From home everything works fine:

```
~$ echo "" > file 
```

but

```
~$ mkdir folder; cd folder
~/folder$ echo "" > file
bash: file: Permission denied

```

My sudoer

```
## This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"


# Host alias specification


# User alias specification


# Cmnd alias specification


# User privilege specification
root	ALL=(ALL:ALL) ALL
jean ALL = (ALL:ALL) ALL 
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL


# See sudoers(5) for more information on "#include" directives:


#includedir /etc/sudoers.d
jean ALL = (ALL) NOPASSWD:ALL



```


Thanks

---

### Post by TheFu on 2013-09-22
I don't see any sudo in the examples, but if you are trying to use something like:
```
sudo mkdir  /etc/TTTTT
sudo dpkg --get-selections > /etc/TTTTT/my-great-list-o-packages-for-backups.txt
```
then understand that sudo only works on the first command and nothing after the redirection. That is just the **dpkg --get-selections** part.  The  **> /etc/TTTTT/my-great-list-o-packages-for-backups.txt** redirects with the privileges of your normal userid.  

There are 3 ways around this.  Group the entire command inside the sudo (can't recall how right now), redirect the output to a place your normal account can write (~/my-great-list-o-packages-for-backups.txt) then move the file to where you really want it and chown.  or start an interactive root shell  with **sudo -s**.

---

### Post by Lars Noodén on 2013-09-22
> **TheFu said:**
>  Group the entire command inside the sudo (can't recall how right now)

One way is that you could wrap it in [sh](http://manpages.ubuntu.com/manpages/raring/en/man1/sh.1posix.html).

```

sudo sh -c 'dpkg --get-selections > /etc/TTTTT/my-great-list-o-packages-for-backups.txt'

```

---

