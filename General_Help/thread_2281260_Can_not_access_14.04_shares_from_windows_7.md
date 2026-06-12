---
title: "Can not access 14.04 shares from windows 7"
date: 2015-06-05
forum: General Help
---

### Post by LG_Auction on 2015-06-05
Samba is installed on Ubuntu 14.04. I can access the public share on Windows 7. I can see the Ubuntu computer on Windows Explorer, but can not log in. I always get a Windows Security dialog to enter a password. The user name and password for Ubuntu are correct and there is a Samba user created with this info. 

I had great success with 12.04, but no joy now. 

Any hints would be greatly appreciated.

---

### Post by bab1 on 2015-06-05
> **LG_Auction said:**
> Samba is installed on Ubuntu 14.04. I can access the public share on Windows 7. I can see the Ubuntu computer on Windows Explorer, but can not log in. I always get a Windows Security dialog to enter a password. The user name and password for Ubuntu are correct and there is a Samba user created with this info. 

I had great success with 12.04, but no joy now. 

Any hints would be greatly appreciated.

Post the output of these 2 terminal commands```
cat /etc/samba/smb.conf

smbtree -d3
```
Please post all data between the [noparse] ```
  
``` [/noparse]blocks.  You can do this by clicking on the [SIZE=5]**# **[/SIZE] icon located at the top center of the advanced editor that you are using to respond to this forum.

If your shares were created using file manager (i.e. nautilus) GUI then post the output of this command```
net usershare info --long
```

---

### Post by LG_Auction on 2015-06-07
Here is the output from all three commands. 

Thank you for looking!


	

```
> cat /etc/samba/smb.conf
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 

#======================= Global Settings =======================

[global]
	panic action = /usr/share/samba/panic-action %d
	workgroup = LGAS
	server string = %h server (Samba, Ubuntu)
	passwd program = /usr/bin/passwd %u
	server role = standalone server
	pam password change = yes
	os level = 20
	obey pam restrictions = no
	map to guest = bad user
	usershare allow guests = yes
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	log file = /var/log/samba/log.%m
	syslog = 0
	passdb backend = tdbsam
	unix password sync = yes
	dns proxy = no
	max log size = 1000

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects

# Cap the size of the individual log files (in KiB).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections

########## Domains ###########

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

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

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

> smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.75 bcast=192.168.1.255 netmask=255.255.255.0
Enter GUEST's password: resolve_lmhosts: Attempting lmhosts lookup for name LGAS<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name LGAS<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name LGAS<0x1d>
Got a positive name query response from 192.168.1.75 ( 192.168.1.75 )
Connecting to 192.168.1.75 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
LGAS
Connecting to 192.168.1.75 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\SUGAR          		Sugar server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name SUGAR<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name SUGAR<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SUGAR<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\SUGAR\Spice          	
		\\SUGAR\Data           	
		\\SUGAR\LGAS-Net-BU    	
		\\SUGAR\Sugar-Public   	
		\\SUGAR\HP-LaserJet-4050-Series	HP LaserJet 4050 Series
		\\SUGAR\Zebra-ZPL-Label	Zebra ZPL Label
		\\SUGAR\print$         	Printer Drivers
		\\SUGAR\IPC$           	IPC Service (Sugar server (Samba, Ubuntu))
	\\ROBERTDALE-PC  		
resolve_lmhosts: Attempting lmhosts lookup for name ROBERTDALE-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name ROBERTDALE-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name ROBERTDALE-PC<0x20>
resolve_hosts: getaddrinfo failed for name ROBERTDALE-PC [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name ROBERTDALE-PC<0x20>
Got a positive name query response from 192.168.1.88 ( 192.168.1.88 )
Connecting to 192.168.1.88 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\ROBERTDALE-PC\ZEBRA S600     	ZEBRA S600
		\\ROBERTDALE-PC\Users          	
		\\ROBERTDALE-PC\RED_DVD        	
		\\ROBERTDALE-PC\print$         	Printer Drivers
		\\ROBERTDALE-PC\Photo_Room     	
		\\ROBERTDALE-PC\Ortery RED     	
		\\ROBERTDALE-PC\IPC$           	Remote IPC
		\\ROBERTDALE-PC\C$             	Default share
		\\ROBERTDALE-PC\ADMIN$         	Remote Admin
	\\CENTRAL-OFFICE 		
resolve_lmhosts: Attempting lmhosts lookup for name CENTRAL-OFFICE<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name CENTRAL-OFFICE<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name CENTRAL-OFFICE<0x20>
resolve_hosts: getaddrinfo failed for name CENTRAL-OFFICE [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name CENTRAL-OFFICE<0x20>
Got a positive name query response from 192.168.1.100 ( 192.168.1.100 )
Connecting to 192.168.1.100 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\CENTRAL-OFFICE\Users          	
		\\CENTRAL-OFFICE\Ricoh Aficio 1515 PCL6	Ricoh Aficio 1515 PCL6
		\\CENTRAL-OFFICE\Public         	
		\\CENTRAL-OFFICE\print$         	Printer Drivers
		\\CENTRAL-OFFICE\lgas-nb_QuickBooks	
		\\CENTRAL-OFFICE\IPC$           	Remote IPC
		\\CENTRAL-OFFICE\HP 4050n       	HP 4050N on PCL 5
		\\CENTRAL-OFFICE\FreeAgent      	
		\\CENTRAL-OFFICE\F$             	Default share
		\\CENTRAL-OFFICE\D$             	Default share
		\\CENTRAL-OFFICE\C$             	Default share
		\\CENTRAL-OFFICE\ADMIN$         	Remote Admin
> net usershare info --long
[Spice]
path=/media/Spice
comment=
usershare_acl=Everyone:F,
guest_ok=n

[Data]
path=/media/Data
comment=
usershare_acl=Everyone:F,
guest_ok=n

[LGAS-Net-BU]
path=/media/Spice/LGAS-Net-BU
comment=
usershare_acl=Everyone:F,
guest_ok=n

[Sugar-Public]
path=/home/bobdale/Public
comment=
usershare_acl=Everyone:F,
guest_ok=n
```

Enter a shell command to execute in the text field below. The cd command may be used to change directory for subsequent commands.

---

### Post by bab1 on 2015-06-07
> **LG_Auction said:**
> Here is the output from all three commands. 

Thank you for looking!


The smb.conf file looks fine.
> 
```
$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.1.75 bcast=192.168.1.255 netmask=255.255.255.0
[COLOR="#FF0000"]**Enter GUEST's password: **[/COLOR]
resolve_lmhosts: Attempting lmhosts lookup for name LGAS<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name LGAS<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name LGAS<0x1d>
Got a positive name query response from 192.168.1.75 ( 192.168.1.75 )
Connecting to 192.168.1.75 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
LGAS
Connecting to 192.168.1.75 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\SUGAR          		Sugar server (Samba, Ubuntu)
resolve_lmhosts: Attempting lmhosts lookup for name SUGAR<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name SUGAR<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SUGAR<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\SUGAR\Spice          	
		\\SUGAR\Data           	
		\\SUGAR\LGAS-Net-BU    	
		\\SUGAR\Sugar-Public   	
		\\SUGAR\HP-LaserJet-4050-Series	HP LaserJet 4050 Series
		\\SUGAR\Zebra-ZPL-Label	Zebra ZPL Label
		\\SUGAR\print$         	Printer Drivers
		\\SUGAR\IPC$           	IPC Service (Sugar server (Samba, Ubuntu))
	\\ROBERTDALE-PC  		
resolve_lmhosts: Attempting lmhosts lookup for name ROBERTDALE-PC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name ROBERTDALE-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name ROBERTDALE-PC<0x20>
resolve_hosts: getaddrinfo failed for name ROBERTDALE-PC [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name ROBERTDALE-PC<0x20>
Got a positive name query response from 192.168.1.88 ( 192.168.1.88 )
Connecting to 192.168.1.88 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\ROBERTDALE-PC\ZEBRA S600     	ZEBRA S600
		\\ROBERTDALE-PC\Users          	
		\\ROBERTDALE-PC\RED_DVD        	
		\\ROBERTDALE-PC\print$         	Printer Drivers
		\\ROBERTDALE-PC\Photo_Room     	
		\\ROBERTDALE-PC\Ortery RED     	
		\\ROBERTDALE-PC\IPC$           	Remote IPC
		\\ROBERTDALE-PC\C$             	Default share
		\\ROBERTDALE-PC\ADMIN$         	Remote Admin
	\\CENTRAL-OFFICE 		
resolve_lmhosts: Attempting lmhosts lookup for name CENTRAL-OFFICE<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name CENTRAL-OFFICE<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name CENTRAL-OFFICE<0x20>
resolve_hosts: getaddrinfo failed for name CENTRAL-OFFICE [Name or service not known]
name_resolve_bcast: Attempting broadcast lookup for name CENTRAL-OFFICE<0x20>
Got a positive name query response from 192.168.1.100 ( 192.168.1.100 )
Connecting to 192.168.1.100 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\CENTRAL-OFFICE\Users          	
		\\CENTRAL-OFFICE\Ricoh Aficio 1515 PCL6	Ricoh Aficio 1515 PCL6
		\\CENTRAL-OFFICE\Public         	
		\\CENTRAL-OFFICE\print$         	Printer Drivers
		\\CENTRAL-OFFICE\lgas-nb_QuickBooks	
		\\CENTRAL-OFFICE\IPC$           	Remote IPC
		\\CENTRAL-OFFICE\HP 4050n       	HP 4050N on PCL 5
		\\CENTRAL-OFFICE\FreeAgent      	
		\\CENTRAL-OFFICE\F$             	Default share
		\\CENTRAL-OFFICE\D$             	Default share
		\\CENTRAL-OFFICE\C$             	Default share
		\\CENTRAL-OFFICE\ADMIN$         	Remote Admin

```
This shows all the smb shares on the network.  The only thing unusual is this```
[COLOR="#FF0000"]**Enter GUEST's password:**[/COLOR] 
```...do you have a user named GUEST?  The guest account is normally invoked any time the a user that is NOT in the Samba user database.
> ```
> net usershare info --long
[Spice]
path=/media/Spice
comment=
usershare_acl=Everyone:F,
guest_ok=n

[Data]
path=/media/Data
comment=
usershare_acl=Everyone:F,
guest_ok=n

[LGAS-Net-BU]
path=/media/Spice/LGAS-Net-BU
comment=
usershare_acl=Everyone:F,
guest_ok=n

[Sugar-Public]
path=/home/bobdale/Public
comment=
usershare_acl=Everyone:F,
guest_ok=n
```


Earlier you said this> "The user name and password for Ubuntu are correct and there is a Samba user created with this info."
Post the output of this command```
sudo pdbedit -L
```

---

### Post by LG_Auction on 2015-06-07
Here is the output of pdbedit -L.

```
nobody:65534:nobody
bobdale:1000:Robert Dale
photobench-pc:1001:Robert Dale
```

---

### Post by bab1 on 2015-06-07
> **LG_Auction said:**
> Here is the output of pdbedit -L.

```
nobody:65534:nobody
bobdale:1000:Robert Dale
photobench-pc:1001:Robert Dale
```

I'm confused.  It looks like you were logged in as GUEST when you ran the smbtree -d3 command.  That's not consistent with the pdbedit results.  What name are you trying to log in as when this fails?  Are you logged into the Windows machine as bobdale?

The Samba guest account is not the same as you having a user named GUEST.  The Samba guest account is really more like an anonymous account.  By default it uses the user=nobody.

---

### Post by LG_Auction on 2015-06-08
Good afternoon.

Both times I ran commands I was logged into Ubuntu through Webmin from home. Same username, same password both times.

---

### Post by bab1 on 2015-06-08
> **LG_Auction said:**
> Good afternoon.

Both times I ran commands I was logged into Ubuntu through Webmin from home. Same username, same password both times.

Webmin can be a complication.  I'm not sure what you mean by "Same username, same password both times".  Do you mean you were using the login on Windows of bobdale?

For a test, why not set a share to allow guest access and see if that works.  If so I my guess is that you have problems with the share definition or the permissions on the share directory. 

Post the output of these commands to show the permissions on the share```
ls -l / grep media

ls -l /media
```...post this to show your login```
who am i
```

---

