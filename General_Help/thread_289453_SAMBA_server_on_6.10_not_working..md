---
title: "SAMBA server on 6.10 not working."
date: 2006-10-31
forum: General Help
---

### Post by aparsons on 2006-10-31
I just built out a 6.10 Server and loaded samba on it.  I can browse to my samba share using my XP machine, but when I go into the folder, and type the root password, I get the following error:

"\\apkcfs1\music is not accessible.  You might not have permission to use this network resource.  Contact the administrator of this server to find out if you have access permissions"

SAMBA CONF:```
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
```

---

### Post by ltmon on 2006-10-31
Your configuration is about 10 times longer than mine (and with many more features I'm sure) so it's really a bit above my head.

Howeve, in case you are new to the distro, my first guess would be that the Ubuntu practice of making the root user being disabled by default is the problem.  Have you enabled the root account on the box?

L

---

### Post by aparsons on 2006-10-31
yes, root is enabled.

---

### Post by dannyboy79 on 2006-10-31
have you added the user you're trying to log into the server with to your your password file? sudo smbpasswd -a username, then enter the password twice, then sudo smbpasswd -e username to enable him. i would strongly suggest NOT using root as the user that yuou'll  use to connect to samba shares. if i were you i would setup the user and passwords exactly the same between winxp and linux that way you can forget about that being the problem. i would also suggest using the default passwd backend which smbpasswd instead of passdb backend = tdbsam, I found that to cause headaches for me and I don't know why but it justs worked for me when I removed passdb backend = tdbsam, which then it defaults to smbpasswd backend. also, you don't have a username.map file if your usernames and password are different between winbloz and linux, just create a file called exaclty username.map and put it in /etc/samba/ and then add this line to your smb.conf,  username map = /etc/samba/username.map
my file looks like this: 
daniel = "Daniel Arfsten"
daniel = daniel
root = administrator Administrator
nobody = guest pcguest smbguest Guest
which basically maps the guest account in linux to the guest account in winbloz and also the admin account. I also found that puttin in the guest account stuff helped, these 2 options in the global section:
    map to guest = Bad User
    guest account = nobody

and also adfding this to each share: 
guest = ok

that way it'll allow guests access but it's ok because it's only what the guest privalages are which is read only. also, to be on the safe side I added, hosts allow = 127.0.0.1 127.0.1.1 192.168. EXCEPT 192.168.0.20 
which allows everyone on  my internal network access to the shares except my roommate which her ip is the .20. Anyway, if you want anymore help let me know and I'll try to help you the best i can.

---

