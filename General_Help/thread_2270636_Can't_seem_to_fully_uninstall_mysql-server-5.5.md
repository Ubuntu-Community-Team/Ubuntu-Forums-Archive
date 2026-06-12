---
title: "Can't seem to fully uninstall mysql-server-5.5"
date: 2015-03-24
forum: General Help
---

### Post by michael274 on 2015-03-24
I am trying to uninstall everything mysql related.  I have ran multiple purge commands, deleted various directories and searched everywhere for my problem but can't seem to find a working solution.  My installation of mysql-server-5.5 is corrupt, and therefore cannot properly uninstall.  My end goal is to re-install, as I previously messed up the my.cnf or socket files along the way and mysql-server would not start after rebooting for the first time.

My attempted removal:
*sudo apt-get remove --purge mysql\**

Here is some related output showing mysql-server stuck at purge:
*root@mikeserver-MS-7821:~# dpkg -l | grep -i mysql*
*pF  mysql-server-5.5                                      5.5.41-0ubuntu0.14.04.1                             amd64        MySQL database server binaries and system database setup*
*root@mikeserver-MS-7821:~# dpkg --get-selections | grep mysql*
*mysql-server-5.5                                purge*
*root@mikeserver-MS-7821:~#*

Upon attempt to uninstall/or re-install, an error is received:
*Errors were encountered while processing:*
* mysql-server-5.5*
[I]E: Sub-process /usr/bin/dpkg returned an error code (1)

[/I]Any help would be greatly appreciated.   I can provide any output requested.
PS. I apologize for any miss-formatting.  Long time lurker, first time poster.

---

### Post by dino99 on 2015-03-24
install an d load 'synaptic', then with it search about the installed 'mysql' packages, then try to purge them one by one (maybe there is some crossed dependencies) ( there is none on a default installation by the way)

---

### Post by michael274 on 2015-03-24
I'm not too familiar with synaptic, but wouldn't the result be the same as doing '*dpkg -l | grep -i mysql' *?  In that case, the mysql-server-5.5 instance appears to be the only thing installed.

---

