---
title: "can not access the samba share from ubuntu on Windows"
date: 2015-02-10
forum: General Help
---

### Post by saad_khan2 on 2015-02-10
Hello everyone !

I searched ALLOVER and still could not figure this out. I have ran samba and a samba share before and used it succesfully (off a raspi)

So the task is simple. Trying to share my RAID1 setup over the network as a NAS. I just want to use a samba share that doesnt ask for any username and password. On Windows, it says
that permission denied, even though i am sure i set it to 0775 and that anyone could access. Even on ubuntu when i try to click on the share i get the same error. I get this error on ubuntu 

"mount: only root can mount //servername/sharename on /media/saad/NetworkArray/NetworkArray/" - Why is this happening when i am the admin ? (this is on 14.04 LTS)

On windows i get the permission denied error. Again,all i want is to be able to access the share without logging in or anything. Here is my SMB.CONF as well :

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

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = network

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = yes

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
;    passdb backend = tdbsam

    obey pam restrictions = yes

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
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;    usershare max shares = 100

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
[profiles]
   comment = Users profiles
   path = /home/samba/profiles
   guest ok = no
   browseable = no
   create mask = 0600
;  directory mask = 0700

[network array]
    comment = NetworkArray
    browsable = yes
    path = /media/saad/NetworkArray/
    gues ok = yes
    read only = no
    create mask = 0775
[shared]
path = "/media/saad/NetworkArray/"


# Windows clients look for this share name as a source of downloadable
# printer drivers
```



So what do you guys think i can change to fix it ?

Thanks !

---

### Post by TheFu on 2015-02-10
Some things aren't clear to me.  What does r-pi have to do with THIS issue?
Which OS is hosting the storage?
Which OS is trying to access the storage?
Have you loaded the CIFS client packages on the clients?  /etc/samba/smb.conf has NOTHING to do with client-side access.

The output from df -h would be handy as would the ls -al for the top of the mounted RAID location. Please.

---

### Post by saad_khan2 on 2015-02-10
I only said RPI because ive implemented a samba share before without no issues
Ubuntu 14.04 is storage
Windows 7 is trying to access storage
I have installed CIFS-UTILS

Here it is :
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        23G  4.7G   18G  22% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.8G  4.0K  3.8G   1% /dev
tmpfs           770M  1.4M  768M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.8G  160K  3.8G   1% /run/shm
none            100M   36K  100M   1% /run/user
/dev/md0        1.8T  284G  1.5T  17% /media/saad/NetworkArray

---

### Post by TheFu on 2015-02-11
**ls -al /media/saad/NetworkArray **
[https://wiki.samba.org/index.php/Public_Samba_Server](https://wiki.samba.org/index.php/Public_Samba_Server) has helpful instructions.

This is yours:
```

[network array]
    comment = NetworkArray
    browsable = yes
    path = /media/saad/NetworkArray/
    gues ok = yes
    read only = no
    create mask = 0775
[shared]
path = "/media/saad/NetworkArray/"
```

Appears to me that you are missing a 't' (details matter) and that the [shared] stanza isn't needed/wanted at all.  Linux file permissions could get in the way - can't tell since those haven't been provided. We've all been burned by a missing character here and there.
    ```
guest ok = yes
``` is what you want for that 1 line (still need most of that stanza).

---

### Post by Morbius1 on 2015-02-11
It looks like you have another problem. The only user that will get to NetworkArray is saad because of the way the system sets an access contol list on /media/saad.

Since this is a guest accessible share one way around this is to make the remote user appear to be saad - at least for this share:
> [network array]
    comment = NetworkArray
    browsable = yes
    path = /media/saad/NetworkArray/
    [COLOR=#0000cd]**guest ok = yes**[/COLOR]
    [COLOR=#0000cd]**force user = saad**[/COLOR]
    read only = no
    create mask = 0775
And don't forget to restart samba:
```
sudo service smbd restart
```

---

### Post by TheFu on 2015-02-11
Ah ... the damn /media mounts.  I hate those. Never use those myself.  What happens when they decide to move them again in the next release back under /var somewhere (joking, don't nkow of any plans for that)?   Plus /media screams gvfs to me. In my mind, /media is for temporary mounts like for USB drives - never for NFS or DAS. Those belong  elsewhere.  I like the /D/ idea; short and no confusion over what it is.

---

### Post by saad_khan2 on 2015-02-11
> **Morbius1 said:**
> It looks like you have another problem. The only user that will get to NetworkArray is saad because of the way the system sets an access contol list on /media/saad.

Since this is a guest accessible share one way around this is to make the remote user appear to be saad - at least for this share:

And don't forget to restart samba:
```
sudo service smbd restart
```

Tried this whole thing and im still getting the same error on windows 

[IMG]http://i62.tinypic.com/noy1qw.jpg[/IMG]

---

### Post by TheFu on 2015-02-11
Try using the ip address to remove DNS issues.
I'd remove the spaces from the name "network array" too in the smb.conf file.

---

### Post by saad_khan2 on 2015-02-11
Same error.

I think i will need to re-do the SMB file. Something is  up with the access issue

---

### Post by TheFu on 2015-02-11
Things I do.
a) hostname and windows name match 100%, exactly.  all lowercase.
b) mount the real storage somewhere that it wouldn't be mounted automatically by nautilus.
c) No spaces in the directory names or share names. Spaces cause issues in strange ways sometimes.
d) I setup /etc/hosts for the clients and server so they can ping each other
e) use **testparm** to see of a client can "see" the storage. Doesn't help with Windows clients
f) either use the default workgroup name or ensure every machine is in the same workgroup, case sensitive
g) verify that the machines are on the same subnet.

So clearly, these are not "must have to work" ideas, just things I do to avoid problems.
I actually haven't setup guest-allowed CIFS in about a decade. There are posts here with simple smb.conf files that work on 14.04 systems. 

BTW, you never posted the **ls -al** for the mount/share location.

---

### Post by saad_khan2 on 2015-02-11
I tried to do this via putty...and it isnt pulling up ls -al correctly.

Here is the out put of testparm :

saad@NAS1:/$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[NetworkArray]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions


[global]
        workgroup = NETWORK
        server string = %h server (Samba, Ubuntu)
        server role = standalone server
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        username map = /etc/samba/smbusers
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        idmap config * : backend = tdb
        guest ok = Yes


[NetworkArray]
        comment = NetworkArray
        path = /media/saad/NetworkArray/
        force user = saad
        read only = No
        create mask = 0775

---

### Post by saad_khan2 on 2015-02-11
double post. sorry

---

