---
title: "my windows shares are not working with xbmc"
date: 2006-08-22
forum: General Help
---

### Post by onesojourner on 2006-08-22
when I ran breezy I had no problems sharing files with smb so my sbox running xbmc could read them, now it does not work. In breezy I could just right click share folder > smb and it was all set up and worked great =D> . dapper does not. when I try to share my mp3s (they are on an ntfs partition) I can see the folder is shared but I cannot access it. I have tried and tried. my folder I am trying to share is showing up on my xbox but it says share unavailable. I think dapper must be adding some sort of security to make things more complicated. I dont need any security on this. I just want anything to have read access. 

I have read through a few other posts trying to fix this so I tried manually configuring my /etc/samba/smb.conf


[music]
path = /media/hdb1/music
available = yes
browseable = yes
public = yes
writable = no

with this set up I get the share unavailable error. this is how dapper set it up.


[music]
    path = /media/hdb1/music
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = peter
    force group = MSHOME
available = yes
public = yes
writable = no

this is where I tried to follow some how-to on setting it up and this gives me no output at all when I try to open it on the xbox, I can try to open the folder all day and nothing happens.

---

### Post by onesojourner on 2006-08-23
does any one have any ideas on this? surely there is a simple fix?

---

### Post by OrganicPanda on 2006-08-23
I share my files in dapper to my xbox: [http://ubuntuforums.org/showpost.php?p=1387072&postcount=4](http://ubuntuforums.org/showpost.php?p=1387072&postcount=4) That post indicates my mounting / share situation which is working flawlessly, Hope it is of use to you.

---

### Post by onesojourner on 2006-08-31
ok I have figured some things out. The shares I need to mount are on hdb1. when I right click and the folder to share it through the gui it is making it point to my home folder rather than the folder on the partition. every share I make comes up in my  /etc/samba/smb.conf comes up mapped to /home/peter .  I have tried to manually put in the what I think should be the correct path but it fails /media/hdb1/mp3s . what is the correct path to my other partitions?

---

### Post by dannyboy79 on 2006-08-31
onesojourner, check out this website, it'll help you set up samba printing and file sharing. I have everything set up great on my network and I have 2 xbox's, 1 Xubuntu wireless laptop, 1 ubuntu desktop, 1 winxp pro and they all talk and print nicely due to this guide. Good luck.

---

### Post by dannyboy79 on 2006-08-31
dah, forgot to attach it. SORRY!

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/54415-fileserver-samba-printserver-cups-howto.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/54415-fileserver-samba-printserver-cups-howto.html)

---

### Post by onesojourner on 2006-08-31
I have actually seen that one in my google searches, but it still does not help me get past the problem of all my shares on other partitions pointing to my home folder.

---

### Post by dannyboy79 on 2006-09-01
Well I think you may be using the wrong terminology. Linux isn't like windows, when you store stuff in a folder on linux you're aren't really storing it in that folder, you're storing it on a particular partition. You're saying that the INFO you want to share is located within partition hdb1. Ok, currently what folder (folders are no more than mount points) does your fstab say to mount hdb1???  So if currently all your music is located within hdb1 and your fstab says to mount hdb1 to your /home/usernamer folder than all your music should be there bottom line. Your parition doesn't contain folders, only your computer contains folders and it sounds like you have created the folders within your home directory which is normal. Really all your info is next to each other on a partition but you create folders to seperate it within linux. So when you click on a folder and say to share it, that folder should be shared and only have the files that you saved within it available. So you either need to change your mount point for your ntfs partition to /media/hdb1/music if that's what you want (make sure that folder is created first) or you need to mount your ntfs partition to a different folder again making sure that folder is there first. Then once you have done this, then you will want to click on that folder and share it and everything should be gravy.

---

### Post by onesojourner on 2006-09-01
hdb1 is an ntfs drive from my windows days. I have not created anything on this drive for over a year. It has been the same since I started using breezy RC1. with breezy I just right clicked hit share and bam it was shared on the network. the mount point of the drive is at /media/hdb1/ thats where dapper put it on the initial install.

so I think you may be saying an option would be to completely unmount hdb1 from my media folder and mount it directly in my home folder? I am going to start searching around for how to do that if that sounds like the best plan of attack to you.

---

### Post by modafokaxx on 2006-09-01
hmm, just a possibility, as it just worked for me, did you add the xbox user to samba with the following command?
```
smbpasswd -a user_name
```

which be with a usual xbox setting would go:
```
sudo smbpasswd -a xbox
```
and then entering the usual xbox password, "xbox".

I wasn't able to access my shares from XBMC untill 10 minutes ago before I read this thread, shares I had originally set up to work with windows 2000, and by adding the user to Ubuntu's samba, it worked. (I don't know if it's related to the fact that earlier on I added a ubunutu user called xbox, I'll try removing that user to see if it changes anything)

---

### Post by onesojourner on 2006-09-03
are you saying I dapper is trying to make my xbox use a password to access my network shares? If so I want to know how to turn that off. I want any computer to be able to access my shares with out any password.

---

### Post by modafokaxx on 2006-09-03
I don't know if samba in dapper is doing that by default, it would make sens as a security measure. I know I have password set up for my xbmc shares, and after doing what I said, it worked.

---

### Post by onesojourner on 2006-09-04
what do I need to do to set the password in xbmc? I would prefer to not have one but if that will get it working I am willing to give that route a shot.

---

### Post by dannyboy79 on 2006-09-06
the password is stored within your xboxmediacenter.xml, what you need to do is ftp into your xbox and copy a file that looks very similar to the name I have stated above, "xboxmediacenter.xml", most likely it is this exact name, copy it over onto your computer. then open it with either notepad or wordpad. then scroll down until you find a section that states username and password, you can do a search or find in wordpad I believe, then just change the password to whatever you want. I don't think you can leave it blank. also, make sure you don't accidentally delete any special characters or change the structure of the .xml file in any way, there are gonna be <, >, and other wierd things like that and you need to make sure you don't delete any of those. then save the file, then upload it back into your xbox into the same folder it used to be in. turn off your xbox and then turn it back on and your xbmx should now have it's new password. I just realized that this is the password for ftping into your xbox, I am sorry but I don't know how you change or set a password for being able to see your xbox within a network. to be honest I don't think you can, the only way that I have ever transfered files is by ftp from my computer. the other way would be to use a file manager and I think you could setup your xbox to see you network and then on the left would be your xbox and on the right would be whereever you set it to. You go to a file manager and hit the white or black button and it brings up a menu, then pick connect to server and you enter the ip I believe. Other than that I can't help you anymore, as I said I just always ftp into and out of my xbox. Later

---

### Post by onesojourner on 2006-09-12
everything is fine on the other computers/xbox in the network. I streamed a movie from my desktop on the ubuntu machine last night it has something to do with ubuntu not letting me share anything outside of my home directory. there has to be a simple reason why it wont let me do that.

here is my smb.conf again

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = MSHOME

# server string is the equivalent of the NT Description field
server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
; wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
; wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
; name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
; interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself. However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
; bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
; syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
# in the samba-doc package for details.
# security = user

# You may wish to use password encryption. See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
encrypt passwords = false

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
passdb backend = tdbsam

obey pam restrictions = yes

; guest account = yes
invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
; unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
; pam password change = no

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
; domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
; logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
; logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
; logon drive = H:
; logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
; logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe. The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
; load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
; printing = bsd
; printcap name = /etc/printcap

# CUPS printing. See also the cupsaddsmb( manpage in the
# cupsys-client package.
; printing = cups
; printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
; printer admin = @lpadmin


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
; include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
# SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
; message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
; domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
; idmap uid = 10000-20000
; idmap gid = 10000-20000
; template shell = /bin/bash

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
; comment = Home Directories
; browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
; valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
; writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
; create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
; directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
; comment = Network Logon Service
; path = /home/samba/netlogon
; guest ok = yes
; writable = no
; share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
; comment = Users profiles
; path = /home/samba/profiles
; guest ok = no
; browseable = no
; create mask = 0600
; directory mask = 0700

wins support = no
[printers]
comment = All Printers
browseable = no
path = /tmp
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
; write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
; comment = Samba server's CD-ROM
; writable = no
; locking = no
; path = /cdrom
; public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
# cdrom share is accesed. For this to work /etc/fstab must contain
# an entry like this:
#
# /dev/scd0 /cdrom iso9660 defaults,noauto,ro,user 0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
# is mounted on /cdrom
#
; preexec = /bin/mount /cdrom
; postexec = /bin/umount /cdrom


[movies]
path = /media/hdb1/media/movies
comment = movies and tv shows
available = yes
browseable = yes
public = yes
writable = yes

#notice this was created by right clicking a folder on my desktop and it points straight to my home folder not the folder I tried to share, but am am able to browse to the folder since it is in home/desktop/test.
[test]
path = /home/peter
comment = test
available = yes
browseable = yes
public = yes
writable = no

---

