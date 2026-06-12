---
title: "Gutsy network printing again"
date: 2007-12-31
forum: General Help
---

### Post by iitywygms on 2007-12-31
I have been searching for some time but can't seem to fix this.
I have Gutsy on my laptop and desktop.  All the latest updates.  I had been able to print from my laptop to the printer connected to my desktop until recently.  I am not sure what has changed or exactly when the printer disappeared from my laptop.
I have enabled sharing on the printer from my desktop computer.  I can print from the desktop no problem.  
Problem is I can't see it anymore with my laptop.  I go here [https://localhost:631/](https://localhost:631/) -cant see it.
I try setting it up using the printer configuration tool, still no go.
I can share files between the two computers.  I even have remote desktop working.
Any ideas as to why I cant share it with my laptop anymore?
It is an hp deskjet 3740.

Thanks

---

### Post by akudewan on 2007-12-31
can you see the printer shared in /etc/samba/smb.conf ?

---

### Post by iitywygms on 2007-12-31
> **akudewan said:**
> can you see the printer shared in /etc/samba/smb.conf ?

Not sure what you mean, here is that file minus the top bs.

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

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

# Put a capping on the size of the log files (in Kb).
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
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

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
;   valid users = %S

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

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
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
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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

---

### Post by akudewan on 2007-12-31
hmm...there's this one line
```

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
; load printers = yes

```

Try removing the semicolon from there. Make a backup of the file before making any changes.
```

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup

```

I don't know if it'll work, just a shot in the dark...Hopefully someone who has experience with this can help you out.

---

### Post by iitywygms on 2007-12-31
> **akudewan said:**
> hmm...there's this one line
```

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
; load printers = yes

```

Try removing the semicolon from there. Make a backup of the file before making any changes.
```

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup

```

I don't know if it'll work, just a shot in the dark...Hopefully someone who has experience with this can help you out.

Okay tried that.  The printer did not show up automatically like it did in the past.  It was 'seen' if I tried installing it thru printer configuration as a windows samba computer.  
After I installed it using that method I tried printing a test page and nothing happened.  I also looked on my desktop to see if any jobs were active and none showed up.
Any other suggestions?

Thanks

---

### Post by qhaz on 2008-01-01
I have exactly the same problem as iitywygms.  Ubuntu (Gutsy) on both my desktop and laptop.  Never had problems printing from my laptop before until recently when all of a sudden my printer does not even appear on my laptop where previously it was always detected without any need to configure a thing.  My printer is a Samsung ML-1710.
I have followed the suggestions here . . . but alas I'm in the same boat as iitywygms.
Wonder if anyone out there is able to shed some light on this one?

---

### Post by qhaz on 2008-01-01
I just noticed iitywygms has ubuntu on both laptop and desktop.  You shouldn't need to touch any smb conf files here as smb stuff would only be necessary if you had a windo$e OS on oned end.  Samba provides the means to interface Linux and Windoze.

---

### Post by iitywygms on 2008-01-01
bump for some help.

---

### Post by iitywygms on 2008-01-02
anyone?

---

### Post by akudewan on 2008-01-03
I read your first post again. You say that you can't see your printer from localhost:631. You can see it here from the desktop, right ?

In the Administration tab of localhost:631, there are some server settings that say: 
Show printers shared by other systems
Share published printers connected to this system
         Allow printing from the Internet
Allow remote administration
...and so on...

You could try changing these...

Again, just a suggestion. I wonder why nobody else is replying...

---

### Post by lordmyth on 2008-01-03
Just a guess, i had the same problem and I just restarted the cupsys service:
```
sudo /etc/init.d/cupsys restart
```

---

### Post by iitywygms on 2008-01-03
> **akudewan said:**
> I read your first post again. You say that you can't see your printer from localhost:631. You can see it here from the desktop, right ?

In the Administration tab of localhost:631, there are some server settings that say: 
Show printers shared by other systems
Share published printers connected to this system
         Allow printing from the Internet
Allow remote administration
...and so on...

You could try changing these...

Again, just a suggestion. I wonder why nobody else is replying...

If I go to localhost:631 from the desktop, I can access all of those settings for my printer.  I have tried all combinations.  Nothing makes it visible from my laptop.

It is odd that I can go to localhost:631 from the desktop and see it, but if I go to the same place from my laptop it is not there.

Am I not going to the same place?  I am not even sure where localhost:631 is so I am not sure what I am changing?

Help!

---

### Post by iitywygms on 2008-01-03
> **lordmyth said:**
> Just a guess, i had the same problem and I just restarted the cupsys service:
```
sudo /etc/init.d/cupsys restart
```


Worked!!! Thank you thank you thank you.
Wonder why????
Oh well, fixed....................

---

### Post by qhaz on 2008-01-03
> **lordmyth said:**
> Just a guess, i had the same problem and I just restarted the cupsys service:
```
sudo /etc/init.d/cupsys restart
```

Well done lordmyth!  Thanks heaps.  I've been wrestling with this for days!  Thanks.

---

### Post by lordmyth on 2008-01-04
still not a real fix though...

---

### Post by akudewan on 2008-01-04
LOL!!!! That was it??!! I feel disgusted, and yet I feel like laughing...

---

