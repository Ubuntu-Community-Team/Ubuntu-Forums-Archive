---
title: "Help with samba configuration"
date: 2007-06-20
forum: General Help
---

### Post by vladk2k on 2007-06-20
Hello. I have a server running ubuntu edgy (server) and I want to make it a storage facility for my windows network.

Right now, I have a few folders that are shared to four "trusted users" - meaning they can change stuff like rename, delete, move, add etc.
What I want is to add some untrusted user, either as guest (so that when they connect they do not need to supply any credentials) or as a simple username (say, username guest, password guest)
Below is my current smb.conf file:
```
[global]
    ; General server settings
    netbios name = K2Kserver
    server string = K2Kserver
    workgroup = RETEA
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
;    printer admin = @lpadmin

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
    browseable = yes
    public = yes
    guest ok = yes
    printable = yes

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Fisiere]
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = vladk2k
    force group = vladk2k

[Vlad-home]
    path = /home/vladk2k/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = vladk2k
    force group = vladk2k

[FTP]
    path = /home/ftp/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = vladk2k
    force group = vladk2k

[Everyone]
    path = /home/samba/ev
    browseable = yes
    read only = yes
    guest ok = yes
    create mask = 0644
    directory mask = 0755

```

What I want specifically is that users **vladk2k**, **mama**, **tata** and **radu** to be allowed write access to ***Fisiere*** and make the folder writeable for anyone else. In change, ***Everyone*** should have full access for anyone.
Also, the access to the printer should be restricted to those four users.
Access to Vlad-home only for user **vladk2k** (but I could easily dispose of the share, and edit stuff through ssh).

So, to wrap things up:
Fisiere - writeable by the four users, viewable by anyone
Everyone - writeable by anyone
Vlad-home - viewable/writeable by vladk2k
FTP - doesn't matter
Printer - viewable/writeable by the four users

I have added a user **guest** with password *guest*
I have tried different things - like changing security from *user* to *share*, using *wirte list = vladk2k,mama,tata,radu*, using *public = yes*, but all I manage is either everyone has write permissions to a share, or nobody has write permissions

---

### Post by ukripper on 2007-06-20
Why dont u add following in your smb.conf :
```
[guest]
    path = /home/samba/ev
    browseable = yes
    read only = yes
    create mask = 0400
    directory mask = 0400
```

---

### Post by nymphaeles on 2007-06-20
You may want to set permissions to control who can do what in your shares.  Use commands chown & chmod to do that.  For example:

```

chown -R root:users /path_to_share1
chmod -R ug+rwx,o+rx-w /path_to_share1

```

That will set permission for all in users to have write access.  For the meaning of the parameters, do a

```

man chmod

```

Don't forget to create users, for example:

```

useradd user1 -m -G users
useradd user2 -m -G readgroup

```


And set their smb passwords

```

smbpasswd -a user1

```

---

