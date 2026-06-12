---
title: "Samba Share Unable To Write"
date: 2015-02-27
forum: General Help
---

### Post by david355 on 2015-02-27
Good evening. This is my first post here. I have Googled this problem to death and have finally given in. I need help...

I am trying to setup a file/media server using a my old computer. I have been able to successfully install Ubuntu server following these videos ([link1]("https://www.youtube.com/watch?v=ndAYZ0DJ-U4&index=1&list=LLr09-tCI02XHzBpuXlQyeuA") [link2]("https://www.youtube.com/watch?v=9jdbwlg0QFc&index=2&list=LLr09-tCI02XHzBpuXlQyeuA")). My original plan was to just hook up my external hard drives to the system and just access the files that way. After trying for hours, I was never able to mount the device and just opted to purchase a new 3TB internal drive.

At this point, I have successfully gained access to the server via my Win7 desktop and laptop, although, I do have to use my samba username and password every time I turn the computer on and access the server. I am so close to being done right now, but I can't write anything to the shares I've created. I've tried changing the permissions, forcing my username, making the shares writable, and recently I just reformatted my new drive to ext3 thinking that would help. Unfortunately, I'm still getting the 'You need permission to perform this action' popup when trying to create a new file.

What am I doing wrong?

Please excuse my ignorance as this is my first post. If you need any documentation/files/logs/etc., please let me know. I don't actually no how to post those items, but I'm researching now...

Thanks

---

### Post by bab1 on 2015-02-27
> **david355 said:**
> Good evening. This is my first post here. I have Googled this problem to death and have finally given in. I need help...

I am trying to setup a file/media server using a my old computer. I have been able to successfully install Ubuntu server following these videos ([link1]("https://www.youtube.com/watch?v=ndAYZ0DJ-U4&index=1&list=LLr09-tCI02XHzBpuXlQyeuA") [link2]("https://www.youtube.com/watch?v=9jdbwlg0QFc&index=2&list=LLr09-tCI02XHzBpuXlQyeuA")). My original plan was to just hook up my external hard drives to the system and just access the files that way. After trying for hours, I was never able to mount the device and just opted to purchase a new 3TB internal drive.

At this point, I have successfully gained access to the server via my Win7 desktop and laptop, although, I do have to use my samba username and password every time I turn the computer on and access the server. I am so close to being done right now, but I can't write anything to the shares I've created. I've tried changing the permissions, forcing my username, making the shares writable, and recently I just reformatted my new drive to ext3 thinking that would help. Unfortunately, I'm still getting the 'You need permission to perform this action' popup when trying to create a new file.

What am I doing wrong?

Please excuse my ignorance as this is my first post. If you need any documentation/files/logs/etc., please let me know. I don't actually no how to post those items, but I'm researching now...

Thanks
From the terminal (cntl +t) cut and paste the output of this command```
cat /etc/samba/smb.conf
```

Place the text inbetween the code tags.  You can do that by clicking on the [SIZE=5]**#**[/SIZE] icon at the top of the advanced reply editor and pasting the data there.

---

### Post by david355 on 2015-02-27
Here's what I get

```
## Sample configuration file for the Samba suite for Debian GNU/Linux.
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
   workgroup = MYWORKGROUP


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
   name resolve order = lmhosts host wins bcast


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
   security = user
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








#security = user
#name resolve order = lmhosts host wins bcast








[David's Files]
 comment = David's Files
 path = /files/david
 browseable = yes
 read only = no
 valid users = david
 force user = david
 writeable = yes


[Plex Media]
 comment = Plex Media
 path = /files/plex
 public = yes
 browseable = yes
 read only = no
 guest ok = yes
 writeable = yes



```

---

### Post by bab1 on 2015-02-27
Post the output of this command
```
ls -l /files

ls -l /files/david

ls -l files/plex
```
This will show the ownership and permissions for the directories.

I don't think you want to use "guest" in the plex directory.  The plex user needs to have access.  Have you made yourself a samba user (smbpasswd -a)?   Post the output of ```
sudo pdbedit -L
```

---

### Post by david355 on 2015-02-27
Here's the output of the first 3 commands:

```
total 12drwxr-xr-x 2 root   root    4096 Feb 27 00:55 david
drwxr-xr-x 2 nobody nogroup 4096 Feb 26 06:22 plex
drwxr-xr-x 3 root   root    4096 Feb 26 06:04 public

```

```
total 28-rw-r--r-- 1 root root 9972 Feb 27 00:36 check1.txt
-rw-r--r-- 1 root root  165 Feb 27 00:55 check2.txt
-rw-r--r-- 1 root root    0 Feb 27 00:55 check3.txt
-rw-r--r-- 1 root root 9970 Feb 26 23:57 smb.conf

```

```
total 0

```

> [COLOR=#000000]I don't think you want to use "guest" in the plex directory. The plex user needs to have access. Have you made yourself a samba user (smbpasswd -a)? ...[/COLOR]

Yes, I have. Just curious, but does the password for the samba user need to be the same as the Win7 user? Both of my Win7 machines have the same username. It's not an issue, I'm just wondering if I changed one of the usernames on the Win7 machines and added samba users with the same name and password that I would be able to access the share without putting in my credentials.

> [COLOR=#000000]Post the output of[/COLOR][COLOR=#000000]Code:
sudo pdbedit -L[/COLOR]


```
david:1000:David Campbell


```

---

### Post by bab1 on 2015-02-27
> **david355 said:**
> Here's the output of the first 3 commands:

```
total 12
drwxr-xr-x 2 root   root    4096 Feb 27 00:55 david
drwxr-xr-x 2 [COLOR="#FF0000"]nobody nogroup[/COLOR] 4096 Feb 26 06:22 plex
drwxr-xr-x 3 root   root    4096 Feb 26 06:04 public

```

```
total 28
-rw-r--r-- 1 [COLOR="#FF0000"]root root[/COLOR] 9972 Feb 27 00:36 check1.txt
-rw-r--r-- 1 root root  165 Feb 27 00:55 check2.txt
-rw-r--r-- 1 root root    0 Feb 27 00:55 check3.txt
-rw-r--r-- 1 root root 9970 Feb 26 23:57 smb.conf

```

```
total 0

```
Samba access is only at the application level  File system access is never overridden by Samba.  I don't see where the user david or the user plex have permission to create files or directories at the Linux file system level (see red above).  The ownership nobody:nogroup is due to you setting guest access on the plex share.  

The /files/david directory should at least have the group ownership as  root:david.  The permissions should be 0775 so you have the ability to create files and directories with your user account.  Assuming the no other user will ever need access to the /files/david directory, you can use these two commands to provide the access```

sudo chown root:david /files/david

sudo chmod 775 /files/david

```...you should be able to create file and directory objects now.

The /files/plex situation is more complex.  There will be at least two users that need to access the directory. (i.e. david and plex).  The best way to handle this is to use common user group ownership of the directory.  If you and plex are the only users then you can add yourself to the plex user group and make that user gorup the owner of the /files/plex directory (root:plex).  How many user will there be for this share.  Since you are using Windows machines we will be using both the sgid bit (I'll explain later) and  *force group = <group_name>* on this share anyway to insure that the group name is preserved 
> 


Yes, I have. ```
david:1000:David Campbell
```
Just curious, but does the password for the samba user need to be the same as the Win7 user? Both of my Win7 machines have the same username. It's not an issue, I'm just wondering if I changed one of the usernames on the Win7 machines and added samba users with the same name and password that I would be able to access the share without putting in my credentials.

You will have to add your name to the permanent keyring if you don't want to have login each time.  If you use guest access the user name and group name is always -- nobody:nogroup by default.

I always have the same username/password on all of my machines in the network for all users.  It just makes it easier to administer.  In large networks that is one of the reasons for centralized user management.

---

### Post by david355 on 2015-02-27
> **bab1 said:**
> Samba access is only at the application level  File system access is never overridden by Samba.  I don't see where the user david or the user plex have permission to create files or directories at the Linux file system level (see red above).  The ownership nobody:nogroup is due to you setting guest access on the plex share.  

The /files/david directory should at least have the group ownership as  root:david.  The permissions should be 0775 so you have the ability to create files and directories with your user account.  Assuming the no other user will ever need access to the /files/david directory, you can use these two commands to provide the access```

sudo chown root:david /files/david

sudo chmod 775 /files/david

```...you should be able to create file and directory objects now.

Great, that allowed me to create files and directory objects in the share.

Now, one thing at a time...

> [COLOR=#000000]The /files/plex situation is more complex. There will be at least two users that need to access the directory. (i.e. david and plex). The best way to handle this is to use common user group ownership of the directory. If you and plex are the only users then you can add yourself to the plex user group and make that user gorup the owner of the /files/plex directory (root[/COLOR]:razz:[COLOR=#000000]lex). How many user will there be for this share. Since you are using Windows machines we will be using both the sgid bit (I'll explain later) and [/COLOR]*force group = <group_name> on this share anyway to insure that the group name is preserved *

I am the only user at the time. When the time comes, I may need to add more users, but that shouldn't be happening any time soon.

> [COLOR=#000000]You will have to add your name to the permanent keyring if you don't want to have login each time. If you use guest access the user name and group name is always -- nobody:nogroup by default.[/COLOR]

[COLOR=#000000]I always have the same username/password on all of my machines in the network for all users. It just makes it easier to administer. In large networks that is one of the reasons for centralized user management.[/COLOR]

How do I add my name to the permanent keyring? Am I to understand correctly that I shouldn't have guest access to the plex directory? Do I just need to change that one line in the smb.conf file?

---

### Post by bab1 on 2015-02-27
> **david355 said:**
> Great, that allowed me to create files and directory objects in the share.

Now, one thing at a time...

I am the only user at the time. When the time comes, I may need to add more users, but that shouldn't be happening any time soon.
For your needs I would just add your name to the plex group```
sudo adduser david plex
```...if you need to add other user you use the same incantation```
sudo adduser <username> plex
```

Then you have change the group ownership to /files/plex with this ```
sudo chown root:plex /files/plex
```...and set the permissions with this```
sudo chmod 0775
```

Lastly you need to set the sgid bit.  This bit forces all file/directory objects created to be the same as the parent directory group owner (SetGroupID)```
sudo chmod g+s /files/plex
```...now restart smbd again ```
sudo service smbd restart
```

You will never have the user plex using the share as that user is only "local" to the Ubuntu host. You DO NOT need to add plex to the smbpasswd data base or name that user in the share's valid users.  The share is almost exactly like the david share.

Do yourself a favor.  Use a share name with no spaces in it (e.g david_share or plex).  Linux has a hard time with spaces in names.
> 
How do I add my name to the permanent keyring? Am I to understand correctly that I shouldn't have guest access to the plex directory? Do I just need to change that one line in the smb.conf file?I don't use guest access unless the share is truly open to anyone and there I use *force group=some_group*.  I don't trust that method when you have specific users.  The login is the same as asking "who are you".  If you have guest enabled, the check is never made. 

When this is done via an Ubuntu Samba client the login box asks you if you want to add the login to the keyring.  IDK how to do it in Windows you will have to check that out.

---

### Post by david355 on 2015-02-27
> **bab1 said:**
> For your needs I would just add your name to the plex group```
sudo adduser david plex
```...if you need to add other user you use the same incantation```
sudo adduser <username> plex
```

Then you have change the group ownership to /files/plex with this ```
sudo chown root:plex /files/plex
```...and set the permissions with this```
sudo chmod 0775
```

Lastly you need to set the sgid bit.  This bit forces all file/directory objects created to be the same as the parent directory group owner (SetGroupID)```
sudo chmod g+s /files/plex
```...now restart smbd again ```
sudo service smbd restart
```


Thanks very much for the help. I may have to put something in another thread, but apparently I didn't mount the drive properly. After setting everything up as you instructed, I was able to gain write access to the plex share. However, it looks like the share is on the boot drive and not the 3TB drive I added. Reason I can tell is because when I tried to copy one folder from my media files which is located on my external (from my Win7 desktop) to the plex share, it said it didn't have enough room. The file size was about 100GB.

I was hoping this wouldn't happen so I THOUGHT I checked to make sure it was mounted properly. Apparently not

---

### Post by bab1 on 2015-02-27
> **david355 said:**
> Thanks very much for the help. I may have to put something in another thread, but apparently I didn't mount the drive properly. After setting everything up as you instructed, I was able to gain write access to the plex share. However, it looks like the share is on the boot drive and not the 3TB drive I added. Reason I can tell is because when I tried to copy one folder from my media files which is located on my external (from my Win7 desktop) to the plex share, it said it didn't have enough room. The file size was about 100GB.

I was hoping this wouldn't happen so I THOUGHT I checked to make sure it was mounted properly. Apparently not

Post the output of ```
df -h

sudo parted -l

cat /etc/fstab
```...I'll help you fix the problem.

The problem now is I need to go away for about 8 hours.  I will reply then and we can continue until it is working correctly.

---

### Post by david355 on 2015-02-27
I do too :P I didn't want to quit until you did because you were helping me so much!

I'll post the results when I wake up...

---

### Post by bab1 on 2015-02-27
> **david355 said:**
> I do too :P I didn't want to quit until you did because you were helping me so much!

I'll post the results when I wake up...

Great!  I'll talk to you then.

---

### Post by david355 on 2015-02-27
> **bab1 said:**
> Post the output of ```
df -h

sudo parted -l

cat /etc/fstab
```

> df -h

```
Filesystem            Size  Used Avail Use% Mounted on/dev/sda1             145G  2.0G  136G   2% /
none                  4.0K     0  4.0K   0% /sys/fs/cgroup
udev                  2.0G   12K  2.0G   1% /dev
tmpfs                 405M  1.5M  404M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  2.0G  8.0K  2.0G   1% /run/shm
none                  100M     0  100M   0% /run/user
/home/david/.Private  145G  2.0G  136G   2% /home/david



```

> [COLOR=#000000][FONT=Ubuntu Mono]sudo parted -l[/FONT][/COLOR]

I answered yes for if it was a gpt table (it's greater than 2TB)

```
Model: ATA WDC WD1600JB-75G (scsi)Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system  Flags
 1      1049kB  158GB  158GB   primary   ext4         boot
 2      158GB   160GB  1998MB  extended
 5      158GB   160GB  1998MB  logical




Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? yes
Model: ATA ST3000DM001-1ER1 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  2097kB  1049kB  ext3         primary



```

> [COLOR=#000000][FONT=Ubuntu Mono]cat /etc/fstab[/FONT][/COLOR]

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=0f868c91-ac6f-4730-bdc8-3383549a101c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=ee519be9-e55f-4240-9362-f357ccac528e none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/sdb1 /files vfat defaults 0 2



```

---

### Post by bab1 on 2015-02-27
I need one more piece of information.  Post the output of this command```
sudo blkid -c /dev/null -o list
```

---

### Post by david355 on 2015-02-27
> **bab1 said:**
> I need one more piece of information.  Post the output of this command```
sudo blkid -c /dev/null -o list
```

```
device     fs_type label    mount point    UUID-------------------------------------------------------------------------------
/dev/sda1  ext4             /              0f868c91-ac6f-4730-bdc8-3383549a101c
/dev/sdb1  ext3             (not mounted)  48fd2d7c-c92b-402b-9772-2008856d1216



```

Apparently it's not mounted...:?

---

### Post by bab1 on 2015-02-27
> **david355 said:**
> ```
device     fs_type label    mount point    UUID-------------------------------------------------------------------------------
/dev/sda1  ext4             /              0f868c91-ac6f-4730-bdc8-3383549a101c
/dev/sdb1  ext3             (not mounted)  48fd2d7c-c92b-402b-9772-2008856d1216



```

Apparently it's not mounted...:?

No swap either.  

Also, I'm not sure how this line in fstab works at all```
/dev/sdb1 /files vfat defaults 0 2
``` ...the formatting for the file system on the 3TB partition is not correct either.  It appears to have only a boot section.  This drive should show the full partition (sdb1) as approximately 2.8TB instead of this with parted```
Model: ATA ST3000DM001-1ER1 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  2097kB  [COLOR="#FF0000"]1049kB [/COLOR] ext3         primary
```
What's this for? What did you do to create this?```
/home/david/.Private  145G  2.0G  136G   2% u u /home/david
```

From my perspective you have no swap (but it is mentioned in the fstab), you have no space on the 3TB HDD defined (partition formatting) and 2 mysteries; one being the incorrect sdb1 entry in fstab; and the second being the hidden directory in your home directory with a separate partition mounted.

Shed some light on this situation.  What do you want to do about it?

---

### Post by david355 on 2015-02-27
> **bab1 said:**
> No swap either.  

Also, I'm not sure how this line in fstab works at all```
/dev/sdb1 /files vfat defaults 0 2
``` ...the formatting for the file system on the 3TB partition is not correct either.  It appears to have only a boot section.  This drive should show the full partition (sdb1) as approximately 2.8TB instead of this with parted```
Model: ATA ST3000DM001-1ER1 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  2097kB  [COLOR=#FF0000]1049kB [/COLOR] ext3         primary
```
What's this for? What did you do to create this?```
/home/david/.Private  145G  2.0G  136G   2% u u /home/david
```

From my perspective you have no swap (but it is mentioned in the fstab), you have no space on the 3TB HDD defined (partition formatting) and 2 mysteries; one being the incorrect sdb1 entry in fstab; and the second being the hidden directory in your home directory with a separate partition mounted.

Shed some light on this situation.  What do you want to do about it?

As far as the first "mystery", I'm not sure what that is. The second one is from me trying to mount the drive into the same location as my plex share.

The short of it is that I was trying to make the drive accessible. Period. What I want to do is use all of the drive for my file shares. I want to use it as a place to store my files on the network so I don't have to keep using my external back and forth. Also, obviously I want to use it for my plex server.

I just bought the drive so there aren't any files on it. I'll do whatever I need to to get it up and running. I'm not concerned about losing any files because there aren't any

---

### Post by bab1 on 2015-02-27
Does this host (the server) have a GUI interface?  Is it really a desktop machine?

---

### Post by david355 on 2015-02-27
It does not. I have a monitor and keyboard hooked up, but I'm now SSHing into it. And yes, I just fairly recently built a new computer and am using my old desktop as the server

---

### Post by bab1 on 2015-02-27
> **david355 said:**
> It does not. I have a monitor and keyboard hooked up, but I'm now SSHing into it. And yes, I just fairly recently built a new computer and am using my old desktop as the server
If we are just going to deal with the 3TB drive then we can just format that and mount it using fstab.  We need to delete the small partition you have and recreate the partition across the entire HDD.

To do that we first have to remove the existing partition on the 3TB disk.  We can do that with this command```
sudo parted /dev/sdb rm 1

``` 

To check the work use this command and post the output back here```
sudo parted -l /dev/sdb
```

---

### Post by david355 on 2015-02-27
Seems as though it was successful

```
Model: ATA WDC WD1600JB-75G (scsi)Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system  Flags
 1      1049kB  158GB  158GB   primary   ext4         boot
 2      158GB   160GB  1998MB  extended
 5      158GB   160GB  1998MB  logical




Model: ATA ST3000DM001-1ER1 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start  End  Size  File system  Name  Flags



```

---

### Post by bab1 on 2015-02-27
Now we will create the 3TB partition.  This will require you to answer a couple of questions.  The questions will be start and stop positions.  The start is 0TB and the stop is 3TB.  You can always cancel just before it runs.  The command is ```

sudo parted /dev/sdb mkpart primary ext4 

```

---

### Post by david355 on 2015-02-27
Here are the results:

```
Start? 0End? 3
Warning: The resulting partition is not properly aligned for best performance.
Ignore/Cancel? cancel
root@wormfarm:/home/david# sudo parted /dev/sdb mkpart primary ext4
Start? 0
End? 3TB
Warning: The resulting partition is not properly aligned for best performance.
Ignore/Cancel? ignore
Information: You may need to update /etc/fstab.



```

---

### Post by david355 on 2015-02-27
Also

```
root@wormfarm:/home/david# sudo parted -l /dev/sdbModel: ATA WDC WD1600JB-75G (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system  Flags
 1      1049kB  158GB  158GB   primary   ext4         boot
 2      158GB   160GB  1998MB  extended
 5      158GB   160GB  1998MB  logical




Model: ATA ST3000DM001-1ER1 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      17.4kB  3001GB  3001GB               primary



```

---

### Post by bab1 on 2015-02-27
> **david355 said:**
> Here are the results:

```
Start? 0End? 3
Warning: The resulting partition is not properly aligned for best performance.
Ignore/Cancel? cancel
root@wormfarm:/home/david# sudo parted /dev/sdb mkpart primary ext4
Start? 0
End? 3TB
Warning: The resulting partition is not properly aligned for best performance.
Ignore/Cancel? ignore
Information: You may need to update /etc/fstab.



```
I would have answered start= [COLOR="#FF0000"]0GB[/COLOR]  and end = [COLOR="#FF0000"]3000GB[/COLOR].  remove the partition and try again.

My edit is in [COLOR="#FF0000"]red[/COLOR]

---

### Post by david355 on 2015-02-27
Done

```
root@wormfarm:/home/david# sudo parted /dev/sdb mkpart primary ext4Start? 0TB
End? 3TB
Information: You may need to update /etc/fstab.



```

---

### Post by bab1 on 2015-02-27
> **david355 said:**
> Done

```
root@wormfarm:/home/david# sudo parted /dev/sdb mkpart primary ext4Start? 0TB
End? 3TB
Information: You may need to update /etc/fstab.



```

Show me the partitions```
sudo parted -l
```

Look at my last response (in red).  If the partition is not 3000GB we will have to do this again.

---

### Post by david355 on 2015-02-27
...

```
Model: ATA WDC WD1600JB-75G (scsi)Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system  Flags
 1      1049kB  158GB  158GB   primary   ext4         boot
 2      158GB   160GB  1998MB  extended
 5      158GB   160GB  1998MB  logical




Model: ATA ST3000DM001-1ER1 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  3001GB  3001GB  ext3         primary



```

---

### Post by bab1 on 2015-02-27
> **david355 said:**
> ...

```
Model: ATA WDC WD1600JB-75G (scsi)Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system  Flags
 1      1049kB  158GB  158GB   primary   ext4         boot
 2      158GB   160GB  1998MB  extended
 5      158GB   160GB  1998MB  logical




Model: ATA ST3000DM001-1ER1 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  3001GB  3001GB  ext3         primary



```
Great!  Now we need to format the partition with this comand```
sudo mkfs.ext4 -m1 /dev/sdb1
```

When this is done use this command to display the new blkid```
sudo blkid -c /dev/null -o list
```

---

### Post by david355 on 2015-02-27
> **bab1 said:**
> Great!  Now we need to format the partition with this comand```
sudo mkfs.ext4 -m1 /dev/sdb1
```

When this is done use this command to display the new blkid```
sudo blkid -c /dev/null -o list
```

Done

```
root@wormfarm:/home/david# sudo blkid -c /dev/null -o listdevice     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              0f868c91-ac6f-4730-bdc8-3383549a101c
/dev/sdb1  ext4             (not mounted)  3c0fb09c-c534-4245-8ff5-bf5cc72bdfbe



```

---

### Post by bab1 on 2015-02-27
> **david355 said:**
> Done

```
root@wormfarm:/home/david# sudo blkid -c /dev/null -o listdevice     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              0f868c91-ac6f-4730-bdc8-3383549a101c
/dev/sdb1  ext4             (not mounted)  3c0fb09c-c534-4245-8ff5-bf5cc72bdfbe



```
Let's temporarily mount it with this```
sudo mount /dev/sdb1 /files
```

Show me the results with these commands```
df -h

mount

```

---

### Post by david355 on 2015-02-27
> **bab1 said:**
> Let's temporarily mount it with this```
sudo mount /dev/sdb1 /files
```

Show me the results with these commands```
df -h

mount

```

I'm guessing I need to change permissions again?

```
root@wormfarm:/home/david# sudo mount /dev/sdb1 /files/root@wormfarm:/home/david# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             145G  2.0G  136G   2% /
none                  4.0K     0  4.0K   0% /sys/fs/cgroup
udev                  2.0G   12K  2.0G   1% /dev
tmpfs                 405M  1.5M  404M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  2.0G  8.0K  2.0G   1% /run/shm
none                  100M     0  100M   0% /run/user
/home/david/.Private  145G  2.0G  136G   2% /home/david
/dev/sdb1             2.7T   73M  2.7T   1% /files
root@wormfarm:/home/david# mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
/home/david/.Private on /home/david type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=ac303eef95c27200,ecryptfs_fnek_sig=a606fe2322e25c7a)
/dev/sdb1 on /files type ext4 (rw)



```

---

### Post by bab1 on 2015-02-27
Yes we will need to set up the file system permissions for sharing and group usage after the next step which is to make the partition auto mount at boot time.

To do that we need to edit the /etc/fstab file.  The original file looks like this ```

# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=0f868c91-ac6f-4730-bdc8-3383549a101c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=ee519be9-e55f-4240-9362-f357ccac528e none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
[COLOR="#FF0000"]/dev/sdb1 /files vfat defaults 0 2[/COLOR]

```

You want the line in red to look like this```
[COLOR="#008000"]**UUID=3c0fb09c-c534-4245-8ff5-bf5cc72bdfbe /files defaults 0 2**[/COLOR]
```

Delete the line in red and add the line in green.  If you want to put a line in as a comment you can add this line just above the line in green```
# The line beow is for the samba shares mounted at /files
```

Note!  The colors are for your benefit only.  They're not needed in the fstab file. ;-)

To actually edit the file you can use this ```
sudo nano /etc/fstab
```

To check the mount command works you can do this```
sudo mount -a
```

Show me these outputs```

mount

df -h
```

---

### Post by david355 on 2015-02-27
> **bab1 said:**
> Yes we will need to set up the file system permissions for sharing and group usage after the next step which is to make the partition auto mount at boot time.

To do that we need to edit the /etc/fstab file.  The original file looks like this ```

# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=0f868c91-ac6f-4730-bdc8-3383549a101c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=ee519be9-e55f-4240-9362-f357ccac528e none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
[COLOR=#FF0000]/dev/sdb1 /files vfat defaults 0 2[/COLOR]

```

You want the line in red to look like this```
[COLOR=#008000]**UUID=3c0fb09c-c534-4245-8ff5-bf5cc72bdfbe /files defaults 0 2**[/COLOR]
```

Delete the line in red and add the line in green.  If you want to put a line in as a comment you can add this line just above the line in green```
# The line beow is for the samba shares mounted at /files
```

Note!  The colors are for your benefit only.  They're not needed in the fstab file. ;-)

To actually edit the file you can use this ```
sudo nano /etc/fstab
```

To check the mount command works you can do this```
sudo mount -a
```

Sow me these outputs```

mount

df -h
```

```
root@wormfarm:/home/david/files# df -hFilesystem            Size  Used Avail Use% Mounted on
/dev/sda1             145G  2.0G  136G   2% /
none                  4.0K     0  4.0K   0% /sys/fs/cgroup
udev                  2.0G   12K  2.0G   1% /dev
tmpfs                 405M  1.5M  404M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  2.0G  8.0K  2.0G   1% /run/shm
none                  100M     0  100M   0% /run/user
/home/david/.Private  145G  2.0G  136G   2% /home/david
/dev/sdb1             2.7T   73M  2.7T   1% /files
root@wormfarm:/home/david/files# mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
/home/david/.Private on /home/david type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=ac303eef95c27200,ecryptfs_fnek_sig=a606fe2322e25c7a)
/dev/sdb1 on /files type ext4 (rw)



```

---

### Post by bab1 on 2015-02-27
Sow me the output of this```
cat /etc/fstab
```...I'm just making sure everything is okay.

Now we need to go back and recreate the to directories we are sharing.

The easy one is /files/david.  Do this to make the directory```
sudo mkdir -p /files/david
```
Then set the ownership ```
sudo chown root:david /files/david
```
Then set the proper permissions```
sudo chmod -R 775 /files
```

Now we setup /files/plex.  Do this to make the directory```
sudo mkdir -p /files/plex
```
Then set the ownership```
sudo chown root:plex /files/plex
```
Then set the permissions ```
sudo chmod -R 775 /files
```
Now set the sgid bit```
sudo chmod g+s /files/plex
```

It should all work at this point.  The Samba sharing has not been disturbed during this side issue.

Do you remember how to look for the permissions and ownership of the directories?

---

### Post by david355 on 2015-02-27
> [COLOR=#000000]Sow me the output of this[/COLOR][COLOR=#000000]Code:
cat /etc/fstab[/COLOR]
[COLOR=#000000]...I'm just making sure everything is okay.[/COLOR]

```
david@wormfarm:~$ cat /etc/fstab# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=0f868c91-ac6f-4730-bdc8-3383549a101c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=ee519be9-e55f-4240-9362-f357ccac528e none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=3c0fb09c-c534-4245-8ff5-bf5cc72bdfbe /files defaults 0 2



```

> [COLOR=#000000]Do you remember how to look for the permissions and ownership of the directories?[/COLOR]

Is this what you mean?

```
david@wormfarm:~$ ls -l /files/total 24
drwxrwxr-x 2 root david  4096 Feb 27 16:23 david
drwxrwxr-x 2 root root  16384 Feb 27 15:27 lost+found
drwxrwsr-x 2 root plex   4096 Feb 27 16:22 plex
david@wormfarm:~$ ls -l /files/david/
total 0
david@wormfarm:~$ ls -l /files/plex/
total 0



```

---

### Post by bab1 on 2015-02-27
Yes.  It all looks good.

Is everything working okay?

If it all works, please mark the thread solved.

---

### Post by david355 on 2015-02-27
It appears to be working just the way I want it to be.

Thanks very much bab1 for your help. My first experience as a user on the forums was very helpful and insightful.

Cheers!

---

