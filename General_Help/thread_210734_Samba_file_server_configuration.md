---
title: "Samba file server configuration"
date: 2006-07-07
forum: General Help
---

### Post by duralisis on 2006-07-07
I'm attempting to setup a file server using Samba for my company.  So we loaded Ubuntu 6.06 onto an old P3 system and now I'm trying to get Samba setup correctly to function as much like a Windows machine with shared folders as possible.

It should appear in My Network Places and have several shared folders so anybody can dump files into them or make new subdirectories.  This is only going to hold our temporary work directories and any shared resources we need to get at.  Security is not a consideration, it can be totally open as it's isolated behind our network.  Ideally it should function like a regular Windows shared folder and allow anyone to write to it without a username/password.

Problem:  I can get our server to show up in the workgroup, and see all its printers and the test shared folder, but I can't write to that share or make new directories in it (same for anyone on the network).

Here's my current 'smb.conf' without all the commenting:

```
[global]
   workgroup = KFI
   server string = FILE-SERVER
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = SHARE
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
   socket options = TCP_NODELAY
   wins support = no
   
[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[share]
   path = /home/kfi/share
   available = yes
   browseable = yes
   public = yes
   writable = yes
   guest ok = yes
   create mask = 0664
   directory mask = 0775
```

Changing the security to "SHARE" under global allowed the file server to show up in Network Places and the folders to be browsed, but after reading some of the confusing Samba docs, I am thinking this is not the correct method?

So what should I change?  How do I get this setup?  If I have to add users or logins, how do I do that and can everybody just use one?

Again I would like it to function as much as a plain Windows XP box with some folders shared.  That's all it has to do.

Thanks.

---

### Post by duralisis on 2006-07-07
Update:

I think I got it working (no thanks to you slobs!!! j/k :)).  I found a post over on the fedora forums that basically takes the same setup I have, but expands on it by adding a directory owned by a user that samba uses to create the share.  Basically I didn't know it, but the user is for the local machine and anyone who puts files in that share has their files "owned" on the server by that user even though you don't log in as a user.

Confusing to say the least...

Here's the post:  [http://www.fedoraforum.org/forum/showthread.php?t=19967](http://www.fedoraforum.org/forum/showthread.php?t=19967)

If you have trouble following it, remember to separate the commands you see with commas.  So use 'chown foo:bar" instead of "chown foo,bar" or 'chmod user /path' then 'chmod group /path' insted of 'chmod o+r...,g+...'.

---

### Post by evilgold on 2006-07-09
Thank you man, I was just totally looking to find out how to do this and you (and your link to the FC forums) saved the day :-)

---

