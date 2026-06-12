---
title: "Samba"
date: 2007-11-12
forum: General Help
---

### Post by Necromantis on 2007-11-12
I've try to get Samba to work all day and it's still not working..

I've created a user john and made a smbpasswd -e john (no password where asked at that point it just said account activated) and a smbpasswd -a john (asked for a password) so that part should be fine.

smb.conf looks like this:

[global]
workgroup = msnhome
netbios name = debian server
encrypt password = yes

[websites]
path=/websites
read only = no
browseable = yes
write list = john

What I get is:
I can see the server on the network from windows XP
When I try to connect I am prompted for a username and password
If i give the wrong credentials I don't get access
when I give the correct username (john) and correct password I can browse the folder and sub folders but I can't delete copy files or create files.

I would really appreciate some help; I can't see why this isn't working :confused:

---

### Post by Necromantis on 2007-11-12
Finally got it working.. 

sudo chown -R john /websites

Basically I had to set john as the owner of the folder and sub to be allow to modify it. Really strange this...

---

### Post by satx on 2007-11-12
Download SMB4K. Great tool, simplifies SAMBA management. Also, I have found that static IP addresses work better- get a DHCP address, then use that to setup static IPs.

My smb.conf file:

[global]
    ; General server settings
    netbios name = UBUNTU-VII
    server string = UBUNTU-VII
    workgroup = DOGNET
    interfaces = lo, eth0
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    
    encrypt passwords = true
    smb passwd file = /etc/smbpasswd
    dns proxy = no
    preserve case = yes
    short preserve case = yes
    default case = lower
    
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


[UBUNTU]
    path = /home/michael
    browseable = yes
    available = yes
    writable = yes    
    guest ok = no
    public = yes
    create mask = 0664
    directory mask = 0775
    ;force user = michael
    ;force group = michael




SATX

---

### Post by JetskiDude911 on 2007-11-12
I use to have problems getting Samba to work. The last time I tried it was with Red Hat 8, not sure if it's changed much since then or not.

---

