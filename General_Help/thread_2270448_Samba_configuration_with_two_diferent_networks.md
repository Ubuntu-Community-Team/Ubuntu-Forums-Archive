---
title: "Samba configuration with two diferent networks"
date: 2015-03-23
forum: General Help
---

### Post by Joan_Agusti_Martin on 2015-03-23
Hi,

I'm want to resolve a issue that I have on my job. I have a samba 3.4.7 on a ubuntu 10.04 and I configure wins to use the domain with other network. 

The IP of the server is 192.168.1.10 and when I try to join to the domain with other IP of the same net this join successfully. 

The problem is when I try to join to this domain with other IP of other net, for example with 10.0.1.10 , I put it a tcpdump and i view the request and the response on samba server but in the client only I view the query but not the response from server and the result is error on the windows machine when this try to join on the domain.

This is my smb.conf :

 [global]	workgroup = domain
	netbios name = DC
	server string = " "
	passdb backend = ldapsam:ldap://localhost
	log level = 3
	syslog = 0
	log file = /var/log/samba/logssamba
	max log size = 1000
	name resolve order = host lmhost wins bcast
	server signing = auto
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192 SO_KEEPALIVE
	add user script = /usr/sbin/smbldap-useradd -m '%u'
	delete user script = /usr/sbin/smbldap-userdel %u
	add group script = /usr/sbin/smbldap-groupadd -a '%g'
	delete group script = /usr/sbin/smbldap-groupdel '%g'
	add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
	delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
	set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'
	add machine script = /usr/sbin/smbldap-useradd -w '%u'
	logon script = allusers.bat
	logon path = \\server\profiles\%U\%a
	domain logons = Yes
	os level = 35
	preferred master = Yes
	domain master = Yes
	dns proxy = No
	wins proxy = Yes
	wins support = Yes
	ldap admin dn = cn=admin,dc=domain,dc=local
	ldap group suffix = ou=Groups
	ldap idmap suffix = ou=Idmap
	ldap machine suffix = ou=Computers
	ldap passwd sync = yes
	ldap suffix = dc=domain,dc=local
	ldap ssl = no
	ldap user suffix = ou=Users
	panic action = /usr/share/samba/panic-action %d
	admin users = admin, root
	acl group control = Yes
	hide unreadable = Yes


[Home]
	path = /home/userhome
	read only = No
	security mask = 0770
	directory security mask = 0770


[netlogon]
	comment = Network Logon Service
	path = /var/lib/samba/netlogon
	read only = No
	guest ok = Yes


[profiles]
	comment = Users Profiles
	path = /var/lib/samba/profiles
	read only = No
	create mask = 0770
	directory mask = 0770

---

### Post by coffeecat on 2015-03-23
Not a Resolution Centre thread.

*Thread moved to **General Help**.*

---

