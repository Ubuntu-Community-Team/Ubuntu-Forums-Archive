---
title: "Nearly There With VMware!"
date: 2006-12-16
forum: General Help
---

### Post by happy-and-lost on 2006-12-16
I'm *nearly* done sharing files between Ubuntu (host) and XP Pro (Guest). I can see my Ubuntu host in the Network Connections of Windows, but nothing more :(

Here's my smb.conf

```
[global]
;General server settings
netbios name = Ubuntu
workgroup = Mshome
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

; NOTE: Inside this place you may build a printer driver repository for Windows 
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

[MyFiles]
path = /home/jo
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = Jo
force group = Jo
available = yes
public = yes
writable = yes

```

---

### Post by chalex on 2006-12-16
Did you tell the samba daemon to re-read the configuration?

Probably something like `sudo /etc/init.d/samba restart`

---

### Post by Mike'sHardLinux on 2006-12-16
Since you are doing user-level security, you need to add a user into the Samba userlist, In the console, you type:    sudo smbpasswd -a username

After you enter the password for sudo, It will prompt for a password for the samba user, twice. When that part is done, that is the username and password to use from the XP guest.

---

