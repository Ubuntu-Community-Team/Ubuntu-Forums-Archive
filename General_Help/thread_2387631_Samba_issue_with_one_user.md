---
title: "Samba issue with one user"
date: 2018-03-21
forum: General Help
---

### Post by esheesle on 2018-03-21
I've had samba running for years now but for whatever reason, one specific user account (user2) has become problematic for me.  I'm including my smb config below.  So far I've deleted both the system and samba user account for this user and recreated.  Passwords are the same.  All other users can access the share just fine, but user2 always fails with no good reason beyond access not allowed.  Any ideas, because I'm stumped?

Thanks


```
[global]   workgroup = CYBERSTRIKE
   server string = ProfessorX
   security = user
   hosts allow = 192.168.1. 192.168.2. 192.168.100.
   load printers = yes
   log file = /var/log/samba/log.%m
   max log size = 50
;   password server = <NT-Server-Name>
;   realm = MY_REALM
;   passdb backend = tdbsam
;   passdb backend = smbpasswd
   socket options = TCP_NODELAY
;   interfaces = 192.168.12.2/24 192.168.13.2/24 
   dns proxy = no 


unix extensions = no
follow symlinks = yes
wide links = yes
idmap uid = 1000-1500
idmap gid = 1000-1500




#============================ Share Definitions ==============================
[homes]
   comment = Home Directories
   browseable = no
   writable = yes


[printers]
comment = All Printers
browsable = yes
guest ok = yes
path = /tmp
printable = yes
public = yes
writable = no
create mode = 0700
printcap name = /etc/printcap
print command = /usr/bin/lpr -P%p -r %s
printing = cups


[shared]
   comment = Shared Directory
   path = /shared
   valid users = user1 admin user2
   read only = no
   public = no
   writable = yes
   printable = no
   create mask = 0664
   directory mask = 0775
;   force group = +windows
;   force create mode = 0664
;   force directory mode = 0775



```

---

### Post by TheFu on 2018-03-21
workgroup needs to be on a separate line? 
Have you tried changing the order of the "valid users" setting?
My global section has:
```
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes 
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdate\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

```

By my needs are pretty simple.

---

