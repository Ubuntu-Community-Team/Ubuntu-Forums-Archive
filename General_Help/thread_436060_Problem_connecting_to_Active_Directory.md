---
title: "Problem connecting to Active Directory"
date: 2007-05-07
forum: General Help
---

### Post by Jenillaroma on 2007-05-07
I have installed Ubuntu Fiesty.  I am trying to put active directory on.  I went through all my conf's and all the How-To's I have looked at there is no difference in mine to there's.  I can get a ticket.  But when I put in : net ads join -U [email]domainadminuser@DOMAIN.INTE[/email]RNAL  it gives me this message.
[2007/05/07 13:51:46, 0] passdb/secrets.c:secrets_init(66)
  Failed to open /var/lib/samba/secrets.tdb
Invalid configuration.  Exiting....
Then when I put sudo in front of net ads join -U [email]domainadminuser@DOMAIN.INTE[/email]RNAL it gives me this message.
[2007/05/07 14:12:18, 0] libsmb/cliconnect.c:cli_session_setup_spnego(785)
  Kinit failed: KDC reply did not match expectations
Failed to join domain!

Can anyone help me please??  Thank you in advanced!!!!!!!!!!!!!!!!!!1

My smb.conf is :
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuation file.  You should read the
# smb.conf(5) manual page in order to understand the options listed
# here.  Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash)
# is a comment and is ignored.  In this example we will use a #
# for commentay and a ; for parts of the config file that you
# may wish to enable
#
# NOTE:  Whenever you modify this file you should run the command
# "testeparm" to check that you have not made any basic syntactic
# errors.
#

# ======================== Global Settings ======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your samba server will
part of
	workgroup = DOMAIN
	netbios name = Username
	realm = DOMAIN.INTERNAL
	password server = domainserver.domain.internal
	winbind separator = +
	winbind enum users = no
	winbind enum groups = no
	winbind use default domain = yes
	template homedir = /home/%D/%U
	template shell = /bin/bash
	client use spnego = yes
	domain master = no

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS
Server
;   wins support = no

# WINS Server -Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT
both
;    wins server = w.x.y.z

# This will prvent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

# What naming service and in what order should we use to resolve host
names
# to IP addresses
;    name resole order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;    interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the 
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine
is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;    bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog.
Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead.  If you want to
log
# through syslog you should set the following parameter to something
higher.
    syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
    panic action = /usr/share/samba/panic-action %d


####### Authentication ########

# "security = user" is always a good idea.  This will require a Unix
account
# in this server for every user accessing the server.  See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-
Collection/ServerType.html
# in the samba-doc package for details.
	security = ads

# You may wish to use password encrypted passwords, Samba will need to know # what password database type you are using.
	passdb backend = tdbsam

	obey pam restrictions = yes
;	guest account = nobody
	invalid users = root

# This boolean parameter controls whether Samba attempts to sync the 
Unix
# password with the SMB password when the encrypted SMB password in the 
# passdb is changed.
;	unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan
# <<kahan@informatik.tumuenchen.de> for sending the correct chat script for # the passwd program in Debian Sarge).
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully*.

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
;	pam password change = no

########## Domains ##########

# Is this machine able to authenticate users.  Both PDC and BDC
# must have this setting enabled.  If you are the BDC you must
# change the 'domain master' setting to no
#
;	domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;	logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
;	logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;	logon drive = H:
;	logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the scrip to run during logon.  The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;	logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" # %u

########## Printing ##########

# If you want to automatically load your printer list rather 
# than setting them up individually then you'll need this
;	load printers = yes

# lpr(ng) printing.  You may wish to override the location of the
# printcap file
;	printing = bsd
;	printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the cupsys-client
# package.
;	printing = cups
;	printcap name = cups

# When using [print$], root is implicity a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;	printer admin = #lpadmin

########## Misc ##########

# Using the following line enables you to customise your configuration
# on a per machine basis.  The %m gets replaced with the netbios name
# of the machine that is connecting
;	include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
#		SO_RCVBUF=8192 SO_SNDBUF=8192
	socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed.  The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;	message command = /bin/sh -c '/usr/bin/linpopup "%f" :%m" %s; rm %s' $

# Domain Master specifies Samba to be the Domain Master Browser.  If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;	domain master = auto

# Some defaults for winbind (make sure you're not using the ranges for
# something else.)
	idmap uid = 500-10000000
	idmap gid = 500-10000000
;	template shell = /bin/bash

#========================= Share Definitions =========================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;	comment = Home Directories
;	browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;	valid users = %S

# By default, the home directories are exported read-only.  Change next
# parameter to 'yes' if you want to be able to write to them.
;	writable = no

# File creation mask is set to 0600 for security reasons.  If you want to
# create files with group=rw permissions, set next parameter to 0664.
;	create mask = 0600

# Directory ceation mask is to 0700 for security reasons.  If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;	directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;	comment = Network Logon Service
;	path = /home/samba/netlogon
;	guest ok = yes
;	writable = no
;	share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be wriable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;	comment = Users profiles
;	path = /home/samba/profiles
;	guest ok = no
;	browseable = no
;	create mask = 0600
;	directory mask = 0700

[printers]
	comment = All Printers
	browseable = no
	path = /temp
	printable = yes
	public = no
	writable = no
	create mode = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	browseable = yes
	read only = yes
	guest ok - no

# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;	write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;	comment = Samba server's CD-ROM
;	writable = no
;	locking = no
;	path = /cdrom
;	public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed.  For this to work /etc/fstab must contain
#	an entry like this:
#
#	/dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user  0  0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;	preexec = /bin/mount  /cdrom
;	postexec = /bin/umount  /cdrom

---

### Post by behrendtb on 2007-05-10
take a look at [http://sadms.sourceforge.net/](http://sadms.sourceforge.net/)

-bj

---

### Post by StrangeBrew on 2008-01-24
Sounds great, but how do you install it?
I know...I'm a rookie...but there is not much info on how to install it.

---

