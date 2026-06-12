---
title: "Samba again-almost complete, but"
date: 2006-11-22
forum: General Help
---

### Post by DougieFresh4U on 2006-11-22
how do I find out if I have static IP? working on setting up Samba, but have a couple of minor issues. If I can get this question answered then I can ask the others. Thanks   "Patients"

---

### Post by Ramses de Norre on 2006-11-22
In an internal network? Set up static ip on all machines and give them all different ip's. They'll all ask their own ip from the router and they'll normally receive the ip they ask.

---

### Post by DougieFresh4U on 2006-11-22
while setting up samba in the gedit, it ask whether static IP -yes or no and I do not know if I use static IP

---

### Post by Ramses de Norre on 2006-11-22
The other thing is dhcp, look in system>admin>networking which you are using.

---

### Post by DougieFresh4U on 2006-11-22
Thank you.says dhcp in wired network

---

### Post by DougieFresh4U on 2006-11-22
some one please look this over as I am not sure what I am doing:::[global]
    ; General server settings
    netbios name = DougiesToyBox
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

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

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = dougie
    force group = dougie   -----------I have dchp and not static ip address. Also I am a bit confused about what I pu t in to the windows machine under  Map Network Drive. would be glad for any help

---

### Post by DougieFresh4U on 2006-11-22
taurus, I know your out there!! please check it out. also I tried nother disk today but it didn't have enough space for what I needed it for. Igot windows ok. I had put an edgy live cd in and for got, so when I finished tweaking map networking in windows and rebooted it was trying to boot cdrom. dah! I need to finish this Samba. please look at my gedit settings. I have to go out to a meeting but be back around in about 3-4 hours . thanks, Happy Thanksgiving

---

### Post by DougieFresh4U on 2006-11-23
It's a BUMPY road

---

