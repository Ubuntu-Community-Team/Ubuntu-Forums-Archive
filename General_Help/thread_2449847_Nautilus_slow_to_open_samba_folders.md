---
title: "Nautilus slow to open samba folders"
date: 2020-09-03
forum: General Help
---

### Post by irober02 on 2020-09-03
I've read quite a few old articles about slow samba connections but none seem to address my problem.

I have a file server running Ubuntu server 20.04 with a number of samba shares. 

I have a number of clients running Ubuntu 20.04 desktop with Nautilus (Files)  that can open folders on those shares but it is very S-L-O-W. I'm not concerned with download speeds or hostname resolution. It's slow to open the folders especially folders with a few hundred items in them. I don't think there's a problem connecting to the server as I rely on entries in /etc/hosts files on each client. ssh & sftp connect quickly.

I have a couple of MS Windows 10 clients (sorry about that) and they connect quickly to those shares (using hosts file entries also).

I don't think this problem existed with earlier Ubuntu releases but I may be remembering poorly. 

Since other clients connect quickly, I'm suspecting the the problem lies with Nautilus/Files - perhaps it's extracting metadata about the files before displaying the folder.

Can anybody give me some hints how to tweak either the file server or the Nautilus client to achieve better performance.

Here's part of the smb.conf file for reference:

```
# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

<snip />

[usr1]
    path = /data/samba/usr1
    browseable = no
    read only = no
    force create mode = 0660
    force directory mode = 2770
    valid users = usr1

[usr2]
    path = /data/samba/usr2
    browseable = no
    read only = no
    force create mode = 0660
    force directory mode = 2770
    valid users = usr2

[family]
    path = /data/samba/family
    browseable = no
    read only = no
    force create mode = 0660
    force directory mode = 2770
    valid users = usr1 usr2

<snip />

```

---

