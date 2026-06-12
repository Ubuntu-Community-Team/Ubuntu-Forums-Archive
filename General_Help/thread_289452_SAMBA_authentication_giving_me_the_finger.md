---
title: "SAMBA authentication giving me the finger"
date: 2006-10-31
forum: General Help
---

### Post by aparsons on 2006-10-31
I just built out a 6.10 Server and loaded samba on it.  I can browse to my samba share using my XP machine, but when I go into the folder, and type the root password, I get the following error:

"\\apkcfs1\music is not accessible.  You might not have permission to use this network resource.  Contact the administrator of this server to find out if you have access permissions"



SAMBA CONF:
=========================
root@apkcfs1:/# cat /etc/samba/smb.conf
[global]
   workgroup = PARSONS
   netbios name = apkcfs1
   server string = %h server (Samba, Ubuntu)


   passdb backend = tdbsam
   security = user
   username map = /etc/samba/smbusers
   name resolve order = wins bcast hosts
   domain logons = yes
   preferred master = yes
   wins support = yes

   # Set CUPS for printing
   printcap name = CUPS
   printing = CUPS

   # Default logon
   logon drive = H:
   #logon script = scripts/logon.bat
   logon path = \\apkcfs1\profile\%U


   # Useradd scripts
   add user script = /usr/sbin/useradd -m %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usermod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000


   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
   passwd chat debug = yes
   unix password sync = yes

   # set the loglevel
   log level = 3


[homes]
   comment = Home
   valid users = %S
   read only = no
   browsable = no


[printers]
   comment = All Printers
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   browsable = no


[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   admin users = Administrator
   valid users = %U
   read only = no


[profile]
   comment = User profiles
   path = /home/samba/profiles
   valid users = %U
   create mode = 0600
   directory mode = 0700
   writable = yes
   browsable = no

[music]
  comment = Music
  path = /data/music
  valid users = @users
  force group = users
  create mask = 0660
  directory mask = 0771
  writable = yes
=======================

My directory permissions:
root@apkcfs1:/# ls -la / | grep -i data
drwxrwxr-x  7 root root   160 2006-10-30 23:01 data
root@apkcfs1:/# ls -la /data
total 4
drwxrwxr-x  7 root root   160 2006-10-30 23:01 .
drwxr-xr-x 23 root root   616 2006-10-28 15:34 ..
drwxrwxr-x  2 root users   48 2006-10-30 23:01 music
drwxrwxrwx  3 root root  1552 2006-06-17 12:20 myth_backup
drwxrwxrwx  2 root root  2480 2006-06-16 23:15 video


Any help would be greatly appreciated.

---

