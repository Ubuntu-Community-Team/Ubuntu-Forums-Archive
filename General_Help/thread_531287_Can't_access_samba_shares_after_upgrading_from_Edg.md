---
title: "Can't access samba shares after upgrading from Edgy to Feisty"
date: 2007-08-21
forum: General Help
---

### Post by geekgerl on 2007-08-21
Hello,

I recently upgraded from Kubuntu Edgy to Kubuntu Feisty, and I can no longer access my Samba server shares. I am not running iptables, and I have a very basic setup in smb.conf:

[myshare]
path = /var/myshare
guest ok = yes
read only = no
admin users = laura
case sensitive = no
strict locking = no
msdfs proxy = no

When I attempt to connect, I get the following error:

root@CHI-W:/etc/samba# smbclient -U laura //localhost/myshare
Password:
Domain=[CHI-W] OS=[Unix] Server=[Samba 3.0.24]
Connection to \ô·ÿ:å·ôoõ· failed
root@CHI-W:/etc/samba#

No error messages are logged under /var/log/samba when this occurs. When I enter an incorrect password, I get the expected error:

root@CHI-W:/var/log/samba# smbclient -U laura //localhost/myshare
Password:
session setup failed: NT_STATUS_LOGON_FAILURE
root@CHI-W:/var/log/samba#

I have reinstalled samba, samba-common, and smbclient but I still get the same errors. I'm guessing that a newer version of samba was installed as part of the upgrade to Fesity, and perhaps I need to add some additional options to smb.conf to get this to work. In both Edgy and Fesity I configured samba folders through Konqueror, but maybe that doesn't work in Feisty? I'm sorry that I can't provide more information, I'm not sure why the samba logs aren't reporting errors!

Thanks!

-Laura

---

