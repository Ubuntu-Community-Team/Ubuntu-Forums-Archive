---
title: "Win10 File Explorer sees Kubuntu 16.04 Samba Server but cannot Access Shares"
date: 2016-10-28
forum: General Help
---

### Post by gus_zernial on 2016-10-28
Win10 box(es) File Explorer(s) show Kubuntu 16.04 Samba Server (by name) but cannot Access Shares in the linux box (on the same private LAN). Tried multiple Win10 boxes. Kubuntu 16.04 Samba Server related info below:

$ sudo apt list | grep samba

dpsyco-samba/xenial,xenial 1.0.36 all
fusiondirectory-plugin-samba/xenial,xenial 1.0.8.8-3ubuntu2 all
fusiondirectory-plugin-samba-schema/xenial,xenial 1.0.8.8-3ubuntu2 all
gadmin-samba/xenial 0.3.2-0ubuntu1 amd64
gadmin-samba-dbg/xenial 0.3.2-0ubuntu1 amd64
gosa-plugin-samba/xenial,xenial 2.7.4+reloaded2-9ubuntu1 all
python-samba/xenial-updates,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.1 amd64 [installed,automatic]
samba/xenial-updates,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.1 amd64 [installed]
samba-common/xenial-updates,xenial-updates,xenial-security,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.1 all [installed]
samba-common-bin/xenial-updates,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.1 amd64 [installed,automatic]
samba-dbg/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.1 amd64
samba-dev/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.1 amd64
samba-dsdb-modules/xenial-updates,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.1 amd64 [installed,automatic]
samba-libs/xenial-updates,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.1 amd64 [installed]
samba-testsuite/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.1 amd64
samba-vfs-modules/xenial-updates,xenial-security,now 2:4.3.11+dfsg-0ubuntu0.16.04.1 amd64 [installed,automatic]
system-config-samba/xenial,xenial,now 1.2.63-0ubuntu6 all [installed]
vlc-plugin-samba/xenial,now 2.2.2-5 amd64 [installed,automatic]

$ps -ef | grep mbd
root      2142     1  0 12:14 ?        00:00:00 /usr/sbin/nmbd -D
root      2161     1  0 12:14 ?        00:00:00 /usr/sbin/smbd -D
root      2163  2161  0 12:14 ?        00:00:00 /usr/sbin/smbd -D
root      2179  2161  0 12:14 ?        00:00:00 /usr/sbin/smbd -D

$ cat /etc/samba/smb.conf

#======================= Global Settings =======================

[global]


   workgroup = workgroup


        server string = %h server (Samba, Ubuntu)

   dns proxy = no

#### Networking ####

hosts allow = 192.168.1.

   log file = /var/log/samba/log.%m

   max log size = 1000

   syslog = 0

   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

   server role = standalone server

   obey pam restrictions = yes

   unix password sync = yes

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

   pam password change = yes

   map to guest = bad user

########## Domains ###########

############ Misc ############

   usershare allow guests = yes

#======================= Share Definitions =======================


[homes]
;   comment = Home Directories
;   browseable = yes

[XXXX's Home]
   comment = XXXX's Home
   path = /home/XXXX
   available = yes
   browseable = yes
   read only = no
   guest ok = no

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[/tmp]
   comment = /tmp
   path = /tmp
   available = yes
   browseable = yes
   read only = no
   guest ok = no

---

### Post by SeijiSensei on 2016-10-29
Did you create matching Samba users with the smbpasswd command?  Try running "sudo smbpasswd XXXX" to create a corresponding Samba user for XXXX.

---

### Post by gus_zernial on 2016-10-29
The problem was my unix firewall. "sudo ufw allow Samba" solved the problem

---

