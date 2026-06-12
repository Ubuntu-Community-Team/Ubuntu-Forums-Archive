---
title: "Ubuntu 13.04 file sharing with other Ubuntu Computers"
date: 2013-05-28
forum: General Help
---

### Post by AgentZ86 on 2013-05-28
I'm getting time outs

I have the default install of 13.04 on 2 machines, and 1 machines is 12.04, and the other is Windows 7
My main share is on a ubuntu 13.04 folder lets call this one MAIN for description purposes.

Ubuntu - Right click share options, share with read/write and guest access with default WORKGROUP name.
Windows 7 box same setup WORKGROUP name

All the computers on the router have a shared folder setup for sharing requirements mostly

I cannot access the MAIN share on the MAIN box itself from the network browser,  nor from the other ubuntu computers
Oddly the Windows computer can access the MAIN share

I get time out from the ubuntu computers or from the MAIN itself when accessing the network browser

However, the other 2 Ubuntu computers can access their shared folders among themselves
This is very strange and I have not experienced this before.

Please advise

---

### Post by redmk2 on 2013-05-28
From the "network browser" try using cntl+l to get a location bar.  Then use this to connect:   smb://IP_ADDRESS (use the IP address of the MAIN machine).  Does this show the share?

---

### Post by AgentZ86 on 2013-05-28
> **redmk2 said:**
> From the "network browser" try using cntl+l to get a location bar.  Then use this to connect:   smb://IP_ADDRESS (use the IP address of the MAIN machine).  Does this show the share?

Yes it does
All shares seem to work normally with smb//IP's
Why is it doing that and how to fix it ?

Thanks for the replies

---

### Post by redmk2 on 2013-05-28
> **AgentZ86 said:**
> Yes it does
All shares seem to work normally with smb//IP's
Why is it doing that and how to fix it ?

Thanks for the replies

This confirms that the Samba daemon (smbd) is working correctly.  The name service (nmbd) is not resolving the name to IP.  There are several things that can be the culprit.  We need to dig some more using the CLI.

From the terminal of the server you call Main post the output of this command```
hostname
```

Also post the output of ```
cat /etc/hosts
```.

is the this machine's IP address static (stays the same)?  What is the address?  What is the output of this command```
ifconfig
```

---

### Post by HiImTye on 2013-05-28
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
are you using ufw? if so try adding the following rules
```

sudo ufw allow from 192.168.0.0/24 to any port 137:139,445 proto tcp
sudo ufw allow from 192.168.0.0/24 to any port 137:139,445 proto udp

```
substituting the ip range of your network if necessary.

---

### Post by redmk2 on 2013-05-29
> **HiImTye said:**
> [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
are you using ufw? if so try adding the following rules
```

sudo ufw allow from 192.168.0.0/24 to any port 137:139,445 proto tcp
sudo ufw allow from 192.168.0.0/24 to any port 137:139,445 proto udp

```
substituting the ip range of your network if necessary.

Samba works.  There is no need to diddle with the FW at all.  See *"All shares seem to work normally with smb//IP's"* from above.

---

### Post by HermanAB on 2013-05-29
Howdy,

Samba works best if you have a DNS server for your LAN, or at least have all hostnames and IP addresses defined in all /etc/hosts files.  Delays are usually due to bad name lookups, forcing Samba to try different methods to resolve things.

---

### Post by HiImTye on 2013-05-29
ignore this

---

### Post by AgentZ86 on 2013-05-29
Couldn't do this last night but anyhow here is the outpu

hostname
warehouse-GX617AA-ABA-SR5310F
warehouse@warehouse-GX617AA-ABA-SR5310F:~$ 


cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	warehouse-GX617AA-ABA-SR5310F

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:60:d1:7f:4a  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fed1:7f4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:133018 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71923 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:131522567 (131.5 MB)  TX bytes:24235895 (24.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:598515 (598.5 KB)  TX bytes:598515 (598.5 KB)

Look like the other ubuntu boxes

I should mention one thing that may not be related

If I turn off the computer that has the MAIN share on it, the other 2 ubuntu boxes can share among themself more easily without delays.
Just thought I should mention it

---

### Post by redmk2 on 2013-05-29
> **AgentZ86 said:**
> Couldn't do this last night but anyhow here is the output

```
hostname
warehouse-GX617AA-ABA-SR5310F
warehouse@warehouse-GX617AA-ABA-SR5310F:~$ 
```


```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	warehouse-GX617AA-ABA-SR5310F

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:60:d1:7f:4a  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fed1:7f4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:133018 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71923 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:131522567 (131.5 MB)  TX bytes:24235895 (24.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6393 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:598515 (598.5 KB)  TX bytes:598515 (598.5 KB)

```

Look like the other ubuntu boxes

I should mention one thing that may not be related

If I turn off the computer that has the MAIN share on it, the other 2 ubuntu boxes can share among themself more easily without delays.
Just thought I should mention it

The host with the MAIN share is the problem for sure.  The first thing I see is the hostname is longer than 15 characters.  NETBIOS names must be less than 15 characters.  We need to change that.  There are 2 ways to do that.  We can change the hostname itself or we can explicitly configure a suitable NETBIOS name in the **smb.conf** file.  The second method is the easiest, but the name you browse for will not be the same as the hostname.

There may be other problems, but this is definitely a problem that needs to be resolved (pardon the pun).

---

### Post by AgentZ86 on 2013-05-29
Ok thanks
I can change the name no problem

I didn't know about 15 characters so I'll definately fix that
Ubuntu gave it that name by default I didn't create that name myself

I turned it off for now and shared it on another box which is working perfectly
I need to make note of that for future reference

I'll post back once I change the name and see if that fixes the problem
Thanks again


P.S
Is this topic true for all the shared folder name too not just the computer name ?

---

### Post by redmk2 on 2013-05-29
> **AgentZ86 said:**
> 
Is this topic true for all the shared folder name too not just the computer name ?
The 15 character limit is for the NETBIOS name (the COMPUTER NAME) only.  

I would also make the share name short and with no spaces anyway.  The share name does not have to be the directory (folder name) either.  At all times the browsing is by //NETBIOS_NAME/SHARE_NAME.  I would *not want* the clutter of something like this ```
//MYCOMPUTERNAME/FAVORITE MOVIES AND VIDEOS.
```

This is preferable```
//NAME/share
```

---

### Post by AgentZ86 on 2013-05-29
Ok

I have changed the hostname via 
gksudo gedit /etc/hostname

And I copied some folders/files to another ubuntu box with the shared MAIN folder and it appeared to work well at first.

But once transfer was complete
I cannot access the shared folder with the network browser and gives me errors from any ubuntu box.

When I sit at the recieving Ubuntu box to access the folders/files with the file browser, all are locked with a little lock on each folder/file
I cannot create,add or delete content with the file browser for any of these folders but I can accessing them with the network browser on the same machine

Is this normal ?

New ouput:
hostname
beth-pc
agent86@beth-pc:~$


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
agent86@beth-pc:~$ 

eth0      Link encap:Ethernet  HWaddr 00:24:21:de:05:db  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:fede:5db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22118640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12145860 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32524030279 (32.5 GB)  TX bytes:1870395349 (1.8 GB)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2209138 (2.2 MB)  TX bytes:2209138 (2.2 MB)

---

### Post by redmk2 on 2013-05-29
> **AgentZ86 said:**
> Ok

I have changed the hostname via 
gksudo gedit /etc/hostname

When you said you knew how to change the hostname I assumed you knew that it should be changed in 2 places.  Along with the */etc/hostname *file you need to change the ***/etc/hosts*** file too.> 

And I copied some files to another computer

I can still access the files via smb://IP
But not with the network browser
If not there, where? What are you using to access via IP address.> 

Also the folder I transferred are not accessible from the network browser and the network browser gives me errors if I try to access that file from another ubuntu machine
???> 

After copy and past some folders/files to another Ubuntu box, and when I sit at the receiving Ubuntu box
and look at the folders/files with the file browser, all are locked with a little lock on each folder/file
I cannot create or add content from the file browser to any of these folders.
A Linux permissions problem.> 

I can access the local files from via network browser and open the files and ad or remove content but not from the file browser
Is this normal ?
Nautilus is both the network browser and the local file browser.  The difference is the transport protocol.  Smb/CIFS is a file protocol that is able to mount remote file systems to the local file system.  The difference is whether you are using the EXT routines to manipulate the file system or SMB/CIFS> 

Also when I go back to the sending ubuntu machine the network browser gives times out errors and can no longer access the receiving machine except for via smb://IP
Because the name services is still not correct.

What is the new hostname?  Use that in the /etc/hosts file.  Next reboot the system (for completeness).  Remember that Samba is for remote file systems (the *other *computer) and EXT is the local (to you) file system.

Now what happens?

[COLOR="#0000FF"]Edit:  
    Is this normal ?
[/COLOR]
    New ouput:
 ```
   hostname
    beth-pc
    agent86@beth-pc:~$
...


```
```

    eth0 Link encap:Ethernet HWaddr 00:24:21:de:05:db
    inet addr:192.168.1.4 Bcast:192.168.1.255 Mask:255.255.255.0
    inet6 addr: fe80::224:21ff:fede:5db/64 Scope:Link
    UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
    RX packets:22118640 errors:0 dropped:0 overruns:0 frame:0
    TX packets:12145860 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:1000
    RX bytes:32524030279 (32.5 GB) TX bytes:1870395349 (1.8 GB)
    Interrupt:43 Base address:0x2000

    lo Link encap:Local Loopback
    inet addr:127.0.0.1 Mask:255.0.0.0
    inet6 addr: ::1/128 Scope:Host
    UP LOOPBACK RUNNING MTU:16436 Metric:1
    RX packets:3989 errors:0 dropped:0 overruns:0 frame:0
    TX packets:3989 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0
    RX bytes:2209138 (2.2 MB) TX bytes:2209138 (2.2 MB) 

```

[COLOR="#008000"]**Is the IP address 192.168.1.4  static?**[/COLOR]

---

### Post by AgentZ86 on 2013-05-29
Thanks, 

I think I was editing my post while you were preparing a reponse. My edits may be more clear now, 
I really appreciate your responses and time on this.

Your assumption were correct based on my statement. 
I figured I could google it and get the name changes worked out but it appears that what I google was incomplete
Anyhow I have now changed the etc/hosts, rebooted and I can now network browse to the shared folder on the other computer now

No problem doing anything from any computer now when browsing via Browse Network option which appears in the left pane window in case you were wondering what I meant by network browser

So wondering about the file permissions topic with the locks on them
The local machine can only access and make changes to the shared folder/files that it's hosting via Browse Network and not simply file browsing to the folder.
In otherwords while sitting at the machine I can Browse Network to the shared folder/file that is on this same machine and do anything I want.
However, browsing into the home folder and opening the folder that way does not allow changes but does not give me any permission messages either.

So the only problem I have now I believe is the permission topic with the padlocks
Folder right click/permissions says permission unknown or things like
Owner: nobody
Group: nogroup
Last changed unknown

---

### Post by redmk2 on 2013-05-29
> **AgentZ86 said:**
> ...

No problem doing anything from any computer now when browsing via Browse Network option which appears in the left pane window in case you were wondering what I meant by network browser

Just so you know that the Gnome Nautilus is the browser.  It can browse both remote (network) and local files systems.> 

So wondering about the file permissions topic with the locks on them
The local machine can only access and make changes to the shared folder/files that it's hosting via Browse Network and not simply file browsing to the folder.

In otherwords while sitting at the machine I can Browse Network to the shared folder/file that is on this same machine and do anything I want.
However, browsing into the home folder and opening the folder that way does not allow changes but does not give me any permission messages either.

So the only problem I have now I believe is the permission topic with the padlocks
Folder right click/permissions says permission unknown or things like
```
Owner: nobody
Group: nogroup
Last changed unknown
```

The unknown is due to this being a remote file system mounted locally ( a file share).   When talking about a remote host we are talking about a service provided (a server) while the local machine mounting that share is the client.  The problem you are having is because the remote file system is mounted locally without knowing the user that is mounting it.  Samba defaults to the user *nobody* and the group *nogroup*.

How did you create the shares and where in the file system did you create them ( in your home directory maybe?).  The other item needed is; How secure does these shares need to be.

What do you get using this command```
net usershare info --long
```

Post the output of ```
cat /etc/samba/smb.conf
```...and also ```
sudo pdbedit -L
```

---

### Post by AgentZ86 on 2013-05-29
[backup_files]
path=/home/agent86/backup_files
comment=
usershare_acl=Everyone:F,
guest_ok=y
net usershare info --long

[Downloads]
path=/home/agent86/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Documents]
path=/home/agent86/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/powerspecw is not a well formed usershare file.
info_fn: Error was Path is not a directory.

powerspecw ? I don't know what this is the host name use to be agent86-powerspec but no w at the end.




cat /etc/samba/smb.conf
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

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

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

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
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
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
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


sudo pdbedit -L
nobody:65534:nobody
agent86:1000:agent86


I understand what your saying about who hosted to where
Yes I put this in the home directory is this not a good idea for file sharing ?


These are private residence PC's so security is not a big deal

---

### Post by redmk2 on 2013-05-29
> **AgentZ86 said:**
> ```
[backup_files]
path=/home/agent86/backup_files
comment=
usershare_acl=Everyone:F,
guest_ok=y
net usershare info --long

[Downloads]
path=/home/agent86/Downloads
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Documents]
path=/home/agent86/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/powerspecw is not a well formed usershare file.
info_fn: Error was Path is not a directory.

```
powerspecw ? I don't know what this is the host name use to be agent86-powerspec but no w at the end.

This is cruft from your earlier creations.  It can be removed later on.> 


```
cat /etc/samba/smb.conf
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

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

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

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
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
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
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
The smb.conf file appears to be unmolested at this point.> 

```
sudo pdbedit -L
nobody:65534:nobody
agent86:1000:agent86
```
I see you added yourself to the smbpasswd database.  Are there others that will be using the shares on this host ( *beth-pc:*)?> 


I understand what your saying about who hosted to where
Yes I put this in the home directory is this not a good idea for file sharing ?


These are private residence PC's so security is not a big deal
I'm a believer in separating my personal data from the information I share.  My wife of 25 years does not read my email, but with both watch the same movies and look at the same pictures.  I store all of my public data on a separate local disk that is mounted at /srv/smb, but it can just as easily be mounted at /data or /shares or some such.

It's really up to you.  The problem is tailoring the ownership/permissions for users other than yourself when you share from your own home directory.  Debian (and therefore Ubuntu) explicitly allow only the user user access to files in their own directory.   It's easier to create a directory outside that all user are allowed access via the group permissions..  If you leave the shares where they are  I believe you will have to give everyone access to the share.  This is different than guest access (anonymous access).

The choice is yours.  Either way, it's really very simple to do.

---

### Post by AgentZ86 on 2013-05-30
Ahh i see
I was reading that long samba definition and it's making sense now. It specifically talks about the /home directory

YES I prefer to give a group access if that is simpler.
I don't care about the security parts at all since we both use the same email, files/folder etc. anyhow

I assumed that sharing in the home directory would be the simplest, but this appears to be incorrect.
Thanks

P.S
Booting both computers this morning and the shares on the MAIN are no longer shared at leasts thats what is looks like from the local computer
However, I can still use the shortcut on the Second box to get to those files.
But the Second computer can't even Browse Network times out or says OOPs something is wrong message.
No longer can it see it's own self on the network nothing on the network at all now. Additionally cannot use smb:// + IP address either times out
And you can almost tell instantly that it won't work because the only folder showing is Windows Network which there should be Ubuntu computers along side of that


P.S
I'm really getting frustrated with this. What is the purpose of right clicking and sharing a folder/file if it doesn't actually share it not even with it's own self

---

### Post by redmk2 on 2013-05-30
> **AgentZ86 said:**
> Ahh i see
I was reading that long samba definition and it's making sense now. It specifically talks about the /home directory

YES I prefer to give a group access if that is simpler.
I don't care about the security parts at all since we both use the same email, files/folder etc. anyhow

I assumed that sharing in the home directory would be the simplest, but this appears to be incorrect.
Thanks

P.S
Booting both computers this morning and the shares on the MAIN are no longer shared
The Second computers can't even get to the Browse Network times out or says OOPs something is wrong message.
No longer can it see it's own self on the network nothing on the network at all now.
And you can almost tell instantly that it won't work because the only folder showing is Windows Network which there should be Ubuntu computers along side of that


P.S
I'm really getting frustrated with this. What is the purpose of right clicking and sharing a folder/file if it doesn't actually share it not even with it's own self
I understand your frustration.  The problems you are having are from the networking infrastructure not Samba at all.  From a client other than beth-pc, provide the output of this command (not a Windows machine)```
smbtree -d3
```...the output can be very long.  If you want, you can save it to a text file and either paste it into the editor or attach it to the post.  To save it to a text file in your home directory you can use this command ```
smbtree -d3 > smbtree.txt
```

[COLOR="#0000FF"]Edit:  What is the IP address of beth-pc today?  This has probably changed, thus causing your problem.[/COLOR]

---

### Post by AgentZ86 on 2013-05-30
It's not that I can't scour the net and learn all about samba and server methods, but I was hoping to keep it as simple as possible just to share files and backup to second drive as well.
I turned off my SME webserver in gateway mode and forgot most of what I learned about it 7 years ago.

I've turned off all the Ubuntu PC's except 1 with 13.04 64bit installed
Just to narrow this down and understand how sharing works on Ubuntu.

Shared one folder home/Documents checked all - allow others, guest access yes
There are other windows boxes connect to the router stil

Output from this one box is:

agent86@agent86-desktop:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::be5f:f4ff:fe9b:d49f%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.6 bcast=192.168.1.255 netmask=255.255.255.0
Enter agent86's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.2 ( 192.168.1.2 )
Connecting to host=192.168.1.2
Connecting to 192.168.1.2 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.1.2 ( 192.168.1.2 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.2 ( 192.168.1.2 )
Connecting to host=192.168.1.2
Connecting to 192.168.1.2 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.1.2 ( 192.168.1.2 )
Connecting to host=192.168.1.2
Connecting to 192.168.1.2 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
	\\LIVINGROOMPC   		Livingroom emachine
Connecting to host=LIVINGROOMPC
resolve_lmhosts: Attempting lmhosts lookup for name LIVINGROOMPC<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name LIVINGROOMPC<0x20>
resolve_wins: Attempting wins lookup for name LIVINGROOMPC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name LIVINGROOMPC<0x20>
Connecting to 199.101.28.20 at port 445
Connecting to 199.101.28.20 at port 139
smbtree -d3Error connecting to 199.101.28.20 (Success)
cli_start_connection: failed to connect to LIVINGROOMPC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\AGENT86-DESKTOP		agent86-desktop server (Samba, Ubuntu)
Connecting to host=AGENT86-DESKTOP
resolve_lmhosts: Attempting lmhosts lookup for name AGENT86-DESKTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name AGENT86-DESKTOP<0x20>
resolve_wins: Attempting wins lookup for name AGENT86-DESKTOP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name AGENT86-DESKTOP<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\AGENT86-DESKTOP\Kyocera-Mita-FS-1920-FS-1920	Kyocera Mita FS-1920 FS-1920
		\\AGENT86-DESKTOP\print$         	Printer Drivers
		\\AGENT86-DESKTOP\Documents      	
		\\AGENT86-DESKTOP\IPC$           	IPC Service (agent86-desktop server (Samba, Ubuntu))
agent86@agent86-desktop:~$ smbtree -d3


I assume the naming is 15 characters default Ubuntu given is OK ? or should this be changed again too ?


IP's all the same today as yesterday even though it's dynamic DHCP on the router
However, shouldn't I at least see computers on the network regardless of whether or not I can access any of their folders/files ?

---

### Post by AgentZ86 on 2013-05-30
When I had the SME server setup as a gateway and was also a webserver/mailserver/ftp server etc.
DHCP dynamicly gave IP's to all computers connected to the switch on the inside local network and I could share anything just about anywhere to all the computers on the network
There was group/member service to access server files but there was never a problem connecting to other computers shares on the network either. Home directories or otherwise

Still wondering if I should revisit the router setup ?

I don't understand why the Ubuntu computers only show a windows network folder and not the computers themself as they always had before ?

---

### Post by AgentZ86 on 2013-05-30
New info:
And I'm sorry to report on this

I my last post indicated I wondered about my router switch or some hardware might have something to do with it.
Although I didn't believe it was I fiddled with it anyhow.

Disconnect beth-pc and connect directly to the router just to see if I could see that computer when browsing the network
This did not seem to have any effect and I re connected it back into the switch/hub which is an Allied AT-8024

I never had a problem with this switch or connections but seemed strange to have so much trouble after taking out the SME server

I reseated all the connections and turned on the beth-pc which now sees ubuntu computers and windows network folder
Inside the windows network folder it sees all computers

The second ubuntu box running 13.04 can see all ubuntu computers and windows computer instantly and windows network folder which has all the computers in there as well.

I can't say for sure unless this problem re emerges but it would appear I have something else going on other then Ubuntu computer and samba issues.
Well at least at a glance anyhow.

Yet it is strange that the windows computers could always access the ubuntu shared files regardless of what the ubuntu computers could do and regardless of what I did with moving round connections.

I hate all this text and having to report every little thing that may or may not be related to any of it but I want to be thorough in the description in case it helps solve the problem.
Anyhow I'll restart the computers a few times and post back on the results if anything new emerges or if it resorts back to it's failed state.

I sincerly appreciate your time and effort you have put in on this.

---

### Post by AgentZ86 on 2013-05-30
It would seem that the file sharing is working as it should with little or no changes to the standard default ubuntu setup.
After I reseated all the connections on the switch the ubuntu computers shares and Browse network seems to be working as it should.

I don't know if there was a connection issue or switch issue but I have to assume there was at this point.

I guess the user who shared the files can simply use the network browser to read/write/delete instead of going through the home folder
I'll read on this topic some to get familiar with Samba so I understand more about these permissions

Thanks a lot seriously
It's been helpful and I will reflect back to this thread in the future to those commands for seeing my shares etc.

I can mark as solved for now if I can figure out how to do it. Thats seems to have changed also including the Go Advanced method LOL

---

### Post by redmk2 on 2013-05-30
You can mark it solved by using [[COLOR="#FF8C00"]**this technique **[/COLOR]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").  At the present time the "solved" option is broken.  :(

---

### Post by redmk2 on 2013-05-30
> **AgentZ86 said:**
> New info:
And I'm sorry to report on this

I my last post indicated I wondered about my router switch or some hardware might have something to do with it.
Although I didn't believe it was I fiddled with it anyhow.

Disconnect beth-pc and connect directly to the router just to see if I could see that computer when browsing the network
This did not seem to have any effect and I re connected it back into the switch/hub which is an Allied AT-8024

I never had a problem with this switch or connections but seemed strange to have so much trouble after taking out the SME server

I reseated all the connections and turned on the beth-pc which now sees ubuntu computers and windows network folder
Inside the windows network folder it sees all computers

The second ubuntu box running 13.04 can see all ubuntu computers and windows computer instantly and windows network folder which has all the computers in there as well.

I can't say for sure unless this problem re emerges but it would appear I have something else going on other then Ubuntu computer and samba issues.
Well at least at a glance anyhow.

Yet it is strange that the windows computers could always access the ubuntu shared files regardless of what the ubuntu computers could do and regardless of what I did with moving round connections.

I hate all this text and having to report every little thing that may or may not be related to any of it but I want to be thorough in the description in case it helps solve the problem.
Anyhow I'll restart the computers a few times and post back on the results if anything new emerges or if it resorts back to it's failed state.

I sincerly appreciate your time and effort you have put in on this.
Without getting too technical; the reason for the delay has nothing to do with your hardware.  It appears that the Master Browse List needed re-populating when you turned all the machines off for the night and then were restarted.  If the first machine on can't find the MBL then it elects itself as the Master Browser for the network and re-populates the MBL.  This takes about 15 minutes.

I don't think the information you want is in a concise form.  It is spread among many documents and sometimes is totally undocumented.  If you want to read a good tutorial I suggest [**[COLOR="#FF8C00"]Samba by Example [/COLOR] **]("http://www.samba.org/samba/docs/man/Samba-Guide/") to start with.

---

