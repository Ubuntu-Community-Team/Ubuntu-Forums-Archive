---
title: "Can't use shared printer"
date: 2008-05-04
forum: General Help
---

### Post by arbulus on 2008-05-04
Ok, so I had this problem in Gusty, and I just wiped the computer clean and did a fresh install of Hardy hoping this would resolve itself, but it hasn't.

The machine I'm discussing is a Dell running Hardy.  It acts as a file and print server on my network.  I had previously only had one printer, an HP Deskjet D1320 attached to it and it was sharing across my network just fine.  I could print to it from my Ubuntu lappy, my wife's Macbook and from a Vista machine. 

I purchased a Brother HL-2040 laser printer and attached it to the Hardy file server and shared it.  At first it was working just fine.  then  one day it stopped and can no longer be accessed across the network. I can print to it just fine from the server itself, but I can't print remotely. And, my HP printer can no longer be accessed either.  I am completely unable to access across the network any printers that are connected to the server.  The other computers can see that they are there, but cannot print to them.  When I look at the printers on my Ubuntu lappy, I see that they are there and available, but the option to print to them is grayed out. 

I found some links to a cups wrapper on Brother's website.  I read that apparently Brother printers are difficult in Linux.  so I tried to install the cups wrapper from there but it refused to install, kept erroring out.  Finally, I came across this one:

[http://packages.ubuntu.com/hardy/i386/brother-cups-wrapper-laser/download](http://packages.ubuntu.com/hardy/i386/brother-cups-wrapper-laser/download)

and I was able to install it,  but it didn't solve my problem.  It didn't appear to make any difference at all.

What I'm really puzzled by is that even if the Brother printer didn't work well with Linux, why would the HP printer be inaccessible as well?  It has always worked perfectly. Does one faulty printer ruin the entire print server?

I really need these printers to share out over the network. What can I do to make them work?

---

### Post by arbulus on 2008-05-08
Bump

---

### Post by arbulus on 2008-05-12
Bump

---

### Post by medic8ted on 2008-05-14
I'm with you, laptop can't find the shared printers on the desktop, all are shared, but Hardy laptop can't see them.

---

### Post by talz13 on 2008-05-14
I would look at the /etc/samba/smb.conf for anything regarding printers and make sure they are still shared correctly.  Don't know why they would suddenly stop working, but if the local machine can print fine and networked ones can't, I'd point my finger at the networking (smb.conf).

---

### Post by arbulus on 2008-05-14
> **talz13 said:**
> I would look at the /etc/samba/smb.conf for anything regarding printers and make sure they are still shared correctly.  Don't know why they would suddenly stop working, but if the local machine can print fine and networked ones can't, I'd point my finger at the networking (smb.conf).

I'll check it out, but I'm curious:  would samba have anything to do with it since I share my printers using CUPS?

---

### Post by arbulus on 2008-05-15
Ok, I've never looked at the printer section in the smb.conf file.  so I'll post my smb conf here and see if anyone can tell me if it looks ok:

```
#
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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = decafenated

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

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
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how nsuccessful authentication attempts are mapped 
# to anonymous connections
map to guest = bad user

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

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

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

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
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
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
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
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[Data]
	writable = yes
	path = /home/dave/Data
	force directory mode = 777
	force create mode = 777
	browsable = yes
	public = yes
	create mode = 777
	available = yes
	directory mode = 777

[Media]
	writable = yes
	path = /home/dave/Media
	force directory mode = 777
	force create mode = 777
	browsable = yes
	public = yes
	create mode = 777
	available = yes
	directory mode = 777
```

---

### Post by talz13 on 2008-05-15
Check out this tutorial:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by arbulus on 2008-05-15
> **talz13 said:**
> Check out this tutorial:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)


I'm completely familiar with that. Like I said, I've been sharing just fine for a year and a half or more. But just recently since I purchased the Brother printer, I can't print from the client machines anymore - to either printer. But I can print on the server itself just fine.

---

### Post by arbulus on 2008-05-15
Ok, so I unplugged the Brother printer, deleted both printers from the server and then restarted. So the ONLY printer that is attached is the old HP. The same HP that I've been using and sharing for over a year.  So I tried to print from other machines and it still will not print. 

To be quite honest, this really makes me angry.  Like I've said, I have used that HP printer alone for well over a year attached to this server and have shared it across my network just fine. Why will no printers share now?  I don't edit the CUPS config file by hand, and I don't share the printers by Samba.  I just go to localhost:631 on the server and configure everything from there. Gutsy just stopped sharing and when I did a clean re-install of Hardy, it won't share either.  what has happened in the past month to make my shared printers inaccessible? This is not user error.  Something happened, maybe after a system update or something like that, but I did not change anything from the way it was before, the printers just stopped sharing. I just don't understand. 

Is there possibly some default block on port 631 in Ubuntu now?  Even when you explicitly tell it to share the printers?  Is there some other thing you have to do now to open port 631?  I really don't understand what else it could be.

---

### Post by talz13 on 2008-05-16
> **arbulus said:**
> Ok, so I unplugged the Brother printer, deleted both printers from the server and then restarted. So the ONLY printer that is attached is the old HP. The same HP that I've been using and sharing for over a year.  So I tried to print from other machines and it still will not print. 

To be quite honest, this really makes me angry.  Like I've said, I have used that HP printer alone for well over a year attached to this server and have shared it across my network just fine. Why will no printers share now?  I don't edit the CUPS config file by hand, and I don't share the printers by Samba.  I just go to localhost:631 on the server and configure everything from there. Gutsy just stopped sharing and when I did a clean re-install of Hardy, it won't share either.  what has happened in the past month to make my shared printers inaccessible? This is not user error.  Something happened, maybe after a system update or something like that, but I did not change anything from the way it was before, the printers just stopped sharing. I just don't understand. 

Is there possibly some default block on port 631 in Ubuntu now?  Even when you explicitly tell it to share the printers?  Is there some other thing you have to do now to open port 631?  I really don't understand what else it could be.

If you want to see if 631 is blocked, do an ```
nmap -p 631 192.168.1.0/24
``` on whatever your IP range is. You'll want to see something like:```
jeff@server:~$ nmap -p 631 192.168.1.0/24

Starting Nmap 4.20 ( http://insecure.org ) at 2008-05-16 08:14 EDT
Interesting ports on router (192.168.1.1):
PORT    STATE  SERVICE
631/tcp closed ipp

Interesting ports on server (192.168.1.5):
PORT    STATE  SERVICE
631/tcp closed ipp

Interesting ports on brotherPrinter (192.168.1.8):
PORT    STATE SERVICE
631/tcp open  ipp

Nmap finished: 256 IP addresses (3 hosts up) scanned in 2.341 seconds
jeff@server:~$
``` where brotherPrinter is my printer, and it has 631/tcp open.

I'm concerned that you said you did a complete reinstall and are still having issues.  Maybe try going back to a clean install of gutsy if it was working in the past just to check it out?

---

### Post by arbulus on 2008-05-16
> **talz13 said:**
> If you want to see if 631 is blocked, do an ```
nmap -p 631 192.168.1.0/24
```

Here's what I got from that:

```
dave@fileserver:~$ nmap -p 631 192.168.1.0/24

Starting Nmap 4.53 ( http://insecure.org ) at 2008-05-16 22:18 EDT
Interesting ports on 192.168.1.1:
PORT    STATE  SERVICE
631/tcp closed ipp

Interesting ports on fileserver (192.168.1.201):
PORT    STATE SERVICE
631/tcp open  ipp

Nmap done: 256 IP addresses (2 hosts up) scanned in 1.704 seconds
```

192.168.1.1 is my router.  192.168.1.201 is the server.  It appears that it's open, so I guess that idea is out. 

> **talz13 said:**
> I'm concerned that you said you did a complete reinstall and are still having issues.  Maybe try going back to a clean install of gutsy if it was working in the past just to check it out?

Yeah, that's why it's so confusing.  It seems like a complete re-install should solve any problems that would be happening if it worked before.  I think I may give a fresh install of Gutsy a try and see what happens.

---

### Post by arbulus on 2008-05-17
Ok, so I wiped the machine clean and did a fresh install of Gutsy.  I disabled updates and I'm running with just the stock base install of Gutsy on the server.

When I first finished the install and shared the printers, I was actually able to print from the computers across the network to both printers.  Everything worked beautifully as it should.  But I wanted to be completely sure.  So I shut the server down, waited a minute, then turned it back on.  Sure enough, after the reboot, the printers no longer work. Neither one of them. I'm right back where I started.

Why on earth would it work perfectly and exactly as it should and then completely stop after a reboot?

I don't know if it helps, but here are my CUPS logs:

Access log:

```
localhost - - [17/May/2008:00:02:58 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes client-error-not-found
localhost - - [17/May/2008:00:03:01 -0400] "POST / HTTP/1.1" 200 1389520 CUPS-Get-PPDs -
localhost - - [17/May/2008:00:03:08 -0400] "POST /admin/ HTTP/1.1" 401 290 CUPS-Add-Modify-Printer successful-ok
localhost - root [17/May/2008:00:03:08 -0400] "POST /admin/ HTTP/1.1" 200 290 CUPS-Add-Modify-Printer successful-ok
localhost - root [17/May/2008:00:03:11 -0400] "POST /admin/ HTTP/1.1" 200 136 Resume-Printer successful-ok
localhost - root [17/May/2008:00:03:11 -0400] "POST /admin/ HTTP/1.1" 200 136 CUPS-Accept-Jobs successful-ok
localhost - - [17/May/2008:00:03:18 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - - [17/May/2008:00:06:25 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:00:06:45 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - - [17/May/2008:00:07:52 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:00:07:56 -0400] "GET /ppd/Deskjet_D1300_series.ppd HTTP/1.1" 200 21126 - -
localhost - - [17/May/2008:00:07:56 -0400] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - - [17/May/2008:00:08:09 -0400] "POST /admin/ HTTP/1.1" 401 170 CUPS-Add-Modify-Printer successful-ok
localhost - root [17/May/2008:00:08:09 -0400] "POST /admin/ HTTP/1.1" 200 170 CUPS-Add-Modify-Printer successful-ok
localhost - - [17/May/2008:00:08:09 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - root [17/May/2008:00:08:09 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - root [17/May/2008:00:08:15 -0400] "PUT /admin/conf/cupsd.conf HTTP/1.1" 201 1643 - -
localhost - - [17/May/2008:00:08:16 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:00:08:16 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:00:08:16 -0400] "GET /ppd/Deskjet_D1300_series.ppd HTTP/1.1" 200 21126 - -
localhost - - [17/May/2008:00:08:16 -0400] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
192.168.1.2 - - [17/May/2008:00:10:28 -0400] "GET /ppd/Deskjet_D1300_series.ppd HTTP/1.1" 200 21126 - -
localhost - - [17/May/2008:00:10:32 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
192.168.1.2 - - [17/May/2008:00:10:32 -0400] "POST /printers/Deskjet_D1300_series HTTP/1.1" 200 45197 Print-Job successful-ok
localhost - - [17/May/2008:00:10:32 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
192.168.1.2 - - [17/May/2008:00:10:32 -0400] "POST /printers/Deskjet_D1300_series HTTP/1.1" 200 251 Get-Job-Attributes successful-ok
localhost - - [17/May/2008:00:10:32 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - - [17/May/2008:00:10:32 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - - [17/May/2008:00:10:32 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:00:10:33 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
192.168.1.2 - - [17/May/2008:00:10:42 -0400] "POST /printers/Deskjet_D1300_series HTTP/1.1" 200 251 Get-Job-Attributes successful-ok
localhost - - [17/May/2008:00:10:46 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
192.168.1.2 - - [17/May/2008:00:10:52 -0400] "POST /printers/Deskjet_D1300_series HTTP/1.1" 200 251 Get-Job-Attributes successful-ok
localhost - - [17/May/2008:00:11:09 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:00:11:10 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - - [17/May/2008:00:11:10 -0400] "POST / HTTP/1.1" 200 1389520 CUPS-Get-PPDs -
localhost - - [17/May/2008:00:11:21 -0400] "POST /admin/ HTTP/1.1" 401 263 CUPS-Add-Modify-Printer successful-ok
localhost - root [17/May/2008:00:11:21 -0400] "POST /admin/ HTTP/1.1" 200 263 CUPS-Add-Modify-Printer successful-ok
localhost - root [17/May/2008:00:11:24 -0400] "POST /admin/ HTTP/1.1" 200 130 Resume-Printer successful-ok
localhost - - [17/May/2008:00:11:24 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - root [17/May/2008:00:11:24 -0400] "POST /admin/ HTTP/1.1" 200 130 CUPS-Accept-Jobs successful-ok
localhost - - [17/May/2008:00:11:25 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - - [17/May/2008:00:11:36 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:00:11:38 -0400] "GET /ppd/HL-2040_series.ppd HTTP/1.1" 200 12503 - -
localhost - - [17/May/2008:00:11:38 -0400] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - - [17/May/2008:00:11:52 -0400] "POST /admin/ HTTP/1.1" 401 130 CUPS-Set-Default successful-ok
localhost - root [17/May/2008:00:11:52 -0400] "POST /admin/ HTTP/1.1" 200 130 CUPS-Set-Default successful-ok
localhost - root [17/May/2008:00:11:52 -0400] "GET /admin/conf/lpoptions HTTP/1.1" 404 0 - -
localhost - root [17/May/2008:00:11:52 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
192.168.1.2 - - [17/May/2008:00:12:12 -0400] "GET /ppd/Deskjet_D1300_series.ppd HTTP/1.1" 200 21126 - -
192.168.1.2 - - [17/May/2008:00:12:26 -0400] "GET /ppd/HL-2040_series.ppd HTTP/1.1" 200 12503 - -
192.168.1.2 - - [17/May/2008:00:12:30 -0400] "POST /printers/HL-2040_series HTTP/1.1" 200 53892 Print-Job successful-ok
192.168.1.2 - - [17/May/2008:00:12:31 -0400] "POST /printers/HL-2040_series HTTP/1.1" 200 245 Get-Job-Attributes successful-ok
192.168.1.2 - - [17/May/2008:00:12:41 -0400] "POST /printers/HL-2040_series HTTP/1.1" 200 245 Get-Job-Attributes successful-ok
localhost - - [17/May/2008:00:13:43 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:00:13:43 -0400] "GET /ppd/HL-2040_series.ppd HTTP/1.1" 200 12503 - -
localhost - - [17/May/2008:00:13:43 -0400] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - - [17/May/2008:00:13:46 -0400] "GET /ppd/Deskjet_D1300_series.ppd HTTP/1.1" 200 21126 - -
localhost - - [17/May/2008:00:13:46 -0400] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - - [17/May/2008:00:13:47 -0400] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
192.168.1.5 - - [17/May/2008:00:23:17 -0400] "GET /ppd/HL-2040_series.ppd HTTP/1.1" 200 12503 - -
192.168.1.5 - - [17/May/2008:00:23:21 -0400] "GET /ppd/Deskjet_D1300_series.ppd HTTP/1.1" 200 21126 - -
192.168.1.5 - - [17/May/2008:00:23:57 -0400] "GET /ppd/HL-2040_series.ppd HTTP/1.1" 200 12503 - -
192.168.1.5 - - [17/May/2008:00:24:01 -0400] "POST /printers/HL-2040_series HTTP/1.1" 200 190501 Print-Job successful-ok
192.168.1.5 - - [17/May/2008:00:24:01 -0400] "POST /printers/HL-2040_series HTTP/1.1" 200 245 Get-Job-Attributes successful-ok
192.168.1.5 - - [17/May/2008:00:24:02 -0400] "POST /printers/HL-2040_series HTTP/1.1" 200 245 Get-Job-Attributes successful-ok
192.168.1.5 - - [17/May/2008:00:24:04 -0400] "POST /printers/HL-2040_series HTTP/1.1" 200 245 Get-Job-Attributes successful-ok
192.168.1.5 - - [17/May/2008:00:24:07 -0400] "POST /printers/HL-2040_series HTTP/1.1" 200 245 Get-Job-Attributes successful-ok
localhost - - [17/May/2008:00:27:47 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:00:27:47 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:00:28:08 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - - [17/May/2008:00:34:01 -0400] "GET / HTTP/1.1" 200 5252 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /cups.css HTTP/1.1" 200 3998 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /favicon.ico HTTP/1.1" 200 3638 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /images/top-left.gif HTTP/1.1" 200 473 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /images/top-middle.gif HTTP/1.1" 200 1144 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /images/top-right.gif HTTP/1.1" 200 121 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /images/tab-left.gif HTTP/1.1" 200 46 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /images/tab-right.gif HTTP/1.1" 200 47 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /images/button-help.gif HTTP/1.1" 200 256 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /images/button-add-class.gif HTTP/1.1" 200 387 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /images/button-add-printer.gif HTTP/1.1" 200 401 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /images/button-manage-classes.gif HTTP/1.1" 200 522 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /images/button-manage-jobs.gif HTTP/1.1" 200 450 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /images/button-manage-printers.gif HTTP/1.1" 200 508 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /images/button-manage-server.gif HTTP/1.1" 200 493 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /images/happy.gif HTTP/1.1" 200 3522 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /images/bottom-left.gif HTTP/1.1" 200 122 - -
localhost - - [17/May/2008:00:34:01 -0400] "GET /images/bottom-right.gif HTTP/1.1" 200 123 - -
localhost - - [17/May/2008:00:34:04 -0400] "GET /admin/ HTTP/1.1" 200 0 - -
localhost - - [17/May/2008:00:34:04 -0400] "POST / HTTP/1.1" 200 107 Get-Subscriptions client-error-not-found
localhost - - [17/May/2008:00:34:04 -0400] "GET /admin/ HTTP/1.1" 200 6032 - -
localhost - - [17/May/2008:00:34:04 -0400] "GET /images/button-find-new-printers.gif HTTP/1.1" 200 509 - -
localhost - - [17/May/2008:00:34:04 -0400] "GET /images/button-edit-configuration-file.gif HTTP/1.1" 200 562 - -
localhost - - [17/May/2008:00:34:04 -0400] "GET /images/button-view-access-log.gif HTTP/1.1" 200 534 - -
localhost - - [17/May/2008:00:34:04 -0400] "GET /images/button-view-error-log.gif HTTP/1.1" 200 473 - -
localhost - - [17/May/2008:00:34:04 -0400] "GET /images/button-view-page-log.gif HTTP/1.1" 200 496 - -
localhost - - [17/May/2008:00:34:04 -0400] "GET /images/button-change-settings.gif HTTP/1.1" 200 521 - -
localhost - - [17/May/2008:00:34:04 -0400] "GET /images/button-add-rss-subscription.gif HTTP/1.1" 200 624 - -
```

Error Log:

```
E [17/May/2008:00:03:03 -0400] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [17/May/2008:00:03:08 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [17/May/2008:00:08:09 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [17/May/2008:00:08:16 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:00:08:16 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:00:08:16 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:00:08:16 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:00:08:16 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:00:08:16 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:00:08:16 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:00:10:32 -0400] [Job 1] pdftops-options: 
E [17/May/2008:00:11:10 -0400] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [17/May/2008:00:11:21 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [17/May/2008:00:11:52 -0400] CUPS-Set-Default: Unauthorized
E [17/May/2008:00:12:31 -0400] [Job 2] pdftops-options: 
E [17/May/2008:00:24:01 -0400] [Job 3] No %%BoundingBox: comment in header!
E [17/May/2008:00:26:55 -0400] DNSServiceRegister failed with error -65537
E [17/May/2008:00:26:55 -0400] DNSServiceRegister failed with error -65537 
```

---

### Post by arbulus on 2008-05-17
So i wanted to try something out of curiosity:

I unplugged the Brother printer but left the HP printer plugged in and did another clean re-install of Gutsy.  I was thinking that perhaps the Brother printer was causing all this problem so I wanted to try to see what would happen if it weren't in the mix. 

Once again when the install was complete, the HP printer worked just fine and I was able to print to it across the network.  But when I rebooted the server, no other machines could see that the HP printer was being shared. Nothing at all has changed in the settings, but it's just as though the printer wasn't being shared.  Nothing can see it.  I can still print to it fine from the server, but no other machines know it's there. 

Once again, my CUPS logs:

Access:

```
localhost - - [17/May/2008:14:06:24 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes client-error-not-found
localhost - - [17/May/2008:14:06:27 -0400] "POST / HTTP/1.1" 200 1389520 CUPS-Get-PPDs -
localhost - - [17/May/2008:14:06:46 -0400] "POST /admin/ HTTP/1.1" 401 290 CUPS-Add-Modify-Printer successful-ok
localhost - root [17/May/2008:14:06:46 -0400] "POST /admin/ HTTP/1.1" 200 290 CUPS-Add-Modify-Printer successful-ok
localhost - root [17/May/2008:14:06:48 -0400] "POST /admin/ HTTP/1.1" 200 136 Resume-Printer successful-ok
localhost - root [17/May/2008:14:06:48 -0400] "POST /admin/ HTTP/1.1" 200 136 CUPS-Accept-Jobs successful-ok
localhost - - [17/May/2008:14:07:02 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - - [17/May/2008:14:08:25 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:14:08:30 -0400] "PUT /admin/conf/cupsd.conf HTTP/1.1" 401 0 - -
localhost - root [17/May/2008:14:08:30 -0400] "PUT /admin/conf/cupsd.conf HTTP/1.1" 201 1643 - -
localhost - - [17/May/2008:14:08:31 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:14:08:31 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
192.168.1.3 - - [17/May/2008:14:09:31 -0400] "GET /ppd/Deskjet_D1300_series.ppd HTTP/1.1" 200 21126 - -
localhost - - [17/May/2008:14:10:29 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:14:10:49 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - - [17/May/2008:14:12:04 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:14:12:06 -0400] "GET /ppd/Deskjet_D1300_series.ppd HTTP/1.1" 200 21126 - -
localhost - - [17/May/2008:14:12:06 -0400] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - - [17/May/2008:14:16:55 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:14:16:56 -0400] "GET /ppd/Deskjet_D1300_series.ppd HTTP/1.1" 200 21126 - -
localhost - - [17/May/2008:14:16:56 -0400] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - - [17/May/2008:14:22:36 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:14:22:46 -0400] "PUT /admin/conf/cupsd.conf HTTP/1.1" 401 0 - -
localhost - root [17/May/2008:14:22:46 -0400] "PUT /admin/conf/cupsd.conf HTTP/1.1" 201 1784 - -
localhost - - [17/May/2008:14:22:47 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:14:22:47 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:14:22:48 -0400] "GET /ppd/Deskjet_D1300_series.ppd HTTP/1.1" 200 21126 - -
localhost - - [17/May/2008:14:22:48 -0400] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - - [17/May/2008:14:22:50 -0400] "POST /admin/ HTTP/1.1" 401 136 CUPS-Delete-Printer successful-ok
localhost - root [17/May/2008:14:22:50 -0400] "POST /admin/ HTTP/1.1" 200 136 CUPS-Delete-Printer successful-ok
localhost - - [17/May/2008:14:22:50 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - root [17/May/2008:14:22:50 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes client-error-not-found
localhost - - [17/May/2008:14:22:50 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - - [17/May/2008:14:23:52 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes client-error-not-found
localhost - - [17/May/2008:14:23:57 -0400] "POST / HTTP/1.1" 200 1389520 CUPS-Get-PPDs -
localhost - - [17/May/2008:14:24:13 -0400] "POST /admin/ HTTP/1.1" 401 290 CUPS-Add-Modify-Printer successful-ok
localhost - root [17/May/2008:14:24:13 -0400] "POST /admin/ HTTP/1.1" 200 290 CUPS-Add-Modify-Printer successful-ok
localhost - - [17/May/2008:14:24:19 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - root [17/May/2008:14:24:19 -0400] "POST /admin/ HTTP/1.1" 200 136 Resume-Printer successful-ok
localhost - - [17/May/2008:14:24:19 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - root [17/May/2008:14:24:19 -0400] "POST /admin/ HTTP/1.1" 200 136 CUPS-Accept-Jobs successful-ok
localhost - - [17/May/2008:14:25:01 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:14:25:02 -0400] "GET /ppd/Deskjet_D1300_series.ppd HTTP/1.1" 200 21126 - -
localhost - - [17/May/2008:14:25:02 -0400] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - - [17/May/2008:14:25:09 -0400] "POST /admin/ HTTP/1.1" 401 21266 CUPS-Add-Modify-Printer successful-ok
localhost - root [17/May/2008:14:25:09 -0400] "POST /admin/ HTTP/1.1" 200 21266 CUPS-Add-Modify-Printer successful-ok
localhost - root [17/May/2008:14:25:09 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:14:25:09 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - root [17/May/2008:14:25:09 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - root [17/May/2008:14:25:09 -0400] "GET /ppd/Deskjet_D1300_series.ppd HTTP/1.1" 200 21130 - -
localhost - root [17/May/2008:14:25:09 -0400] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - root [17/May/2008:14:25:19 -0400] "POST /admin/ HTTP/1.1" 200 170 CUPS-Add-Modify-Printer successful-ok
localhost - root [17/May/2008:14:25:19 -0400] "POST /admin/ HTTP/1.1" 200 168 CUPS-Add-Modify-Printer successful-ok
localhost - - [17/May/2008:14:25:19 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - root [17/May/2008:14:25:19 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:14:25:19 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - root [17/May/2008:14:25:19 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - root [17/May/2008:14:25:19 -0400] "GET /ppd/Deskjet_D1300_series.ppd HTTP/1.1" 200 21130 - -
localhost - root [17/May/2008:14:25:19 -0400] "POST / HTTP/1.1" 200 149 Get-Jobs successful-ok
localhost - root [17/May/2008:14:25:25 -0400] "PUT /admin/conf/cupsd.conf HTTP/1.1" 201 1643 - -
localhost - - [17/May/2008:14:25:26 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:14:25:26 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
192.168.1.3 - - [17/May/2008:14:29:52 -0400] "GET /ppd/Deskjet_D1300_series.ppd HTTP/1.1" 200 21130 - -
192.168.1.3 - - [17/May/2008:14:30:07 -0400] "GET /ppd/Deskjet_D1300_series.ppd HTTP/1.1" 200 21130 - -
192.168.1.3 - - [17/May/2008:14:30:12 -0400] "POST /printers/Deskjet_D1300_series HTTP/1.1" 200 31973 Print-Job successful-ok
localhost - - [17/May/2008:14:30:12 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
192.168.1.3 - - [17/May/2008:14:30:12 -0400] "POST /printers/Deskjet_D1300_series HTTP/1.1" 200 251 Get-Job-Attributes successful-ok
localhost - - [17/May/2008:14:30:12 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - - [17/May/2008:14:30:12 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
192.168.1.3 - - [17/May/2008:14:30:13 -0400] "POST /printers/Deskjet_D1300_series HTTP/1.1" 200 251 Get-Job-Attributes successful-ok
localhost - - [17/May/2008:14:30:13 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - - [17/May/2008:14:30:15 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
192.168.1.3 - - [17/May/2008:14:30:15 -0400] "POST /printers/Deskjet_D1300_series HTTP/1.1" 200 251 Get-Job-Attributes successful-ok
192.168.1.3 - - [17/May/2008:14:30:18 -0400] "POST /printers/Deskjet_D1300_series HTTP/1.1" 200 251 Get-Job-Attributes successful-ok
192.168.1.3 - - [17/May/2008:14:30:22 -0400] "POST /printers/Deskjet_D1300_series HTTP/1.1" 200 251 Get-Job-Attributes successful-ok
localhost - - [17/May/2008:14:30:26 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
192.168.1.3 - - [17/May/2008:14:30:27 -0400] "POST /printers/Deskjet_D1300_series HTTP/1.1" 200 251 Get-Job-Attributes successful-ok
localhost - - [17/May/2008:14:31:09 -0400] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes successful-ok
localhost - - [17/May/2008:14:31:28 -0400] "POST / HTTP/1.1" 200 178 Get-Jobs successful-ok
localhost - - [17/May/2008:14:33:58 -0400] "GET / HTTP/1.1" 200 5252 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /cups.css HTTP/1.1" 200 3998 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /favicon.ico HTTP/1.1" 200 3638 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /images/top-left.gif HTTP/1.1" 200 473 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /images/top-middle.gif HTTP/1.1" 200 1144 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /images/top-right.gif HTTP/1.1" 200 121 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /images/tab-left.gif HTTP/1.1" 200 46 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /images/tab-right.gif HTTP/1.1" 200 47 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /images/button-help.gif HTTP/1.1" 200 256 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /images/button-add-class.gif HTTP/1.1" 200 387 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /images/button-add-printer.gif HTTP/1.1" 200 401 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /images/button-manage-classes.gif HTTP/1.1" 200 522 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /images/button-manage-jobs.gif HTTP/1.1" 200 450 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /images/button-manage-printers.gif HTTP/1.1" 200 508 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /images/button-manage-server.gif HTTP/1.1" 200 493 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /images/happy.gif HTTP/1.1" 200 3522 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /images/bottom-left.gif HTTP/1.1" 200 122 - -
localhost - - [17/May/2008:14:33:59 -0400] "GET /images/bottom-right.gif HTTP/1.1" 200 123 - -
localhost - - [17/May/2008:14:34:00 -0400] "GET /admin/ HTTP/1.1" 200 0 - -
localhost - - [17/May/2008:14:34:01 -0400] "POST / HTTP/1.1" 200 107 Get-Subscriptions client-error-not-found
localhost - - [17/May/2008:14:34:00 -0400] "GET /admin/ HTTP/1.1" 200 6032 - -
localhost - - [17/May/2008:14:34:01 -0400] "GET /images/button-find-new-printers.gif HTTP/1.1" 200 509 - -
localhost - - [17/May/2008:14:34:01 -0400] "GET /images/button-edit-configuration-file.gif HTTP/1.1" 200 562 - -
localhost - - [17/May/2008:14:34:01 -0400] "GET /images/button-view-access-log.gif HTTP/1.1" 200 534 - -
localhost - - [17/May/2008:14:34:01 -0400] "GET /images/button-view-error-log.gif HTTP/1.1" 200 473 - -
localhost - - [17/May/2008:14:34:01 -0400] "GET /images/button-view-page-log.gif HTTP/1.1" 200 496 - -
localhost - - [17/May/2008:14:34:01 -0400] "GET /images/button-change-settings.gif HTTP/1.1" 200 521 - -
localhost - - [17/May/2008:14:34:01 -0400] "GET /images/button-add-rss-subscription.gif HTTP/1.1" 200 624 - -
localhost - - [17/May/2008:14:34:02 -0400] "GET /admin/log/access_log HTTP/1.1" 200 10854 - -
localhost - - [17/May/2008:14:34:11 -0400] "GET /admin/log/error_log HTTP/1.1" 200 2116 - -
```


Error:
```

E [17/May/2008:14:06:29 -0400] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [17/May/2008:14:06:46 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [17/May/2008:14:08:31 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:08:31 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:08:31 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:08:31 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:09:49 -0400] DNSServiceRegister failed with error -65537
E [17/May/2008:14:22:47 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:22:47 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:22:47 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:22:47 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:22:48 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:22:48 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:22:48 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:22:50 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:22:50 -0400] CUPS-Delete-Printer: Unauthorized
E [17/May/2008:14:23:57 -0400] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [17/May/2008:14:24:13 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [17/May/2008:14:25:09 -0400] CUPS-Add-Modify-Printer: Unauthorized
E [17/May/2008:14:25:26 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:25:26 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:25:26 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:25:26 -0400] cupsdAuthorize: Local authentication certificate not found!
E [17/May/2008:14:30:29 -0400] DNSServiceRegister failed with error -65537
```


Maybe I should try going back to Feisty?

---

### Post by arbulus on 2008-05-17
So I just decided to give it a shot and I did a clean install of Feisty. 

It works like a dream.  I've rebooted and shut down the server several times and everything is working as it should be. I can print from across the network to both printers.

So apparently the new printing system that's used in Gutsy and Hardy is a problem.

---

### Post by persev on 2008-05-19
> **talz13 said:**
> Check out this tutorial:

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Still doesn't work from my wifes xp laptop.

---

### Post by persev on 2008-05-19
Found my problem, I had to open port 631 on my router.

---

### Post by arbulus on 2008-05-23
So I rescind what I said.  They no longer work.

I am so angry about this.  When I finally got Feisty working on the server, I rebooted the server multiple times, I rebooted my clients multiple times and each time I would try to print and it would be successful. I wanted to be sure that it worked and would continue to work even with reboots. And it did. But now, **OUT OF NOWHERE**, once again, the printing no longer works across the network.  I haven't changed a single thing at all in anyway at all on the server since I got it working.  And it was working brilliantly, just as it should, and did so for several days. 

Why would it just randomly stop working?  Why can I no longer print across the network?  Why did this work for me for several years just fine and now won't work at all, especially when I am not doing anything differently than I ever have?  I even went back to Feisty, a version that I **KNOW** for a fact worked perfectly with the printing.  Why on earth would the printers just stop functioning without any human intervention?  I disabled updates on the server, so nothing at all has changed!

Here are my CUPS logs:

Error Log:
```

E [23/May/2008:19:15:44 -0400] CUPS-Set-Default: Unauthorized
E [23/May/2008:19:15:49 -0400] CUPS-Set-Default: Unauthorized
E [23/May/2008:19:15:49 -0400] cupsdCloseClient: Error in the push function.
E [23/May/2008:19:15:53 -0400] CUPS-Set-Default: Unauthorized
```

Access Log:

```
fileserver - - [23/May/2008:19:15:11 -0400] "GET /admin/ HTTP/1.1" 200 0 - -
localhost - - [23/May/2008:19:15:11 -0400] "POST / HTTP/1.1" 200 2191 CUPS-Get-Devices -
fileserver - - [23/May/2008:19:15:13 -0400] "GET /images/button-add-this-printer.gif HTTP/1.1" 200 577 - -
fileserver - - [23/May/2008:19:15:11 -0400] "GET /admin/ HTTP/1.1" 200 5961 - -
fileserver - - [23/May/2008:19:15:14 -0400] "GET /images/button-edit-configuration-file.gif HTTP/1.1" 200 699 - -
fileserver - - [23/May/2008:19:15:14 -0400] "GET /images/button-view-access-log.gif HTTP/1.1" 200 638 - -
fileserver - - [23/May/2008:19:15:14 -0400] "GET /images/button-view-error-log.gif HTTP/1.1" 200 554 - -
fileserver - - [23/May/2008:19:15:14 -0400] "GET /images/button-view-page-log.gif HTTP/1.1" 200 590 - -
fileserver - - [23/May/2008:19:15:14 -0400] "GET /images/button-change-settings.gif HTTP/1.1" 200 615 - -
fileserver - - [23/May/2008:19:15:18 -0400] "GET /classes/ HTTP/1.1" 200 0 - -
localhost - - [23/May/2008:19:15:18 -0400] "POST / HTTP/1.1" 200 417 CUPS-Get-Classes successful-ok
fileserver - - [23/May/2008:19:15:18 -0400] "GET /classes/ HTTP/1.1" 200 3626 - -
fileserver - - [23/May/2008:19:15:19 -0400] "GET /admin HTTP/1.1" 200 0 - -
localhost - - [23/May/2008:19:15:19 -0400] "POST / HTTP/1.1" 200 2191 CUPS-Get-Devices -
fileserver - - [23/May/2008:19:15:19 -0400] "GET /admin HTTP/1.1" 200 5961 - -
fileserver - - [23/May/2008:19:15:21 -0400] "GET /admin HTTP/1.1" 200 0 - -
localhost - - [23/May/2008:19:15:21 -0400] "POST / HTTP/1.1" 200 2191 CUPS-Get-Devices -
fileserver - - [23/May/2008:19:15:21 -0400] "GET /admin HTTP/1.1" 200 5961 - -
fileserver - - [23/May/2008:19:15:23 -0400] "GET /printers/ HTTP/1.1" 200 0 - -
fileserver - - [23/May/2008:19:15:23 -0400] "GET /printers/ HTTP/1.1" 200 8994 - -
fileserver - - [23/May/2008:19:15:44 -0400] "GET /admin/?op=set-as-default&printer_name=Brother-HL-2040 HTTP/1.1" 200 0 - -
localhost - - [23/May/2008:19:15:44 -0400] "POST /admin/ HTTP/1.1" 401 131 CUPS-Set-Default successful-ok
fileserver - - [23/May/2008:19:15:44 -0400] "GET /admin/?op=set-as-default&printer_name=Brother-HL-2040 HTTP/1.1" 426 0 - -
fileserver - - [23/May/2008:19:15:44 -0400] "GET /admin/?op=set-as-default&printer_name=Brother-HL-2040 HTTP/1.1" 200 0 - -
fileserver - - [23/May/2008:19:15:49 -0400] "GET /admin/?op=set-as-default&printer_name=Brother-HL-2040 HTTP/1.1" 200 0 - -
localhost - - [23/May/2008:19:15:49 -0400] "POST /admin/ HTTP/1.1" 401 131 CUPS-Set-Default successful-ok
fileserver - - [23/May/2008:19:15:49 -0400] "GET /admin/?op=set-as-default&printer_name=Brother-HL-2040 HTTP/1.1" 401 0 - -
fileserver - - [23/May/2008:19:15:49 -0400] "GET /admin/?op=set-as-default&printer_name=Brother-HL-2040 HTTP/1.1" 200 0 - -
fileserver - dave [23/May/2008:19:15:53 -0400] "GET /admin/?op=set-as-default&printer_name=Brother-HL-2040 HTTP/1.1" 200 0 - -
localhost - - [23/May/2008:19:15:53 -0400] "POST /admin/ HTTP/1.1" 401 131 CUPS-Set-Default successful-ok
localhost - dave [23/May/2008:19:15:53 -0400] "POST /admin/ HTTP/1.1" 200 131 CUPS-Set-Default successful-ok
fileserver - - [23/May/2008:19:15:53 -0400] "GET /cups.css HTTP/1.1" 200 3660 - -
fileserver - dave [23/May/2008:19:15:53 -0400] "GET /admin/?op=set-as-default&printer_name=Brother-HL-2040 HTTP/1.1" 200 3669 - -
fileserver - - [23/May/2008:19:15:53 -0400] "GET /favicon.ico HTTP/1.1" 200 3638 - -
fileserver - - [23/May/2008:19:15:53 -0400] "GET /images/top-left.gif HTTP/1.1" 200 473 - -
fileserver - - [23/May/2008:19:15:53 -0400] "GET /images/top-middle.gif HTTP/1.1" 200 1144 - -
fileserver - - [23/May/2008:19:15:53 -0400] "GET /images/top-right.gif HTTP/1.1" 200 121 - -
fileserver - - [23/May/2008:19:15:53 -0400] "GET /images/tab-left.gif HTTP/1.1" 200 46 - -
fileserver - - [23/May/2008:19:15:53 -0400] "GET /images/tab-right.gif HTTP/1.1" 200 47 - -
fileserver - - [23/May/2008:19:15:53 -0400] "GET /images/bottom-left.gif HTTP/1.1" 200 122 - -
fileserver - - [23/May/2008:19:15:53 -0400] "GET /images/bottom-right.gif HTTP/1.1" 200 123 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /printers/ HTTP/1.1" 200 0 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /printers/ HTTP/1.1" 200 9012 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /images/button-clear.gif HTTP/1.1" 200 359 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /images/button-search.gif HTTP/1.1" 200 410 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /images/button-sort-descending.gif HTTP/1.1" 200 723 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /images/printer-idle.gif HTTP/1.1" 200 2546 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /images/button-print-test-page.gif HTTP/1.1" 200 564 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /images/button-stop-printer.gif HTTP/1.1" 200 501 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /images/button-reject-jobs.gif HTTP/1.1" 200 509 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /images/button-move-jobs.gif HTTP/1.1" 200 574 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /images/button-cancel-all-jobs.gif HTTP/1.1" 200 568 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /images/button-unpublish-printer.gif HTTP/1.1" 200 594 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /images/button-modify-printer.gif HTTP/1.1" 200 559 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /images/button-set-printer-options.gif HTTP/1.1" 200 649 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /images/button-delete-printer.gif HTTP/1.1" 200 508 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /images/button-set-as-default.gif HTTP/1.1" 200 585 - -
fileserver - - [23/May/2008:19:15:56 -0400] "GET /images/button-set-allowed-users.gif HTTP/1.1" 200 673 - -
fileserver - - [23/May/2008:19:16:06 -0400] "GET /admin HTTP/1.1" 200 0 - -
localhost - - [23/May/2008:19:16:06 -0400] "POST / HTTP/1.1" 200 2191 CUPS-Get-Devices -
fileserver - - [23/May/2008:19:16:06 -0400] "GET /admin HTTP/1.1" 200 5961 - -
fileserver - - [23/May/2008:19:16:07 -0400] "GET /images/button-add-printer.gif HTTP/1.1" 200 487 - -
fileserver - - [23/May/2008:19:16:07 -0400] "GET /images/button-manage-printers.gif HTTP/1.1" 200 610 - -
fileserver - - [23/May/2008:19:16:07 -0400] "GET /images/button-add-class.gif HTTP/1.1" 200 484 - -
fileserver - - [23/May/2008:19:16:07 -0400] "GET /images/button-add-this-printer.gif HTTP/1.1" 200 577 - -
fileserver - - [23/May/2008:19:16:07 -0400] "GET /images/button-manage-classes.gif HTTP/1.1" 200 619 - -
fileserver - - [23/May/2008:19:16:07 -0400] "GET /images/button-manage-jobs.gif HTTP/1.1" 200 556 - -
fileserver - - [23/May/2008:19:16:07 -0400] "GET /images/button-edit-configuration-file.gif HTTP/1.1" 200 699 - -
fileserver - - [23/May/2008:19:16:07 -0400] "GET /images/button-view-access-log.gif HTTP/1.1" 200 638 - -
fileserver - - [23/May/2008:19:16:07 -0400] "GET /images/button-view-error-log.gif HTTP/1.1" 200 554 - -
fileserver - - [23/May/2008:19:16:07 -0400] "GET /images/button-view-page-log.gif HTTP/1.1" 200 590 - -
fileserver - - [23/May/2008:19:16:07 -0400] "GET /images/button-change-settings.gif HTTP/1.1" 200 615 - -
fileserver - - [23/May/2008:19:16:12 -0400] "GET / HTTP/1.1" 200 5725 - -
fileserver - - [23/May/2008:19:16:12 -0400] "GET /images/button-help.gif HTTP/1.1" 200 327 - -
fileserver - - [23/May/2008:19:16:12 -0400] "GET /images/button-manage-server.gif HTTP/1.1" 200 599 - -
fileserver - - [23/May/2008:19:16:12 -0400] "GET /images/happy.gif HTTP/1.1" 200 3522 - -
fileserver - - [23/May/2008:19:16:12 -0400] "GET /images/esp-logo.gif HTTP/1.1" 200 2529 - -
fileserver - - [23/May/2008:19:53:54 -0400] "GET /admin/ HTTP/1.1" 200 0 - -
localhost - - [23/May/2008:19:53:54 -0400] "POST / HTTP/1.1" 200 2191 CUPS-Get-Devices -
fileserver - - [23/May/2008:19:53:54 -0400] "GET /admin/ HTTP/1.1" 200 5961 - -
fileserver - - [23/May/2008:19:54:00 -0400] "GET /admin/log/error_log HTTP/1.1" 200 263 - -
fileserver - - [23/May/2008:19:54:10 -0400] "GET /admin/log/access_log HTTP/1.1" 200 7961 - -
fileserver - - [23/May/2008:19:58:08 -0400] "GET /admin/log/error_log HTTP/1.1" 304 0 - -

```

---

### Post by nix4me on 2008-05-23
Im having CUPS issues also.  i had to resort to samba.  CUPS printer sharing in Ubuntu 8.04 is broke in my opinion.  I filed a bug but it is being ignored.

nix4me

---

### Post by arbulus on 2008-05-23
> **nix4me said:**
> Im having CUPS issues also.  i had to resort to samba.  CUPS printer sharing in Ubuntu 8.04 is broke in my opinion.  I filed a bug but it is being ignored.

nix4me

I agree.  Printing in Hardy is definitely broken.  I'd say the same thing about Gutsy as well.  It doesn't make sense why the bug would be ignored, it seems to me that printing would be a pretty high priority. 

How does one go about sharing by Samba?  I've never tried that.

---

### Post by arbulus on 2008-05-24
> **nix4me said:**
> Im having CUPS issues also.  i had to resort to samba.  CUPS printer sharing in Ubuntu 8.04 is broke in my opinion.  I filed a bug but it is being ignored.

nix4me

I just thought of something.  Can you give me a link to your bug?  I'll go to launchpad and comment on it and also give a link to this thread so people can see it.  Maybe it'll get some more attention.

---

### Post by arbulus on 2008-05-26
So I've pretty much given up on this.  I just wiped the server clean and installed openSUSE and everything works now just as it should with no problems at all.  I have to be able to print across my network and these problems have really been driving me up a wall.  So I just moved on.  

I made a comment on a printer bug over at launchpad and gave a link back here.  Hopefully it will help.

And thanks everyone for your help.

---

