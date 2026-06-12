---
title: "Samba Configuration"
date: 2006-11-20
forum: General Help
---

### Post by aparsons on 2006-11-20
I have a samba server, and am currently sharing out the following directory:

> 
/data/music.
aparsons@aphbgfs01:~$ ls -ltr /data
total 1
drwxrwx--x 23 aparsons users 648 2006-11-04 02:27 software
drwxrw-r--  4 rsync    users  96 2006-11-04 12:28 music
drwxrwx--x  8 aparsons users 224 2006-11-05 08:07 movies
drwxrwxr--  3 root     users  72 2006-11-20 10:47 scripts


My smb.conf file looks as such:
> 
[global]
   workgroup = PARSONS
   netbios name = aphbgfs01
   server string = %h Samba Server


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
   logon script = scripts/logon.bat
   logon path = \\aphbgfs1\profile\%U


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
  force user = rsync
  force group = users
  case sensitive = no
  #msdfs proxy = no
  guest ok = Yes
  writable = No


My question is:

How do I:

1. Allow the share to be read-only to all guests.
2. Only allow writes to the directory for specific users or a specific group of users.  
3.  If I force users to authenticate, how can I grab the username from the hostpc so that i don't have to force a username?  Forcing the rsync user was THE ONLY WAY I could have any user browse this share.

Thanks for all of the help!

---

