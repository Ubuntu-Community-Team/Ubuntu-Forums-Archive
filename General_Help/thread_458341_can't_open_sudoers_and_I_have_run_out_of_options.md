---
title: "can't open sudoers and I have run out of options"
date: 2007-05-29
forum: General Help
---

### Post by dsowerby on 2007-05-29
I get "can't open /etc/sudoers: Permission denied" after digging a hole for myself.  I made some recursive changes to permissions in  /etc and have been locked out of sudo since.   

I've tried / checked the following , but am now stuck for any further ideas.

There are quite a few posts on this and among others I've tried [  this ]("https://help.ubuntu.com/community/RootSudo") and  [ this ]("http://www.psychocats.net/ubuntu/sudo").

I can log in as su (don't know when I made that possible) or start in recovery mode as root

mode of /etc/sudoers is 0440
-r--r----- 1 root root 546 2007-05-29 00:27 sudoers
I am in both admin and adm groups
I've opened and resaved with visudo (and made sure it wasn't the .tmp file)
content of /etc/sudoers is 

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

#added to allow backuppc to run tar without password see http://backuppc.sourceforge.net/fa$
backuppc ALL = NOPASSWD: /bin/tar

---

### Post by kuja on 2007-05-29
Boot up a live cd, mount your ubuntu partition, change the files and permissions back, done :)

---

### Post by dsowerby on 2007-05-30
Thanks but I don't really need to boot from CD - as above, I can log in as root.  It is more a question of what do I change the permissions back to ... which files are associated with sudoers?

---

