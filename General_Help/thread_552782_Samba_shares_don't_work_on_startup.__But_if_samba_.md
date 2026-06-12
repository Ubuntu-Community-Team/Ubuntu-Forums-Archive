---
title: "Samba shares don't work on startup.  But if samba is restarted they work."
date: 2007-09-16
forum: General Help
---

### Post by jake on 2007-09-16
I have a small problem with my samba shares.  I am sharing a folders with my wife's XP home machine.  When I first start up Ubuntu and try to connect from the windows machine it can't find the Linux machine on the network.  If I attempt to mount the samba shares of the Ubuntu machine on the Ubuntu machine it also fails.  If I go to the Ubuntu machine and restart samba then things start working and I am able to share folders and things seem to be working normally.  From the XP machine I can ping the Ubuntu machine so I know it exists on the network.  On the Ubuntu machine I can also mount the shares from the XP machine.  I can log into it via ssh so I know that at least some of the services are running.  I set this up using the HOWTO here:

[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

My smb.conf is below if there is something off there.

```

[global]
panic action = /usr/share/samba/panic-action %d
workgroup = MSHOME
netbios name = JAKECOMP
server string = jake linux computer
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = tdbsam
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
;obey pam restrictions = yes
;pam password change = no
null passwords = yes
interfaces = eth0, lo
bind interfaces only = yes
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

#Share Definitions

[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = yes
    read only = no
    veto files = /*.{*}/.*/mail/bin/

[MyFiles]
    path = /media/media
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = andersj
    force group = andersj

```

I run Kubuntu if it matters.  If anyone can point me in the right direction I would greatly appreciate it.

Thanks,
Jake

---

### Post by HermanAB on 2007-09-16
Check whether Samba is enabled to run on startup in the Services wizard.

Cheers,

H.

---

### Post by jake on 2007-09-17
It is enabled.  When I statup, I can find processes for samba when from ps -e.

---

