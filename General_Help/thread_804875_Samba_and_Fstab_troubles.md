---
title: "Samba and Fstab troubles"
date: 2008-05-23
forum: General Help
---

### Post by chris86wm on 2008-05-23
First off I am using Gutsy.
I'm having trouble sharing a folder over my network using Samba. The folder is located on a second internal hard drive and is mounted to "/media/Share/Public". What I'm going for is to have the "Public" folder completely open and accessible to everyone on the network (read/write etc).

I have edited my fstab to auto mount the drive and I can read and write to it. However, when I attempt to right click and share the "Public" folder I get an error.

ERROR: 
[I]The folder contents could not be displayed
error accessing 'file:///media/Share/Public': Access denied[/I]

I usually have no problem with samba shares, but this one has me stumped.

Here is my smb.conf and fstab files:

**smb.conf**
```
global]
usershare owner only = False
    ; General server settings
    netbios name = UBUNTU
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Public]
    path = /media/Share/Public/
	public = yes
   	browseable = yes
    	read only = no
    	guest ok = yes
	guest only = yes
	guest account = nobody
    	create mask = 0644
    	directory mask = 0755

```

**Fstab**
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=6b0cd4ac-1b2f-44b7-9718-dd265d4829dc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=46A7-E353  /media/Share    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=68D4EAC5D4EA949A /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=b382305d-b173-49c9-8c76-d6d44e86a948 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hdb1 	/media/Share vfat rw,exec,auto,async,user,umask=000 0 0
```

---

### Post by chris86wm on 2008-05-23
bump.... anybody?

---

### Post by bodhi.zazen on 2008-05-23
Well, in fstab you have the hard drive mounted to /media/Share (not /media/Share/Public)

Where is /media/Share/Public ?

---

### Post by chris86wm on 2008-05-23
There are other folders in "Share" but "Public" is the one i want to share over the network.

...the hard drive is formatted as fat32 so I can "share" files between linux and windows

---

### Post by chris86wm on 2008-05-24
bump :popcorn:

---

### Post by bodhi.zazen on 2008-05-24
I do not see anything wrong with the config file.

My only other thoughts are :

1. Firewall ? do you have a firewall blocking the connection ?

2. Did you add a samba user on the server ?

---

