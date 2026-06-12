---
title: "Ubuntu 8.04 keeps changing my password back to Unix one. from samba password."
date: 2008-05-16
forum: General Help
---

### Post by gizm0 on 2008-05-16
I'm still having problems with my Samba (Ubuntu 8.04). It keeps changing my samba password back to Unix one. Although i have changed these settings in smb.conf unix password sync = no and pam password change = no. How do i solve this problem?

I'm using clean install of Ubuntu 8.04.

---

### Post by pointone on 2008-05-16
After changing settings in smb.conf, you need to restart the Samba daemon for the changes to take effect.

---

### Post by gizm0 on 2008-05-17
> **pointone said:**
> After changing settings in smb.conf, you need to restart the Samba daemon for the changes to take effect.

I have done /etc/init.d/samba restart and rebooted my PC several times. It didn'lp help :(. Here is my  smb.conf in the attachement. 

By the way i tried to copy new smb.conf from /usr/share/samba/ and just edit some parts of it, but that didnt help either. What i'm doing wrong here?:(

---

### Post by gizm0 on 2008-05-17
I tried to reinstall samba. Now i got these errors:
> sudo apt-get remove --purge samba; sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 9425kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 100597 files and directories currently installed.)
Removing samba ...
 * Stopping Samba daemons                                                [ OK ] 
Purging configuration files for samba ...
Removing configuration file /etc/default/samba...
Removing configuration file /etc/default/samba...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/3838kB of archives.
After this operation, 9425kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 100547 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.28a-1ubuntu4_i386.deb) ...
Setting up samba (3.0.28a-1ubuntu4) ...
Generating /etc/default/samba...
export_database: username="(NULL)"
tdbsam_open: Converting version 0 database to version 3.
TDBSAM converted successfully.[b]
tdb(unnamed): tdb_open_ex: could not open file /var/lib/samba/account_policy.tdb: No such file or directory
account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to chan[/B]

---

### Post by gizm0 on 2008-05-19
I reinstalled the whole Ubuntu and that solved the problem.

---

### Post by duckville on 2008-05-19
> **gizm0 said:**
> I reinstalled the whole Ubuntu and that solved the problem.

sorry you had to do that,
but your statement reminds me an OS i used a while back lol...
what's it name again....
can't remember haven't had much e**XP**erience with it for a while now...:lolflag:

---

