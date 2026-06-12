---
title: "Sharing Ubuntu directory across to Windows on home network"
date: 2021-11-11
forum: General Help
---

### Post by edstevens on 2021-11-11
I have a laptop running Ubuntu 16.04 LTS and would like to share directories on it with my Windows 10 laptop, both on my home network.  I followed as best I could the instructions [here]("https://www.answertopia.com/ubuntu/sharing-files-between-ubuntu-and-windows-systems-with-samba/").  Everything appears to have been done on the Ubuntu side, but when I open Network from Windows Explorer, it only lists the Windows machines on the network.  Appears to not be recognizing the Ubuntu machine.  So it appears I will need some step-by-step hand-holding diagnostics here.

For openers, the Windows machine is configured with the default workgroup of WORKGROUP.

Here's my /etc/samba/smb.conf file.  The 'eddocuments' section at the end is my addition, per my understanding of the instructions at the page linked above.

```
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

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
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d

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
   server role = standalone server

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de>
 for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\
n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

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
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d
 /var/lib/samba -s /bin/false %u

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
   usershare allow guests = yes

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
[eddocuments]
  comment = share ed documents
  path = /home/ed/Documents
  browseable = Yes
  public = yes
  writeable = yes













```

---

### Post by TheFu on 2021-11-11
16.04 support ended last April.
Please move to a supported release.

As for samba, please post **testparm -s** output.
Thanks for using code-tags.

Generally, it is a really bad idea to share directories under any user's HOME.  Just use the 
[homes] stanza to allow the userid who should have access to those files the access.  For multiple users to have access, always, always, create a shared directory outside /home/.
There are many threads here with example smb.conf stanzas for [homes]. If you follow those and have an issue, perhaps you didn't create a new entry in the smbpasswd file for the userid(s)?

And Win10 as a client needs different overall settings. In MSFT's efforts to make more secure file sharing, they changed some defaults both on their clients and their servers in early 2020.  By running Ubuntu 20.04, you'll have a version of samba that needs only a few config lines to work well with Win10. Win7 and older aren't supported, though they do work with proper settings.

---

### Post by ajgreeny on 2021-11-11
Ubuntu 16.04 is now out of support so if you have not signed up to the extended support available for personal use, offering security support until 2026, your first move should be to move to a fully supported version; I would recommend 20.04 at the moment.

See [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm) for the details.

Regrettably I can not help with samba and folder sharing with Windows as I have no Windows OS with which to share anything.

---

### Post by dragonfly41 on 2021-11-11
Indeed you can use samba but I have not used it.. 
Instead I use a rough and ready approach. I have created a small ntfs partition in my Windows internal drive and when I am in Ubuntu I just mount it and place files in a directory in this small partition to share between Windows and Ubuntu.
Moreover I can install a cross platform note manager such as CherryTree in both Windows 10 and Ubuntu 20.04 (which is in an external SSD) and share notes between the two OS. That is, using CherryTree extension *.ctd.
Another ploy is to use a free Dropbox account for sharing files.

---

### Post by edstevens on 2021-11-12
> **TheFu said:**
> 16.04 support ended last April.
Please move to a supported release.

Noted.  I tried once before and had issues (don't remember the method or the issues) so set it aside.  I'll take that up with my next thread.


> As for samba, please post **testparm -s** output.


```
root@ed-Gazelle-00:/home/ed# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[eddocuments]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[eddocuments]
    comment = share ed documents
    path = /home/ed/Documents
    read only = No
    guest ok = Yes


```






> Generally, it is a really bad idea to share directories under any user's HOME.  Just use the 
[homes] stanza to allow the userid who should have access to those files the access.  For multiple users to have access, always, always, create a shared directory outside /home/.
In this case, there will not be multiple users. Just me, with two machines, on my home network.
Are you saying I should drop the [eddocuments] stanza and just un-comment the 'valid users' line in the [homes] stanza?  If so, should I also change the default value of '%S'?  To what?

> There are many threads here with example smb.conf stanzas for [homes]. If you follow those and have an issue, perhaps you didn't create a new entry in the smbpasswd file for the userid(s)?  
And Win10 as a client needs different overall settings. In MSFT's efforts to make more secure file sharing, they changed some defaults both on their clients and their servers in early 2020.  By running Ubuntu 20.04, you'll have a version of samba that needs only a few config lines to work well with Win10. Win7 and older aren't supported, though they do work with proper settings.

ok. Let's make sure everything on the linux side is correct, then we'll tackle the windows side.

---

### Post by TheFu on 2021-11-12
I think you missed the main point.

Step 1: Install 20.04.
Thinks related to samba have changed, so you need to move to that release and only then try to get it working.  You don't want to fight with this multiple times, right?

---

### Post by Morbius1 on 2021-11-13
On the Win10 machine open explorer ( file manager ) and in the location bar enter:
```
\\ed-Gazelle-00.local
```
Or if you want to get direct access to the shared folder:
```
\\ed-Gazelle-00.local\eddocuments
```

You can then "Pin to Quick access" in explorer so you don't have to go through this again.

---

### Post by edstevens on 2021-11-14
> **TheFu said:**
> I think you missed the main point.

Step 1: Install 20.04.
Thinks related to samba have changed, so you need to move to that release and only then try to get it working.  You don't want to fight with this multiple times, right?

ok. Point taken.  I'll pursue that, then get back.

---

