---
title: "Samba Help"
date: 2007-02-15
forum: General Help
---

### Post by Word on 2007-02-15
I followed this [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) howto but I still can not access the files on my ubuntu laptop from a windows machine it give a you dont have permission error. I made a smb user account for the windows machine. Is there a everyone clause liek in windows you can say everyone has read write access. Thats what I want. Here is my smb file and the out put of # smbclient -L localhost -U%

************************************
[global]
; General server settings
netbios name = Magrathea
server string =
workgroup = pattonhome
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
interfaces = lo, eth0
bind interfaces only = true

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

[Magrathea]
path = /storage
browseable = yes
read only = no
guest ok = yes
create mask = 0777
directory mask = 0777
force user = kweli
force group = pattonhome
**************************************
Domain=[PATTONHOME] OS=[Unix] Server=[Samba 3.0.22]

Sharename Type Comment
--------- ---- -------
ADMIN$ IPC IPC Service ()
IPC$ IPC IPC Service ()
Magrathea Disk
print$ Disk
Domain=[PATTONHOME] OS=[Unix] Server=[Samba 3.0.22]

Server Comment
--------- -------
KWELIVIAO
MAGRATHEA
USER

Workgroup Master
--------- -------
PATTONHOME MAGRATHEA

**********************************************

---

### Post by tronica on 2007-02-15
you could try adding 

> valid user = username

which is the samba username

and add 

> writable = yes 

don't know if it will help, but that how i have mine set up

---

### Post by Word on 2007-02-15
> **tronica said:**
> you could try adding 



which is the samba username

and add 



don't know if it will help, but that how i have mine set up

that didnt work.

---

### Post by Word on 2007-02-18
anyone?

---

