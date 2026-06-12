---
title: "easy samba how to"
date: 2008-05-26
forum: General Help
---

### Post by chrismitt2002 on 2008-05-26
to set up samba share do this .....................

Change owner to your username

```
sudo apt-get install samba smbfs smbclient
```

move smb.conf to samba folder enter this command - copy and paste entire LINE

```
sudo rm /etc/samba/smb.conf; sudo cp /home/owner/Desktop/smb.conf /etc/samba/
```
                                           ^^^^^^^^^^
                                     or folder that its located in
                                               
enable user name 

```
sudo smbpasswd -L -a username

```
```
sudo smbpasswd -L -e username
```

to restart samba 


```
sudo /etc/init.d/samba restart
```

to stop samba 

```
sudo /etc/init.d/samba stop
```

also linux hates windows shares with spaces in shares show use -or_ insted



[global]
    ; General server settings
    netbios name = pcname
    server string =
    workgroup = workgroup name
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



;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/



;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no


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


[network-share]
	path = /home/owner/my-share/
	browseable = yes
	ready only = no
	guest ok = no
	create mask = 0644
	directory mask = 0755
	force user = owner
	force group = work group name

---

