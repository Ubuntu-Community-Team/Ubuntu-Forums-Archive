---
title: "Can connect to shared folders with group users but not the create user"
date: 2013-11-20
forum: General Help
---

### Post by woznicbh on 2013-11-20
I am on Ubuntu desktop 12.04 and I am in the process of building a media server to house all my movies and files and serve them up to a number of different devices most of which being windows pcs. I have a drive (Media) that contains my movies and tv shows. Those folders are shared and can be accessed by group members but not the owner of the folder who is also part of that same group.


File permissions for folder: ls -l /media/Media/ 


    drwxr-xr-x 1 woznicbh media 163840 Nov 16 02:21 Movies
    drwxr-xr-x 1 woznicbh media      0 Nov 15 19:24 $RECYCLE.BIN
    drwxr-xr-x 1 woznicbh media      0 Nov 15 19:24 System Volume Information
    drwxr-xr-x 1 woznicbh media   4096 Nov 15 19:49 TV


Fstab output


    # /etc/fstab: static file system information.
    #
    # <file system> <mount point>   <type>  <options>       <dump>  <pass>


    proc	/proc	proc	nodev,noexec,nosuid	0	0
    #Entry for /dev/sdb1 :
    UUID=042d522c-c0ad-41e2-9bef-c6860fb4bc70	/	ext4	errors=remount-ro	0	1
    #Entry for /dev/sda1 :
    UUID=467CFDBB6D579AAB	/media/sda1	ntfs    uid=1000,gid=1003,umask=0000,sync,auto,rw	0       0
    #Entry for /dev/sdb5 :
    UUID=3a2ce524-f1a6-4a2a-985b-7e311d1524d5	none	swap	sw	0	0
    #Entry for Media:
    UUID=7E48EB6748EB1D21	/media/Media	ntfs	uid=1000,gid=1003,umask=0022,sync,auto,rw       0       0


blkid


    /dev/sdb1: UUID="042d522c-c0ad-41e2-9bef-c6860fb4bc70" TYPE="ext4" 
    /dev/sdb5: UUID="3a2ce524-f1a6-4a2a-985b-7e311d1524d5" TYPE="swap" 
    /dev/sdc1: LABEL="System Reserved" UUID="7C340E18340DD5D4" TYPE="ntfs" 
    /dev/sdc2: LABEL="Media" UUID="7E48EB6748EB1D21" TYPE="ntfs" 
    /dev/sda1: LABEL="Files" UUID="467CFDBB6D579AAB" TYPE="ntfs"


And lastly my smb.conf output


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
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:*%n\n*password\supdated\ssuccessfully* .
	obey pam restrictions = yes
	map to guest = bad user
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
    ;	passdb backend = tdbsam
 	wins support = true
 	dns proxy = no
    ;	netbios name = mediaserver
	server string = Media Server
	unix password sync = yes
	workgroup = BRETSGROUP
    ;	os level = 20
	security = share
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	usershare allow guests = yes
	max log size = 1000
	pam password change = yes
	usershare owner only = false


    ## Browsing/Identification ###


    # Change this to the workgroup/NT-domain name your Samba server will part of


    # server string is the equivalent of the NT Description field


    # Windows Internet Name Serving Support Section:
    # WINS Support - Tells the NMBD component of Samba to enable its WINS Server
    #   wins support = no


    # WINS Server - Tells the NMBD components of Samba to be a WINS Client
    # Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
    ;   wins server = w.x.y.z


    # This will prevent nmbd to search for NetBIOS names through DNS.


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


    # Cap the size of the individual log files (in KiB).


    # If you want Samba to only log through syslog then set the following
    # parameter to 'yes'.
    #   syslog only = no


    # We want Samba to log a minimum amount of information to syslog. Everything
    # should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
    # through syslog you should set the following parameter to something higher.


    # Do something sensible when Samba crashes: mail the admin a backtrace




    ####### Authentication #######


    # "security = user" is always a good idea. This will require a Unix account
    # in this server for every user accessing the server. See
    # /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
    # in the samba-doc package for details.
    #   security = user


    # You may wish to use password encryption.  See the section on
    # 'encrypt passwords' in the smb.conf(5) manpage before enabling.


    # If you are using encrypted passwords, Samba will need to know what
    # password database type you are using.  




    # This boolean parameter controls whether Samba attempts to sync the Unix
    # password with the SMB password when the encrypted SMB password in the
    # passdb is changed.


    # For Unix password sync to work on a Debian GNU/Linux system, the following
    # parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
    # sending the correct chat script for the passwd program in Debian Sarge).


    # This boolean controls whether PAM will be used for password changes
    # when requested by an SMB client instead of the program listed in
    # 'passwd program'. The default is 'no'.


    # This option controls how unsuccessful authentication attempts are mapped
    # to anonymous connections


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
    ;	printing = cups
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
    ;	usershare max shares = 100
 
    # Allow users who've been granted usershare privileges to create
    # public shares, not just authenticated ones


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
    ;	guest ok = no
    ;	read only = yes
	create mask = 0700


    # Windows clients look for this share name as a source of downloadable
    # printer drivers
    [print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
    ;	browseable = yes
    ;	read only = yes
    ;	guest ok = no
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




    [TV]
	path = /media/Media/TV




    [Documents]
	path = /home/woznicbh/Documents
    ;	writeable = No
    ;	browseable = yes
	guest ok = yes


    [test]
	path = /media/sda1/test
	writeable = yes
    ;	browseable = yes
	guest ok = yes


    [Movies]
	path = /media/Media/Movies

---

### Post by bab1 on 2013-11-21
> **woznicbh said:**
> I am on Ubuntu desktop 12.04 and I am in the process of building a media server to house all my movies and files and serve them up to a number of different devices most of which being windows pcs. I have a drive (Media) that contains my movies and tv shows. Those folders are shared and can be accessed by group members but not the owner of the folder who is also part of that same group.


File permissions for folder: ```
ls -l /media/Media/ 

    drwxr-xr-x 1 woznicbh media 163840 Nov 16 02:21 Movies
    drwxr-xr-x 1 woznicbh media      0 Nov 15 19:24 $RECYCLE.BIN
    drwxr-xr-x 1 woznicbh media      0 Nov 15 19:24 System Volume Information
    drwxr-xr-x 1 woznicbh media   4096 Nov 15 19:49 TV
```


Judging by this, the Ubuntu user *woznicbh* has authorization to access to everything in both Movies and TV,  This is because the owner, group and other all have the eXecute bit set on those directories.  This view is from the localhosts CLI and does not take into account any Samba authentication.

Does the user woznicbh have uid = 1000?  We can see that with this command ```
getent passwd woznicbh
```
Is the user woznicbh also a Samba user?   We can see that with this command```
sudo pdbedit -L
```
> 


Fstab output
```

    #Entry for /dev/sda1 :
    UUID=467CFDBB6D579AAB	/media/sda1	ntfs    uid=1000,gid=1003,umask=0000,sync,auto,rw	0       0

    #Entry for Media:
    UUID=7E48EB6748EB1D21	/media/Media	ntfs	uid=1000,gid=1003,umask=0022,sync,auto,rw       0       0

```

This shows that user 1000 and the group 1003 owners of the root directory of the 2 file systems (sda1 and Media) on the localhost
> 

blkid
 ```

   /dev/sdc2: LABEL="Media" UUID="7E48EB6748EB1D21" TYPE="ntfs" 

    /dev/sda1: LABEL="Files" UUID="467CFDBB6D579AAB" TYPE="ntfs"
```

This shows that the UUID and Lable of both partitions used as Samba shares.  Comment:  I would have named these to match the mount point at which each was mounted  (sda1 would be TV ). 


And lastly my smb.conf output

```

    [global]

 	wins support = true  [COLOR="#FF0000"]<-- Why this?[/COLOR]

    ;	netbios name = mediaserver  [COLOR="#FF0000"]<-- Why NOT this?[/COLOR]
	server string = Media Server
	unix password sync = yes
	workgroup = BRETSGROUP

    # "security = user" is always a good idea. This will require a Unix account
    # in this server for every user accessing the server. See
    # /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
    # in the samba-doc package for details.
    #   security = user
 
	security = share  [COLOR="#FF0000"]<-- For Samba authentication you need to use *_user_* here (see the above comments)
[/COLOR]

    ## Browsing/Identification ###

    ;   name resolve order = lmhosts host wins bcast [COLOR="#FF0000"]<-- This can be either "host bcast" or bcast alone and uncommented [/COLOR]


    [TV]
	path = /media/Media/TV [COLOR="#FF0000"]<-- Why no authentication parameters with this share[/COLOR]




    [Documents] [COLOR="#FF0000"]<-- Same thing here as above.  Why do you need to use guest on a private directory?  
                There are better ways of doing this[/COLOR]
	path = /home/woznicbh/Documents
    ;	writeable = No
    ;	browseable = yes
	guest ok = yes


    [test]  [COLOR="#FF0000"]<-- And again here ???[/COLOR]
	path = /media/sda1/test
	writeable = yes
    ;	browseable = yes
	guest ok = yes


    [Movies]  [COLOR="#FF0000"]<-- And here too ???[/COLOR]
	path = /media/Media/Movies
```


It would be better to use Samba user authentication (who are you).  This requires the user to be a Linux user and a Samba user.  The you use the file permissions for authorization (what you can do).  I would not mount anything in /media via fstab.  This directory is reserved for removable media (flash drives or portable USB HDD or SSD).  I usually store all shared data at /srv/samba.  If you have a partition you wish to mount it can be at /srv if you like.  You can make public directories (for all users) and private directories ( for specific users) via the smb.conf file.

I'd need to know more of what you are trying to do to provide a specific system design.  How many remote users?  How much security do you need for these users?  Is your private data (/home stuff) just for you?

---

