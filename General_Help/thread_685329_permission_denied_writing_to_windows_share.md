---
title: "permission denied writing to windows share"
date: 2008-02-02
forum: General Help
---

### Post by msknight on 2008-02-02
Hi Folks,

I've seen quite a few threads on this, but no answers that work for me.

Situation ... laptop changed from SuSE 10.1 to Gutsy 7.10 32 bit.

Action - opening up a window and connection to a windows share.  It asks for my credentials and I give them.  I can connect, browse the tree but I can't open any files or write to them.  No problems whatsoever under SuSE.

I've tried installing samba and smbfs and followed various instructions but there is no [home] section in my samba.conf file, and if I create one then I understand that is creating a share on the Ubuntu machine when in reality I need to get at the Windows share.

Anyone help please?

Michelle.

---

### Post by msknight on 2008-02-03
Bump

---

### Post by msknight on 2008-02-03
Bump - does no one know the answer to this?

---

### Post by msknight on 2008-02-04
Bump

---

### Post by beesthorpe on 2008-02-04
I second that bump  -   I've just had pretty much the same problem. In previous versions I've got Samba working using [[COLOR="Navy"]Stormbringer's instructions [/COLOR]]("http://ubuntuforums.org/showthread.php?t=202605")  but now it's behaving as msknight described.

---

### Post by msknight on 2008-02-04
Glad I'm not the only one with the problem.  The question is ... does anyone have the solition!
- yes, this is another bump, by the way.

---

### Post by Borbus on 2008-02-04
Is this a Windows server or samba?

---

### Post by msknight on 2008-02-04
It's a windows workstation.  I attach to shares on each others drives to swap files between them as I need.  The Linux laptop is my e-mail and communication station (which I take downstairs and stuff and also goes on the move to support my life) and the Windows 2000 pro is a PC that I use for gaming, writing, photograph editing, web design and stuff.  So I create with the Windows machine and communicate with the Linux laptop.

Connecting to a share on the Linux Laptop from the Windows machine was a no brainer, but the reverse is not possible.  Also, I have an Ubuntu server and I'm getting the same problem attaching to smb shares on that as well ... but I think that if I concentrate on the Windows/Linux side of it, then the connection to the Linux server will drop in to place.

In the end when Gimp can handle RAW and 16 bit, then the Windows machine will prety much have had its day, but until then I've got to work with both.

---

### Post by msknight on 2008-02-06
Bump again

---

### Post by msknight on 2008-02-07
bump again

---

### Post by msknight on 2008-02-08
bump

---

### Post by mbsullivan on 2008-02-08
Hi msknight,

Let's try from the command line and see what kind of messages you get.  

First, you may need to unmount the current mount point, if the samba share actually is getting mounted:

```
sudo umount -f [wherever it is]
```

Then, let's create a new point to mount to:

```
sudo mkdir /mnt/tmp
```

Next, try to mount the folder:

```
sudo mount -t smbfs //[MACHINE]/[FOLDER] /mnt/tmp
```

If you get a permission error, you could try:

```
sudo mount -t smbfs -o user=[WORKGROUP NAME]/[USER NAME],pass=[PASSWORD] //[MACHINE]/[FOLDER] /mnt/tmp
```

You can also try:

```
sudo mount -t cifs //[MACHINE]/[FOLDER] /mnt/tmp
```

Windows sharing is incredibly finicky... sometimes it'll work some days and not others. It's normally an issue of the Windows box, in my experience. Let me know what messages you get on the command line.

Mike

---

### Post by msknight on 2008-02-08
Hi Mike, thanks for helping.

The Windows share on the box has been very stable when connecting with SuSE over the three or four years I was running it.

I tried ...
```
sudo mount -t smbfs -o user=big-cats/administrator,pass=[PASSWORD] //michelle/c$ /mnt/michellec
```

... and it asked for the password again.  It then returned permission denied.  It is worth noting I went straight for this option because there is no equivalent account on the Windows box.  The windows box doesn't have much on it and doesn't go anywhere, so it automatically logs on with the local administrator account.  It logs on to the Linux server sabma storage for any important files, and Windows using an Ubuntu server share is great - no problems.

The Ubuntu laptop using the Windows share is another kettle of fish, though.  The laptop does go places, have my e-mails and therefore does have password accounts on it.

The mount -t cifs option gave..
"Mount error: could not find target server.  TCP name michelle/c$ not found
No ip address specified and hostname not found."

---

### Post by mbsullivan on 2008-02-08
Hi msknight,

From the looks of it, you're mounting a "default share", or entire drive, judging from the $ at the end of the filename... You can verify this by looking at the output of:

```
smbtree
```

One thing is that It should be possible to do what you want, and I'll play around with some things later. However, I've found it much easier just to mount a simple folder rather than an entire drive.

With CIFS, you should use the IP address... it seems to have issues with winbind addresses.  Also, you may need to use \$ for the $ character.

Let me know if you have any luck, or if you lower your standards and decide to mount a folder instead :)

Mike

---

### Post by tosk on 2008-02-08
I assume your Windows box has the correct permissions set for the shares in question?

Can you post your smb.conf and any relevant mount commands that you use to mount the shares?

Also, are the permissions on your laptop set correctly for the mount point?

---

### Post by msknight on 2008-02-10
Hi Folks,

The C$ share is a "default" share, it is just that the $ sign makes the share invisible during share browsing.  Many people don't even know the administrative share is set up as default on some versinos of Windows.  The permissions are correctly set from the Windows side as, as I mentioned, I've been doing this with SuSE for years. 

I tried the IP address with the CIFS share, but despite telling it the user name to use, it rpeatedly asked me for the password for michelle rather than administrator, which is the account I need to connect with.

The actual mounting, etc. is being done as root so there should be no permissions problems from the point of view of making the mount itself.  

If I try smb via konqueror then it asks for credentials and it will let me get at the share, but I just can't write anything.

Here is the smb.conf file without the comments...
```
#======================= Global Settings =======================

[global]

   workgroup = big-catS

   server string = %h server (Samba, Ubuntu)

;   wins support = no

;   wins server = w.x.y.z

   dns proxy = no

;   name resolve order = lmhosts host wins bcast

#### Networking ####

;   interfaces = 127.0.0.0/8 eth0

;   bind interfaces only = true

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m

   max log size = 1000

;   syslog only = no

   syslog = 0

   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

   security = share

   encrypt passwords = true

   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

;   unix password sync = no

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .

;   pam password change = no

########## Domains ###########

;   domain logons = yes
;   logon path = \\%N\profiles\%U

;   logon path = \\%N\%U\profile

;   logon drive = H:
;   logon home = \\%N\%U

;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

;   load printers = yes

;   printing = bsd
;   printcap name = /etc/printcap

;   printing = cups
;   printcap name = cups

;   printer admin = @lpadmin

############ Misc ############

;   include = /home/samba/etc/smb.conf.%m

   socket options = TCP_NODELAY

;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

;   domain master = auto

;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;
; The following was the default behaviour in sarge
; but samba upstream reverted the default because it might induce
; performance issues in large organizations
; See #368251 for some of the consequences of *not* having
; this setting and smb.conf(5) for all details
;
;   winbind enum groups = yes
;   winbind enum users = yes

#======================= Share Definitions =======================

[homes]
   comment = Home Directories
   browseable = yes
   writable = yes
  read only = no
users = michelle
write list = michelle
security = user

;   valid users = %S

;   writable = no

;   create mask = 0700

;   directory mask = 0700

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
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

;   write list = root, @ntadmin


;[cdrom]
;   comment = Samba server's CD-ROM
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes


;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

```

---

### Post by msknight on 2008-02-11
bump

---

### Post by msknight on 2008-02-12
bump

---

### Post by linuxisfree on 2008-02-12
Just out of Curiousity, is [this]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+windows") on of the threads you've seen?

---

### Post by msknight on 2008-02-12
Hi,

I hadn't seen that ... but that is the wrong way.  My problem is writing/connecting to a Windows share.  I've got Windows to connect to Gusty with no problem, but not the other way around.

Michelle.

---

### Post by linuxisfree on 2008-02-12
Oh, i see... Sorry 'bout that! Anyway, when you supply the username and password that is asked, i'm assuming you supply the user and password of the windows computer, am i right or wrong?

---

### Post by BFris on 2008-02-13
Here's a nice link to the community docs:
   [https://help.ubuntu.com/community/MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")

I found the answer here. For me it was to use the noperm parameter. Worked a charm.

---

### Post by msknight on 2008-02-13
Many thanks, I'll go through that after work tonight and let you know how it went.

I've got to admit, though, that it is a long way from just giving a user name and password on connection and just being able to use the share.  This does seem a little over the top.

---

### Post by harrysales on 2008-02-14
I must be missing something but surely its a question of using the connect to server option in places. If it doesn't work study the logs in /var/log/syslog or the others in there use 'tail -n 20 /var/log/syslog' as root or sudo.

---

