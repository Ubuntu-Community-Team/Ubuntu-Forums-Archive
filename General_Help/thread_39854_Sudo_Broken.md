---
title: "Sudo Broken?"
date: 2005-06-06
forum: General Help
---

### Post by DutchLau on 2005-06-06
I've been trying to use the sudo command, but it seems like my "sudo" is broken. When I try starting up synaptic it gives me the following error message:

> Failed to run /usr/sbin/synaptic
Child terminated with 1 status 

Similarly when I try running synaptic (or any other "sudo" program) from a terminal I get errors:

> discom@discom:~$ sudo synaptic
sudo: must be setuid root 

What has happened? Is there any any way to fix this problem?

---

### Post by az on 2005-06-06
Did you bork your sudoers file?  It should have a line like this in it:

user ALL=(ALL) ALL


Where user is youe user name.

Boot into recovery mode to become root and fix it with

nano /etc/sudoers

---

