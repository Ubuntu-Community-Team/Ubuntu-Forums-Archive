---
title: "known_hosts file changing permissions automatically?"
date: 2015-09-03
forum: General Help
---

### Post by vfulco on 2015-09-03
On 15.04, I am ssh'ing in to a new linode server using ansible, dokku and docker.  When I first try to make connection, my public key is failing.  Look at permissions in /home/foo/.ssh folder and all permissions are set for me as user (sudo, admin) except for known_hosts file.  Reset file for user permissions.  Destroy the server later on, try again to setup and provision the server and known_hosts file reverts back to root permissions,  How is that possible? TIA.

---

### Post by TheFu on 2015-09-04
Anything is possible.

If you can be more exact.  What userid?  What files and which permissions?  An **ls -al ~/.ssh/** should provide all the data we need.
```
$ ls -al ~/.ssh/
total 64
drwx------  2 thefu thefu  4096 Aug 23 17:37 ./
drwxr-xr-x 91 thefu thefu  4096 Sep  4 11:56 ../
-rw-------  1 thefu thefu   783 Feb 19  2015 authorized_keys
-rw-------  1 thefu thefu  1999 Aug 23 17:37 config
-rw-------  1 thefu thefu  1675 Nov 15  2014 id_rsa
-rw-r--r--  1 thefu thefu   389 Nov 15  2014 id_rsa.pub
-rw-------  1 thefu thefu 20050 Aug 18 14:51 known_hosts
-rw-------  1 thefu thefu 18716 Jun 12 10:01 known_hosts.old
```
These are the proper permissions for a non-root login.  ssh doesn't like this directory to be too open.

---

