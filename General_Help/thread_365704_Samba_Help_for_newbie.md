---
title: "Samba Help for newbie"
date: 2007-02-19
forum: General Help
---

### Post by zimbie_z on 2007-02-19
Ok, now that I have tried one more thing with the same result I want to wave the gigantic WHITE SAMBA FLAG.

ERROR CONDITION that I have is this:
[COLOR="Red"]
Copying from Windows Pc to Ubuntu samba share---Cannot copy Filename: The specified network name is no longer available. [/COLOR] 

I copied this smb.conf and changed it for my setup 

[COLOR="Pink"]Here it is:[/COLOR]
[B]
[global]
; General server settings
netbios name = linuxpc
server string =
workgroup = mshome
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

[linuxshare]
comment = linuxshare
path = /media/windowshare/
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = uddlinux
force group = uddlinux
[/B]

My FSTAB is:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1	/media/windowshare	vfat	iocharset=utf8,umask=000	0	0

[COLOR="Red"]I am including this just in case the vfat is causing my problem.  I am trying to copy across files that are >4 gigs.  If the problem is vfat then what file system should I use?[/COLOR]

I have setup my entire network using static IP's.
I have given the same username and passwords to the UBUNTU and windows users.  

I have tried and UBUNTU SAMBA has beaten me.

If this is not enough info to help just let me know.

Please give basic commands I am still newbie.

Any help would be appreciated.

Thanks :)

---

### Post by jasutton on 2007-02-20
As far as I know, vfat (a.k.a., FAT32 in the windows world) can't handle files larger than 4 GB.  So, you'd need to use a different file system.  I recommend ext3 just for the standardness of it.  In any event, it really shouldn't matter to the client (windows machines connecting to the share) what filesystem you use, as those details are abstracted away by samba.

---

### Post by zimbie_z on 2007-02-20
Ok, I will change it to ext3 and post back the results.  

One thing that I need to add from my original post is that the file will begin to copy and will copy partially and then the error pops up.

---

### Post by zimbie_z on 2007-02-20
Yeha it was the file system.  Thanks for the reply jasutton.

---

### Post by quantboy on 2007-05-05
Thanks for the post.  Ran into the same problem with copying huge files.  Will try to switch filesystems.

---

