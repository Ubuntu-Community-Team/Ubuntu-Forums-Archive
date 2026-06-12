---
title: "samba help"
date: 2004-11-21
forum: General Help
---

### Post by danip on 2004-11-21
Im trying to set up my computer so that my room mates windows computer can access my home directory.  heres my smb.conf file.

```
; /etc/smb.conf
;
; Make sure and restart the server after making changes to this file, ex:
; /etc/rc.d/init.d/smb stop
; /etc/rc.d/init.d/smb start

[global]
; Uncomment this if you want a guest account
; guest account = nobody
   log file = /var/log/samba-log.%m
   lock directory = /var/lock/samba
   share modes = yes

[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mode = 0750
[tmp]
   comment = Temporary file space
   path = /tmp
   read only = no
   public = yes

[public]
   comment = Public Stuff
   path = /home/steve
   public = yes
   writable = yes
   printable = no
   write list = @ubuntu

```

I type in on his computer \\blackbetty\ and it brings up a box to type in a user name and password.  I try my username and password and it wont connect.  I try doing nothing and it wont connect.  What else do I need to do so he can connect. 

Also isnt there a way if i go computer>sysconfig>networking to set up my home directory for share.  Ive read a few things on it but i dont understand what i need to do there to set up it up.

---

### Post by oddabe19 on 2004-11-21
I get that same problem going WinXP=>Linux on ubuntu, I think it may be a bug, cause i've never had that problem before.

---

### Post by stoneguy on 2004-11-21
Can't give you a precise answer, but it's probably more complicated than that.

Things can differ with the Windows version and how login authentication occurs.

Also, smbpasswd command may come into play.

---

### Post by calvinpriest on 2004-11-22
Try the following:
smbpasswd -a username

Then have the Windows user try that username and password.

---

### Post by sect2k on 2004-11-22
If you dont need user authentication, try setting "security = share"
and add guest ok = yes under your [public] share.

This way user authentication is not needed.

This is my smb.conf:

[global]

## Browsing/Identification ###

  workgroup = HATCHBIT
  server string = %h (Samba, Ubuntu Linux)

; wins server = w.x.y.z
  dns proxy = no
  name resolve order = wins bcast


#### Debugging/Accounting ####

  log file = /var/log/samba/log.%m
  max log size = 1000
  syslog = 0

  panic action = /usr/share/samba/panic-action %d


####### Authentication #######

  security = share
  encrypt passwords = yes
  
  passdb backend = tdbsam

  obey pam restrictions = yes

  guest account = nobody
  invalid users = root


########## Printing ##########


######## File sharing ########
[Shared]
  path = /var/opt/shared
  guest ok = yes
  guest only = yes
  read only = no
  force create mode = 0777
  force directory mode = 0777

[Music]
  path = /mnt/win/D/Music
  guest ok = yes
  guest only = yes
  read only = yes

---

### Post by oddabe19 on 2004-11-22
we're talking about the /etc/samda/smb.conf  right? cause he was talking about /etc/smb.conf and i've never head of one there... did Ubuntu move it?

---

### Post by danip on 2004-11-22
Did not realize there was a file in /etc/samba/smb.conf  I read a quick tuoriol and it told me to place it in /etc/smb.conf

Now what if i just copied your smb.conf file would that work at all?

---

### Post by sect2k on 2004-11-22
You need to modify some settings, mainly the workgroup and settings under "File Sharing" (path being the most important), other than that, it should work.

Just keep in mind that my setup allows the connecting user full control over the shared directory, if you want to set up read only, use this in the shares section

[ShareName]
  path = /path/to/directory
  guest ok = yes
  guest only = yes
  read only = yes

This should give you a read only, public accessable, share.

Hope this helps.

LP,
Mitja

---

