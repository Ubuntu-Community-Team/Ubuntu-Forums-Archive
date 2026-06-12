---
title: "samba4 PDC, smbstatus provides no info"
date: 2014-11-13
forum: General Help
---

### Post by jakkuk on 2014-11-13
Hi! I have successfully managed to migrate my samba 3 NT domain from gentoo to a fully operational samba 4 AD on Ubuntu 14.04 LTS with roaming profiles, MMC management and what not. Over 50 users log into that daily.

I've got a number of problems, but let's tackle them one by one. 

When I try to use smbstatus to check who is using the server and what files are being open, I'm getting:
```

# smbstatus 

Samba version 4.1.6-Ubuntu
PID     Username      Group         Machine                        
-------------------------------------------------------------------

Service      pid     machine       Connected at
-------------------------------------------------------

/var/run/samba/locking.tdb not initialised
This is normal if an SMB client has never connected to your server.

```

[LIST]
[*] I cannot find locking.tdb in any of the samba directories,
[*] locking is enabled in smb.conf
[/LIST]

I've tried googling, with no results.

My smb.conf:
```
[global]
	workgroup = GPMV
	realm = my.realm.dot.com
	netbios name = PDC
	server role = active directory domain controller
	idmap_ldb:use rfc2307 = yes
	dns forwarder = 192.168.0.252
	server services = rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate, dns, smb
	dcerpc endpoint servers = epmapper, wkssvc, rpcecho, samr, netlogon, lsarpc, spoolss, drsuapi, dssetup, unixinfo, browser, eventlog6, backupkey, dnsserver, winreg, srvsvc
	client use spnego = yes

	locking = yes


[netlogon]
 	path = /var/local/samba/var/lib/samba/netlogon
	#path = /var/lib/samba/sysvol/biuro.gpm-vindexus.pl/scripts
	read only = No

[sysvol]
	path = /var/lib/samba/sysvol
	read only = No

[profiles] 
 path = /var/local/samba/var/lib/samba/profiles
 read only = no
 browseable = no

[some other shares follow]

```

What can you suggest? What can I check? Or maybe latest samba does not write locks to disk and stores them in memory to be read by some other tool?

---

### Post by bab1 on 2014-11-13
> **jakkuk said:**
> Hi! I have successfully managed to migrate my samba 3 NT domain from gentoo to a fully operational samba 4 AD on Ubuntu 14.04 LTS with roaming profiles, MMC management and what not. Over 50 users log into that daily.

I've got a number of problems, but let's tackle them one by one. 

When I try to use smbstatus to check who is using the server and what files are being open, I'm getting:
```

# smbstatus 

Samba version 4.1.6-Ubuntu
PID     Username      Group         Machine                        
-------------------------------------------------------------------

Service      pid     machine       Connected at
-------------------------------------------------------

/var/run/samba/locking.tdb not initialised
This is normal if an SMB client has never connected to your server.

```

[LIST]
[*] I cannot find locking.tdb in any of the samba directories,
[*] locking is enabled in smb.conf
[/LIST]

I've tried googling, with no results.

My smb.conf:
```
[global]
	workgroup = GPMV
	realm = my.realm.dot.com
	netbios name = PDC
	server role = active directory domain controller
	idmap_ldb:use rfc2307 = yes
	dns forwarder = 192.168.0.252
	server services = rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate, dns, smb
	dcerpc endpoint servers = epmapper, wkssvc, rpcecho, samr, netlogon, lsarpc, spoolss, drsuapi, dssetup, unixinfo, browser, eventlog6, backupkey, dnsserver, winreg, srvsvc
	client use spnego = yes

	locking = yes


[netlogon]
 	path = /var/local/samba/var/lib/samba/netlogon
	#path = /var/lib/samba/sysvol/biuro.gpm-vindexus.pl/scripts
	read only = No

[sysvol]
	path = /var/lib/samba/sysvol
	read only = No

[profiles] 
 path = /var/local/samba/var/lib/samba/profiles
 read only = no
 browseable = no

[some other shares follow]

```

What can you suggest? What can I check? Or maybe latest samba does not write locks to disk and stores them in memory to be read by some other tool?

Just a guess on my part, but I would start with the information listed in posts #4, 5 and 6 of [this thread]("http://ubuntuforums.org/showthread.php?t=2224951").

---

### Post by jakkuk on 2014-11-17
> **bab1 said:**
> Just a guess on my part, but I would start with the information listed in posts #4, 5 and 6 of [this thread]("http://ubuntuforums.org/showthread.php?t=2224951").

Checked this - those recommendations are pretty basic, that are required to get samba 4 PDC working. I've got this covered, since my installation works. Thanks anyway, one more check will not hurt. I guess I need to ignore the problem for now...

---

### Post by jakkuk on 2014-11-18
OK, I know what the problem was. I was using the ntvfs samba service to serve files. I should be using s3fs, as it is the production intended module by the samba team.

I should change from this

```

	server services = rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate, dns, smb

```

to this:

```
	server services = rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate, dns, s3fs

```

Such a bold move means, that a different way of mapping Windows ACLS onto the file system is used, so all permissions should be redone by the administrator from within a windows box. A special care should be taken when it comes to the sysvol share with policies (samba-tool ntacl sysvolreset command is your friend).

---

