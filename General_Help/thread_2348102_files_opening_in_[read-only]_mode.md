---
title: "files opening in [read-only] mode"
date: 2016-12-31
forum: General Help
---

### Post by rebeltaz on 2016-12-31
I have a laptop and a desktop connected to my network. From my laptop, I downloaded a file to the desktop's harddrive. I can open the file from my laptop and do anything I want with it, but if I open that same file from the desktop, it will only open in [read-only] mode. I looked at the properties and while the owner and group was set to derek (me) and with read-write access, the group and others access was set to read-only. I changed those to read-write, but it still only opens in [read-only] mode from the desktop. Furthermore, if I modify the file (it's a .7z archive) from the laptop, the permissions are set back to read-only for group and others. Can someone explain this to me, please?

This is what the ls -l listing looks like (before modifying the archive):

-rw-rw-rw- 1 derek derek 1448969266 Dec 21  2014 filename.rar

After modifying the archive it reads:

-rwxr--r-- 1 derek derek 1448969266 Dec 31 12:52 filename.rar

---

### Post by cariboo on 2016-12-31
Moved to General Help.

---

### Post by TheFu on 2016-12-31
Exactly how are the desktop and laptop connected?  If through samba/cifs, then permissions don't really matter. The samba settings override those.
If through NFS (which is the native mode for Unix systems), then normal ownership, groups, and permissions apply, including ACLs.  

There is something called the **umask**. This is a default mask for directories and file permissions. It is like a netmask. 
```
$ umask 
0002

``` This means that write permissions are removed for "other."  On systems used in corporate environments, it is commonly set to 0027, so "other" cannot see anything and the group doesn't have write.

ACLs can override any permissions.  Use **getfacl** to see them.

I suspect the difference is between the umask and samba settings.

---

### Post by Keith_Helms on 2016-12-31
A little more detail please.  

How did you download a file to another computer?   Were you signed in to the desktop from the laptop through ssh?  Some other way?

What directory did you download this file to?

---

### Post by rebeltaz on 2016-12-31
I thought you might have inadvertently given me the clue... I had forgotten to check the folder contain this file itself. Sure enough, it was set to [access files] for both group and other, so I set those to [create and delete files]. No go... same problem.

My laptop is connected to the desktop via cifs through an automatic mount on demand via fstab. I downloaded the file from the internet using the Firefox addon DownloadThemAll!. This was set to download the file directly to the remote (desktop) computer via the share mount /mnt/shop.data/files/

---

### Post by TheFu on 2016-12-31
CIFS permissions don't use normal Linux permissions. That is all controlled via the samba server settings.  I cannot help with GUI uses of this.
If both systems are Unix/Linux, using NFS would be the preferred method, and faster.

---

### Post by rebeltaz on 2016-12-31
I need for the server (the desktop share) to be able to be accessed from other OSes - Linux, Android, Windows...

---

### Post by bab1 on 2017-01-01
> **rebeltaz said:**
> I have a laptop and a desktop connected to my network. From my laptop, I downloaded a file to the desktop's harddrive. I can open the file from my laptop and do anything I want with it, but if I open that same file from the desktop, it will only open in [read-only] mode. 
Are you using Samba to look at the files on the local machine (desktop)?  Is the client (remote host) also running Ubuntu?  Where/when do you see the [read-only] mode shown?> 
I looked at the properties and while the owner and group was set to derek (me) and with read-write access, the group and others access was set to read-only. I changed those to read-write, but it still only opens in [read-only] mode from the desktop. Furthermore, if I modify the file (it's a .7z archive) from the laptop, the permissions are set back to read-only for group and others. 
You can't change the file and directory permissions when a Samba share (cifs) is mounted.  Only at mount time or by share definition (No chmod!)  You should not have to change any permissions from a download as that is all Linux.  I have checked using my setup and all files are 664 (rw-rw=r) at creation (download).> 
Can someone explain this to me, please?

This is what the ls -l listing looks like (before modifying the archive):

-rw-rw-rw- 1 derek derek 1448969266 Dec 21  2014 filename.rar

After modifying the archive it reads:

-rwxr--r-- 1 derek derek 1448969266 Dec 31 12:52 filename.rar
Neither of these are normal permissions setup based on the umask that Ubuntu uses.  The default Ubuntu umask of 0002 configures files to be 0664 (rw-rw-r--) on creation.  Directories are 775 (drwxrwxr-x).


Rather than guess at what the Samba and FS configuration is, lets see what it looks like.  Post the output of these terminal commands:

What version of Ubuntu are you using on the desktop ```
lsb_release -a
```

What users are there on the file server (desktop)```
getent passwd|grep 100
```

What users are Samba users```
sudo pdbedit -L
```

What is Samba configuration```
cat /etc/samba/smb.conf
```

What (if any) do the GUI defined shares look like```
net usershare info --long
```

What do the /etc/fstab mounts look like```
cat /etc/fstab
```

What are the permissions on the Linux file system that is being shared (/mnt/shop.data/files/  and any subdirectories of /mnt that are relevant)```
ls -l <directory>
```

---

### Post by rebeltaz on 2017-01-01
> **bab1 said:**
> Are you using Samba to look at the files on the local machine (desktop)?  Is the client (remote host) also running Ubuntu?  Where/when do you see the [read-only] mode shown?

What I am doing is deleting certain files from within these archives. They are very large and so it is taking forever to process them over a wireless connection. What I would prefer to do is to log in to the desktop over a remote connection and process the files directly from that computer. The share is a local harddrive to that (desktop) computer, so it's much faster to process files that way. When I open the archive over a remote connection using the desktop's OS, that is when it opens in [read-only] mode. Odd thing is that any other archive I have tried to open that way on the same shared harddrive opens in full access mode. 

> You can't change the file and directory permissions when a Samba share (cifs) is mounted.  Only at mount time or by share definition (No chmod!)  You should not have to change any permissions from a download as that is all Linux.  I have checked using my setup and all files are 664 (rw-rw=r) at creation (download).
Neither of these are normal permissions setup based on the umask that Ubuntu uses.  The default Ubuntu umask of 0002 configures files to be 0664 (rw-rw-r--) on creation.  Directories are 775 (drwxrwxr-x).

This just applies to the main mount point - /mnt/shop.data/ - though, right? I mean I should be be able to modify the permissions of files/directories contained under that point, shouldn't I?

> Rather than guess at what the Samba and FS configuration is, lets see what it looks like.  Post the output of these terminal commands:

What version of Ubuntu are you using on the desktop ```
lsb_release -a
```

The desktop is running 10.04.4 LTS. Yes, I know that is "obsolete" but generally it works and I can perform certain tasks with that machine that I cannot do on newer versions. The laptop is running 16.04.1 LTS with MATE Desktop Environment 1.12.1.

> What users are there on the file server (desktop)```
getent passwd|grep 100
```

```

libuuid:x:100:101::/var/lib/libuuid:/bin/sh
derek:x:1000:1000:Derek,,,:/home/derek:/bin/bash

```

> What users are Samba users```
sudo pdbedit -L
```

```
derek:1000:Derek
```

> What is Samba configuration```
cat /etc/samba/smb.conf
```

```

derek@shop:~$ cat /etc/samba/smb.conf
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
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
;   netbios name = shop

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
   name resolve order = lmhosts hosts wins bcast
#   name resolve order = hosts bcast

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

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user
#   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true
#   encrypt passwords = false

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
#   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
#   passwd program = /usr/bin/passwd %u
#   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
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

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

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
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

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
   usershare owner only = false

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

   lanman auth = Yes
   client lanman auth = Yes
   client plaintext auth = Yes

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

```

> What (if any) do the GUI defined shares look like```
net usershare info --long
```

```

derek@shop:~$ net usershare info --long
[backup.drive]
path=/mnt/backup
comment=
usershare_acl=Everyone:F,
guest_ok=n

[multimedia]
path=/mnt/multimedia
comment=
usershare_acl=Everyone:F,
guest_ok=n

[christmas]
path=/mnt/multimedia/Christmas/Christmas Time in Shelby
comment=
usershare_acl=Everyone:R,
guest_ok=n

[shop_docs]
path=/home/derek
comment=
usershare_acl=Everyone:F,
guest_ok=n

[shop.data]
path=/mnt/shop.data
comment=
usershare_acl=Everyone:F,
guest_ok=n

```

> What do the /etc/fstab mounts look like```
cat /etc/fstab
```

```

derek@shop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b9d38a56-e771-4b56-86e3-aaf87f822578 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=113887ce-b719-4978-a701-763b7d5b14f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sdb2	/mnt/shop_data		ntfs	auto,uid=derek,gid=derek	00

#/dev/sdb1 normally unless another SATA drive installed
UUID=fa9d3519-6125-4121-9810-b2822e398780	/mnt/shop.data	ext4	defaults0	0
UUID=df479888-2010-485f-a620-0fab6516fab6	/mnt/multimedia		ext4	auto,users,rw,exec,sync	0	0

UUID=9ba43ab2-0d28-422d-883c-2fdd38c155e7	/mnt/multimedia.backup		ext4	noauto,users,rw,exec,sync	0	0

```

> What are the permissions on the Linux file system that is being shared (/mnt/shop.data/files/  and any subdirectories of /mnt that are relevant)```
ls -l <directory>
```

```

ls -l /mnt
drwxrwxrwx 20 derek derek 4096 2016-12-22 11:41 shop.data

ls -l /mnt/shop.data
drwxr-xr-x  7 derek derek   4096 2016-12-31 12:05 subfiles

ls -l /mnt/shop.data/subfiles
drwxrwxrwx 2 derek derek 4096 2017-01-01 13:39 files

ls -l /mnt/shop.data/subfiles/files
-rwxr--r-- 1 derek derek  803435740 2017-01-01 13:39 filename01.rar
-rw-rw-rw- 1 derek derek 2224360068 2012-08-14 00:14 filename02.rar

```

On the ls of the /mnt/shop.data/subfiles/files folder, you can see that there are two different permissions for the two files. filename02 is the permissions of the file now, after I modified them with 666 trying to get it to work. When I open the file on my laptop and delete files from within the archive, engrampa archive manager saves it back to the directory with 744 instead.

---

### Post by bab1 on 2017-01-03
> **rebeltaz said:**
>  mode. Odd thing is that any other archive I have tried to open that way on the same shared harddrive opens in full access mode.
This tells me that there is a problem with the archive itself.



... You can't change the file and directory permissions when a Samba share (cifs) is [already] mounted.> 
This just applies to the main mount point - /mnt/shop.data/ - though, right? I mean I should be be able to modify the permissions of files/directories contained under that point, shouldn't I?
No.  It means you can't modify any permissions existing after the entire cifs file system is set> 



```

derek@shop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b9d38a56-e771-4b56-86e3-aaf87f822578 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=113887ce-b719-4978-a701-763b7d5b14f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sdb2	/mnt/shop_data		ntfs	auto,uid=derek,gid=derek	00

#/dev/sdb1 normally unless another SATA drive installed
UUID=fa9d3519-6125-4121-9810-b2822e398780	/mnt/shop.data	ext4	defaults0	0
UUID=df479888-2010-485f-a620-0fab6516fab6	/mnt/multimedia		ext4	auto,users,rw,exec,sync	0	0

UUID=9ba43ab2-0d28-422d-883c-2fdd38c155e7	/mnt/multimedia.backup		ext4	noauto,users,rw,exec,sync	0	0

```

```

ls -l /mnt
drwxrwxrwx 20 derek derek 4096 2016-12-22 11:41 shop.data

ls -l /mnt/shop.data
drwxr-xr-x  7 derek derek   4096 2016-12-31 12:05 subfiles

ls -l /mnt/shop.data/subfiles
drwxrwxrwx 2 derek derek 4096 2017-01-01 13:39 files

ls -l /mnt/shop.data/subfiles/files
-rwxr--r-- 1 derek derek  803435740 2017-01-01 13:39 filename01.rar
-rw-rw-rw- 1 derek derek 2224360068 2012-08-14 00:14 filename02.rar

```
I'm surprised to see then above.  I thought you indicated that you configured the Samba shares to mount via the ftab file.  

On the ls of the /mnt/shop.data/subfiles/files folder, you can see that there are two different permissions for the two files. filename02 is the permissions of the file now, after I modified them with 666 trying to get it to work. When I open the file on my laptop and delete files from within the archive, ***engrampa archive manager saves it back to the directory with 744 instead.***
I no nothing about engrampa.  None of what you have shown indicates a Samba problem.  Sorry I can't help more.

---

### Post by rebeltaz on 2017-01-04
> **bab1 said:**
> This tells me that there is a problem with the archive itself.

... You can't change the file and directory permissions when a Samba share (cifs) is [already] mounted.
No.  It means you can't modify any permissions existing after the entire cifs file system is set
I no nothing about engrampa.  None of what you have shown indicates a Samba problem.  Sorry I can't help more.

I have 66 of these archives exhibiting the same problem. But it is ONLY these 66 .rar files downloaded from this one source. I'm almost done editing them anyway, so...

But the file permissions.... that doesn't make sense. If you can't modify file permissions after a file system is mounted, and you obviously cannot modify file permissions BEFORE a file system is mounted, how are you supposed to modify file permissions? I've modified file permissions on remote mounted file systems many times over the past years....

---

### Post by TheFu on 2017-01-04
In simple Samba setups, file and directory permissions are set at mount time, by the mount options.
[https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html#id2559114](https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html#id2559114) describes other modes.

I understand it is possible to create a Windows-UserID to Unix userid mapping, so that full POSIX permissions are possible. Don't know what that requires under Samba. I've never done this (or don't remember doing it), but have worked places where full-time admins setup and managed it.  Perhaps most people do it these days using Active Directory?  
[https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html](https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/AccessControls.html) is the Samba guide for how to manage this stuff.
>  If the parameter nt acl support is set to false, any attempt to set security permissions will fail with an "Access Denied" message. 

Or you can use NFS. Almost every file and directory permission possible is supported between the client and server. NFS is the native Unix-to-Unix storage sharing method. #3 above gives a little more detail.  Of course, if you Windows is involved, NFS is non-trivial to use and only included in Enterprise and Ultimate versions of the software.

---

### Post by bab1 on 2017-01-04
> **rebeltaz said:**
> But the file permissions.... that doesn't make sense. If you can't modify file permissions after a file system is mounted, and you obviously cannot modify file permissions BEFORE a file system is mounted, how are you supposed to modify file permissions? I've modified file permissions on remote mounted file systems many times over the past years....
I didn't say you can't modify ***any*** file system permissions.  I was specific.  Only CIFS and NTFS have this problem.  The cifs and ntfs-3g drivers are limited in many ways.  Not being a native Linux file system type has it's limitations.  These 2 Microsoft type file system types are what I was specifically talking about.  

I was surprised to see you did not mount the cifs shares via fstab.  Not that you need to, just that it seemed that is what you were talking about.  The EXT file system certainly allows permissions and and ownership to be modified using chmod, chown and chgrp from the command line.  Nautilus uses these 3 tools internally I believe.  Both methods use the default umask for Ubuntu of 0002.

---

### Post by rebeltaz on 2017-01-04
> **bab1 said:**
> I didn't say you can't modify ***any*** file system permissions.  I was specific.  Only CIFS and NTFS have this problem.  The cifs and ntfs-3g drivers are limited in many ways.  Not being a native Linux file system type has it's limitations.  These 2 Microsoft type file system types are what I was specifically talking about.  

I was surprised to see you did not mount the cifs shares via fstab.  Not that you need to, just that it seemed that is what you were talking about.  The EXT file system certainly allows permissions and and ownership to be modified using chmod, chown and chgrp from the command line.  Nautilus uses these 3 tools internally I believe.  Both methods use the default umask for Ubuntu of 0002.

Yeah, I was talking about CIFS and NTFS. Sorry. 

Regarding fstab... I just noticed something, and remember I kjnow just enough about linux to be dangerous! In the fstab of the host (desktop) computer, I do have those drives mounted at boot time:

```
UUID=fa9d3519-6125-4121-9810-b2822e398780	/mnt/shop.data	ext4	defaults0	0
UUID=df479888-2010-485f-a620-0fab6516fab6	/mnt/multimedia		ext4	auto,users,rw,exec,sync	0	0
```

I just noticed that I am using ext4 to mount those. Here on the remote (laptop) system, I am also mounting those via autofs since the computer was trying to mount them before the network was fully up and failing. But... looking at that now, I see that I am, for some reason, using cifs to mount those:

```
multimedia -fstype=cifs,rw,username=derek,password=xxxxxx ://192.168.1.15/multimedia
shop.data -fstype=cifs,rw,username=derek,password=xxxxxxx ://192.168.1.15/shop.data
```

I **want** to think that I tried ext4 to begin with but they wouldn't mount until I used cifs. Not sure why, though, if they mount with ext4 on the host system. 

I do use chown, chmod and chgrp from the command line and nautilus on the host system, but I use nemo on the remote system. My head hurts... I'm going to bed and I will think about this domani...

Later.

---

