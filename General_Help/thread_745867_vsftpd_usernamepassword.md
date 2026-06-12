---
title: "vsftpd username/password??"
date: 2008-04-05
forum: General Help
---

### Post by fondoo on 2008-04-05
i have successfully installed vsftpd on my ubuntu server.

i have edited /etc/vsftpd.conf 

disable anonymous login
and shared a new ftp folder.

now when i attempt to login to a windows system
[ftp://192.168.1.x](ftp://192.168.1.x)

it is requesting username/password

does anyone know where i can add username/passwords on the ubuntu server?

i tried login with the same username/password that i use to login to the ubuntu server, but it failed to log me in to the ubuntu ftp server.

thank in advance.

---

### Post by fsmithred on 2008-04-05
in vsftpd.conf:

```

# Local FTP user Settings
#
# Uncomment this to allow local users to log in.
local_enable=YES

```

If you have multiple users on your system, and you don't want all of them to have access, it gets trickier. Look at the chroot and umask options and be careful how you set things. Been awhile since I played with vsftp, so it's probably better if I don't say too much, or I might tell you something wrong.

---

