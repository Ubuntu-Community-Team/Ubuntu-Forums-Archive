---
title: "help with samba! not allowing discovery"
date: 2021-10-07
forum: General Help
---

### Post by rebeltaz on 2021-10-07
I don't know what is wrong (obviously). I was running a media server on a pi. I had directories shared via samba and I was accessing them across multiple systems and OS's including windows, linux and pi's running Kodi. The server pi crashed so I  installed Ubuntu 20 on a miniPC and installed samba. 

Kodi sees the system because it can read and access the shared mysql database on that system. My laptop (running Ubuntu 18) mounts the shared directories at boot and I can browse them just fine. I can type in smb://192.168.1.15/multimedia and access the directories just fine.  However.....

The directories do not show up under ANY Windows Networking nor can kodi see the directories under it's SMB discovery.

Can someone - ANYONE - tell me what is wrong!? !?! I have spent HOURS on this freaking system and I have the headache to show for it.

This is the smb.conf file contents:

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
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

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

# We want Samba to only log to /var/log/samba/log.{smbd,nmbd}.
# Append syslog@1 if you want important messages to be sent to syslog too.
   logging = file

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone server" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server

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
   pam password change = no

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
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap config * :              backend = tdb
;   idmap config * :              range   = 3000-7999
;   idmap config YOURDOMAINHERE : backend = tdb
;   idmap config YOURDOMAINHERE : range   = 100000-999999
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 means that usershare is disabled.
#   usershare max shares = 100

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


[shop.data]
   comment = shop.data
   path = /mnt/shop.data
   browseable = yes
   read only = no
   guest ok = no

[multimedia]
   comment = multimedia
   path = /mnt/multimedia
   browseable = yes
   read only = no
   guest ok = no


```

If this helps:

```

> smbclient -L 192.168.1.15
WARNING: The "syslog" option is deprecated
Enter WORKGROUP\derek's password: 

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	shop.data       Disk      shop.data
	multimedia      Disk      multimedia
	IPC$            IPC       IPC Service (derek-VOT133 server (Samba, Ubuntu))
Reconnecting with SMB1 for workgroup listing.
protocol negotiation failed: NT_STATUS_INVALID_NETWORK_RESPONSE
Failed to connect with SMB1 -- no workgroup available

```

---

### Post by ActionParsnip on 2021-10-07
Do the folders you are sharing exist? Are the separate partitions and mounted to those points (If so I hope they aren't NTFS).
Do you have firewalls configured and do they allow the SMB traffic?
Are the systems accessing the share on the same subnet?
Can the systems PING each other?

---

### Post by TheFu on 2021-10-07
Win10 changed parameters for SMB connections that were implemented just before 20.04 was released.  The Samba team changed their defaults just before 20.04 was released too.  Since that time, getting Win10 and the version of Samba used by 20.04 to work together has been complicated.  I can recommend that you search these forums for Morbius1's posts about the topic.  

I think the summary is that the only effective way to share with Win10 systems is by setting up the /etc/samba/smb.conf file.  Using a GUI doesn't work reliably.  [Https://ubuntuforums.org/showthread.php?t=2434383](Https://ubuntuforums.org/showthread.php?t=2434383)  I have a note that restarting the service isn't sufficient for some samba configuration changes - a reboot is required.  For those instructions to be so simple, he had to make lots and lots of assumptions.  

If that doesn't help, please post the output from **testparm** so we see exactly what samba sees configured.

---

### Post by rebeltaz on 2021-10-07
> **ActionParsnip said:**
> Do the folders you are sharing exist? Are the separate partitions and mounted to those points (If so I hope they aren't NTFS).
Do you have firewalls configured and do they allow the SMB traffic?
Are the systems accessing the share on the same subnet?
Can the systems PING each other?

What I am trying to share are two drives that are mounted under /mnt as /mnt/multimedia and /mnt/shop.data. fdisk shows the drives as linux partitions. I amusing ufw, but even with it disabled, I still can't access the shares. The systems are all on the same 192.168.1.xxx network. Yes. Everyone responds to each others pings. 

```

~$ sudo fdisk -l
[sudo] password for derek: 
Disk /dev/sda: 1.84 TiB, 2000398933504 bytes, 3907029167 sectors
Disk model: Backup+ Desk    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x4e802e5c

Device     Boot Start        End    Sectors  Size Id Type
/dev/sda1          63 3907024064 3907024002  1.8T 83 Linux

Partition 1 does not start on physical sector boundary.


Disk /dev/sdb: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: Tech            
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x1549f232

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1          63 976768064 976768002 465.8G 83 Linux

Partition 1 does not start on physical sector boundary.


Disk /dev/sdc: 298.9 GiB, 320072933376 bytes, 625142448 sectors
Disk model: WDC WD3200BPVT-2
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x9bf9a4cd

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sdc1  *       2048   1050623   1048576   512M  b W95 FAT32
/dev/sdc2       1052670 625141759 624089090 297.6G  5 Extended
/dev/sdc5       1052672 625141759 624089088 297.6G 83 Linux

Partition 2 does not start on physical sector boundary.

```

> **TheFu said:**
> Win10 changed parameters for SMB connections that were implemented just before 20.04 was released.  The Samba team changed their defaults just before 20.04 was released too.  Since that time, getting Win10 and the version of Samba used by 20.04 to work together has been complicated.  I can recommend that you search these forums for Morbius1's posts about the topic.  

I think the summary is that the only effective way to share with Win10 systems is by setting up the /etc/samba/smb.conf file.  Using a GUI doesn't work reliably.  [Https://ubuntuforums.org/showthread.php?t=2434383](Https://ubuntuforums.org/showthread.php?t=2434383)  I have a note that restarting the service isn't sufficient for some samba configuration changes - a reboot is required.  For those instructions to be so simple, he had to make lots and lots of assumptions.  

If that doesn't help, please post the output from **testparm** so we see exactly what samba sees configured.

I did see the issues with win10 systems, but while yes... one win10 system doesn't see the shares, neither do my other linux systems (one running 18.04 and one running 16.04) or the raspberry pi running raspbian (Jessie, I think). I did do all of the configuration through the smb.conf file, not gui. Yes, I did try restarting the smbd server, but I have also rebooted that system **several** times as well. And for some reason, the laptop running 18.04 can auto mount the shares via fstab (even though th y do not show up under Windows Networks), the desktop running 16.04 apparently can't mount the shares via the same fstab entries - both of which always worked up until now.

This is the testparm output.
```

~$ testparm
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Server role: ROLE_STANDALONE

Press enter to see a dump of your service definitions

# Global parameters
[global]
	log file = /var/log/samba/log.%m
	logging = file
	map to guest = Bad User
	max log size = 1000
	obey pam restrictions = Yes
	pam password change = Yes
	panic action = /usr/share/samba/panic-action %d
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	passwd program = /usr/bin/passwd %u
	server role = standalone server
	server string = %h server (Samba, Ubuntu)
	unix password sync = Yes
	usershare allow guests = Yes
	idmap config * : backend = tdb


[printers]
	browseable = No
	comment = All Printers
	create mask = 0700
	path = /var/spool/samba
	printable = Yes


[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


[shop.data]
	comment = shop.data
	guest ok = Yes
	path = /mnt/shop.data
	read only = No


[multimedia]
	comment = multimedia
	guest ok = Yes
	path = /mnt/multimedia
	read only = No

```

---

### Post by TheFu on 2021-10-07
Are you typing in the IP address in the smb://{ip address} URLs?  Browsing doesn't seem to work in Win10 since MSFT broke that.

---

### Post by rebeltaz on 2021-10-07
> **TheFu said:**
> Are you typing in the IP address in the smb://{ip address} URLs?  Browsing doesn't seem to work in Win10 since MSFT broke that.

I was just fixing to update this. Oddly enough, the one windows system we have is 7, not 10 like I thought, but even at that, we can see, browse and access the shares from there just fine. 

I still can't access it from the raspberry pi running kodi, though, which is most important or from the shop computer running Ubuntu 16.04 and it's not browseable as a network share from the Ubutnu 18.04 system, but it is automounting them so I'm not too concerned with that one - just that the behavior is another piece of the puzzle. 

On the Ubuntu 16.04 system, when I try to go directly to that drive (which used to auto mount through fstab just like the 18.04 system using the same fstab entries), this is what I get:

```
Could not display "smb://192.168.1.15/multimedia/".
Error: Failed to mount Windows share: Connection timed out
Please select another viewer and try again.
```

---

### Post by TheFu on 2021-10-07
Ubuntu 16.04 support ended last April. Sorry. Running supported releases is important.

```
$ smbclient -L 192.168.1.15
```

I use OSMC (a Kodi specifically for r-pi hardware).  Haven't seen any issues accessing media on Ubuntu 18.04 servers via NFS or DLNA (plex or Jellyfin).

---

### Post by rebeltaz on 2021-10-07
> **TheFu said:**
> Ubuntu 16.04 support ended last April. Sorry. Running supported releases is important.

lol... I know. You tell me that every time :) 

Have you seen this - [https://hackaday.com/2021/10/06/atari-st-still-manages-campground-reservations-after-36-years/](https://hackaday.com/2021/10/06/atari-st-still-manages-campground-reservations-after-36-years/) - Newer isn't always better :)

> **TheFu said:**
> ```
$ smbclient -L 192.168.1.15
```
I'll check that when I get to the shop tomorrow. 

I use OSMC (a Kodi specifically for r-pi hardware).  Haven't seen any issues accessing media on Ubuntu 18.04 servers via NFS or DLNA (plex or Jellyfin).[/QUOTE]

Yeah. That's the one. OSMC. Up until I transferred everything from the pi media server to this new 20.04 server, I wasn't having any trouble either. I've got a good mind to erase the whole dadblamed thing and put 18.04 on it.

---

### Post by rebeltaz on 2021-10-07
> **TheFu said:**
> 
```
$ smbclient -L 192.168.1.15
```


Well, since 16 isn't supported anyway, I went ahead and ran that on this computer (18.04) and this was the output:

```

 smbclient -L 192.168.1.15
WARNING: The "syslog" option is deprecated
Enter WORKGROUP\derek's password: 

	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	shop.data       Disk      shop.data
	multimedia      Disk      multimedia
	IPC$            IPC       IPC Service (derek-VOT133 server (Samba, Ubuntu))
	HP_Color_LaserJet_MFP_M476nw_01BDC3_ Printer   
Reconnecting with SMB1 for workgroup listing.
protocol negotiation failed: NT_STATUS_INVALID_NETWORK_RESPONSE
Failed to connect with SMB1 -- no workgroup available

```

---

### Post by rebeltaz on 2021-10-07
So.... I remembered something about setting a 'lanman' setting the last time I had to configure samba. I did a search on that term and found this - [https://askubuntu.com/questions/1213759/allow-smb-1-with-lanman-authentication-with-samba](https://askubuntu.com/questions/1213759/allow-smb-1-with-lanman-authentication-with-samba)

```
[global]
   server min protocol = NT1
   ntlm auth = yes
   lanman auth = yes
```

and then reran smbpasswd to reset the password. THANK GOD! It worked!

In case anyone else has this problem trying to get Ubuntu 20.04 samba talking to "obsolete" (as TheFu would say :P) equipment. Thanks for letting me bounce things off y'all :)

---

