---
title: "samba hates me..."
date: 2006-12-20
forum: General Help
---

### Post by Darth_tater on 2006-12-20
i finally got samba working w/ mt login credentials.
but... i can view the directory and thats all.  i cant write to it or delete from it.

hers the kicker.... my webmin configuration says that the security settings are set to "Read/write to everyone"

this clearly isn't the case as i cannot delete or read to the disk.  its rather annoying.

here is my sambe.conf

> #
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	socket options = TCP_NODELAY
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	passdb backend = tdbsam
	dns proxy = no
	netbios name = karl's UL
	writeable = yes
	server string = MultiServ (karl ONLY)
	invalid users = root
	workgroup = LOFTAREA
	os level = 20
	valid users = karl
	security = user
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
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

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

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
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects

# Put a capping on the size of the log files (in Kb).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


;   guest account = nobody

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

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








wins support = no
[wwwul]
	writable = yes
	wide links = no
	path = /var/www
	force user = karl
	comment = this is the UL dir
	create mode = 777
	browsable = yes
	public = yes
	available = yes



any ideas? thanks!

---

### Post by ayoli on 2006-12-20
/var/www doesnt belongs to your user, it usually belongs to root, and is only readable by other groups/users.
if you want to be able to write to this dir you have to 
chmod -R a+w /var/www
but its a bad idea IMO. if it's for web use why dont you use apache's userdir module which allow you to publish pages in /home/you_username/public_html which would be easier to share with samba ?

---

### Post by Darth_tater on 2006-12-20
ok... thanks.

i know what chmod would do and your right... not exactly the best idea

ill look into the userdir module

---

### Post by scrooge_74 on 2006-12-20
> **Darth_tater said:**
> ok... thanks.

i know what chmod would do and your right... not exactly the best idea

ill look into the userdir module

SAMBA hates all of us that have been not properly iniciated.

In the end I dumped webmin and did my config by hand:

sudo nano /etc/samba /smb.conf

Try reading and following the tutorials in [http://samba.org](http://samba.org)

Also [http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

---

### Post by rotten777 on 2006-12-20
> **scrooge_74 said:**
> SAMBA hates all of us that have been not properly iniciated.

In the end I dumped webmin and did my config by hand:

sudo nano /etc/samba /smb.conf

Try reading and following the tutorials in [http://samba.org](http://samba.org)

Also [http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)



I will have to agree here. Read the latest Samba documentation and use the latest version. Configure it by hand and you'll get a better grip on it's workings. You may also want to double-check the file system permissions when sharing and accessing from samba clients.

If you want to read up on unix permissions, check here:
[http://www.dartmouth.edu/~rc/help/faq/permissions.html](http://www.dartmouth.edu/~rc/help/faq/permissions.html)

---

### Post by Darth_tater on 2006-12-20
thanks for all your replies! 

i use webmin as a type of "double checker"  its kept me from making some pretty stupid mistakes in the past.  i also find it useful that i can use the "gui mode" to configure things or directly edit the config files. 

anybody have a good link to a tutorial on the usage of the userdir module syntax (basically, how do i adjust my config file)

edit:  durr.. i feel retarded now :(... couldn't i just set my document root for apache to be a directory within my home directory?  it makes sense too because i have other files (music/movies) i can share.. and they are located in my home directory.

---

### Post by scrooge_74 on 2006-12-20
> **Darth_tater said:**
> thanks for all your replies! 

i use webmin as a type of "double checker"  its kept me from making some pretty stupid mistakes in the past.  i also find it usefull that i can use the "gui mode" to configure things or directly edit the config files. 

anybody have a good link to a tutorial on the usage of the userdir module syntax (basically, how do i adjust my config file)

I tried webmin and swat in the past, I ended up using nano to edit smb.conf

and then tesparm smb.conf

any error will come up there

---

### Post by ayoli on 2006-12-20
> **Darth_tater said:**
> thanks for all your replies! 

i use webmin as a type of "double checker"  its kept me from making some pretty stupid mistakes in the past.  i also find it useful that i can use the "gui mode" to configure things or directly edit the config files. 

anybody have a good link to a tutorial on the usage of the userdir module syntax (basically, how do i adjust my config file)

edit:  durr.. i feel retarded now :(... couldn't i just set my document root for apache to be a directory within my home directory?  it makes sense too because i have other files (music/movies) i can share.. and they are located in my home directory.

if you're using apache2 (which is default on ubuntu dapper or edgy) just
```
sudo a2enmod userdir && sudo /etc/init.d/apache2 reload
```
then make a dir in your home:
```
mkdir ~/public_html
```
then in your browser:
[http://localhost/~your_username/](http://localhost/~your_username/)

---

### Post by Darth_tater on 2006-12-20
thanks for all your help...

i simply moved the document root to my home folder and changed the permissions so that i am the only one that can read and write to it (i have enabled read in a few other accounts).

i can still login to upload to it, apache serves it... what more could i want!

again, thanks for the help.  a good "nub-friendly" community makes it easier to "forget" vista:D  and transition to a different OS

cheers!

---

