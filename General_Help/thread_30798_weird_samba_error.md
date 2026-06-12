---
title: "weird samba error"
date: 2005-04-30
forum: General Help
---

### Post by remmelt on 2005-04-30
hello

I have set my smb shares up to my liking, works fine with both XP and Ubuntu. The samba shares are on a Debian machine.
I have installed smbfs and have mounted the shares to a folder on my Ubuntu box. So far everything is fine.

The strange thing is: when I save a file with gedit, the rights get all mixed up. The mode is set to -rw--w----, but *only* when I take a look with ssh on the Debian machine, *not* on the Ubuntu side... There it just looks like -rw-rw-r-, which is good and what I set it to be. Chmodding helps from the Ubuntu side, but is rather annoying when you want to change a single character and check the file in a browser or sth.

When I save a file with vi, for example, the rights are fine. When I touch a file, the rights are set to -rw-r--r--... What is going on?

The line in fstab:
```
//deef/www      /var/www_deef           smbfs   _netdev,gid=users,credentials=/root/.smbpasswd,dmask=0775,fmask=0664        0       0
```

The smb.conf on the Debian machine:
```
[global]
   workgroup = WORKGROUP
   server string = %h
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

   encrypt passwords = true
   passdb backend = tdbsam guest
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

   socket options = TCP_NODELAY

[homes]
   comment = Home Directories
   browseable = no
   writable = yes
   create mask = 0600
   directory mask = 0700

[www]
        comment = www-root
        writable = yes
        path = /var/www/html
        public = yes
        create mask = 0664
        directory mask = 0775

[media]
        comment = Media op Deef
        writable = yes
        path = /var/media
        public = yes
        create mask = 0664

```

---

