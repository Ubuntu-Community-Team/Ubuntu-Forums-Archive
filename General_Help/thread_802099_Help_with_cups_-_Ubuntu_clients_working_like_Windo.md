---
title: "Help with cups - Ubuntu clients working like Windows clients"
date: 2008-05-21
forum: General Help
---

### Post by Moso on 2008-05-21
Hi everbody!

I setup a Hardy server with a shared printer in cups/samba.

Print from Windows clients works without ask any user/password.  Cups logs the name of the current Windows user when jobs are submitted.

The "problem" is that Ubuntu clients must provide a user/password that exists in the server to be able to print.  I tried add the printer as a smb printer and as ipp printer and in both cases a user/password is needed.

Question is: what I need to do for Ubuntu clients work like the Windows clients when printing to this cups printer? (without ask user/password and using current Ubuntu username in job logs)

Thanks!

---

### Post by opscure on 2008-05-21
Is this a password for the printer itself or for the connection through samba? 

In the case of a samba password you would have to set the permissions of the location to 777 
```
sudo chmod -R 777 /folder/
or 
sudo chmod 777 file
```
to allow everyone (anonymous) access and configure your smb.conf in /etc/samba/ to allow anonymous access.  (always make a backup first)

if you find the line with
```
; security = user
```
and change it to 
```
; security = share
``` 
you will be able to allow for a connection without a user/pass.

---

### Post by Moso on 2008-05-21
Content of cupsd.conf:

```
LogLevel warning

SystemGroup lpadmin

Listen localhost:631
Listen 192.168.1.254:631
Listen /var/run/cups/cups.sock

Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

DefaultAuthType Basic

<Location />
  Order allow,deny
  Allow from 192.168.1.*
</Location>

<Location /admin>
  Order allow,deny
  Allow from 192.168.1.*
</Location>

<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
```

Content of printers.conf:

```
<Printer HP_LaserJet_1000>
Info HP LaserJet 1000
DeviceURI file:///dev/usb/lp0
State Idle
StateTime 1211296972
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
```

Content of smb.conf:

```
[global]
   workgroup = OFFICE
   server string = Samba on Ubuntu 8.04.1 Server
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   socket options = TCP_NODELAY
   usershare allow guests = yes

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
```

Windows clients that want to print can do it without supply any password and the cups server gets automatically the name of the Windows user that is sending the print job.

In my Ubuntu clients, when I add the printer via smb connection I must supply a username/password that exists in the Ubuntu server to print works.

It's a little office with a single Ubuntu 8.04.1 Server (text only) where the printer is attached and shared via cups/samba.  Windows clients send print jobs and whatever user is currently logged on Windows (Administrator, User_A, User_B, etc) goes to cups logs and prints ok.  Ubuntu 8.04 clients MUST supply a user/password to get print jobs to work.

The problem is that I needed to go to each one of my Ubuntu clients and set the only user/password that I got on my Ubuntu Server to allow these stations to print.  But each one of these Ubuntu clients have two or more local users and the way I need to setup printing on Ubuntu clients EVERY print job sent to the server appears to belong to that server's user I handed put in the Ubuntu clients.

I really like to know how to make Ubuntu clients print the same way Windows clients are printing: no username/password asked to print and the current local user name send as owner of the print job.

Thanks for your attention and tell me if more info are needed.

:lolflag:

---

### Post by Moso on 2008-05-22
I not find a solution yet...  :(

I installed from zero a Ubuntu Server 8.04.1 and a computer to act as client with dual-boot Windows XP Pro SP3/Ubuntu Desktop 8.04.

In Google I only find problems of Cups not printing or not sharing.  This particular problem - Windows can use printer "directly" and Ubuntu desktop must supply valid user/password - I don't find a solution or a explanation of why thing are this way.

I hope that someone here at forum can help... :guitar:

---

### Post by opscure on 2008-05-22
Do you have a guest account enabled for the printer on the server?

Check out the section about Enabling Anonymous Printing:
[http://www.samba.org/samba/docs/man/Samba3-HOWTO/StandAloneServer.html]("http://www.samba.org/samba/docs/man/Samba3-HOWTO/StandAloneServer.html#AnonPtrSvr")

---

### Post by Moso on 2008-05-22
Hi opscure! :)

Thanks for the link, I will read it and check/test.

But I insist in a point: why can't Ubuntu Desktop, when accessing the shared cups printer via samba act exactly the same way as the Windows XP clients?

The XP clients, when accessing the shared cups printer via samba only inform the username of the actual logged user.  No password informed/asked.  And the linux server does't check this user/password.

But Ubuntu desktop using the same way of access (samba) MUST provide user/password valid in the server...  :confused:

---

### Post by opscure on 2008-05-22
You may want to simplify your smb.conf and add things from there.  If you used a very simple smb.conf it may work.  Try:
```
[global]
workgroup = MIDEARTH 
netbios name = LUTHIEN 
security = share 
printcap name = cups 
disable spoolss = Yes 
show add printer wizard printing = cups

[printers]
comment = All Printers 
path = /var/spool/samba 
guest ok = Yes 
printable = Yes 
use client driver = Yes 
browseable = No
```
*Clearly enter your own system specific information*

and see if you can get access from all nodes.  Don't forget to backup your current file so it can be replaced if necessary.

As for you inquiry about the differences between the authentication methods for Windows and Linux, there are many differences and they can be found through the information on the samba website.  Also, samba codes specifically for the operating system it is dealing with and uses specific authentication means for both linux and windows... I'm not entirely sure why you aren't able to share the server with both OS's easily, but then again I'm not really able to play around with things on your end.

Samba's web site: [http://us1.samba.org/samba/](http://us1.samba.org/samba/) 
look at links section learning samba on the left.

Don't be afraid to try things, you know where the current state of your system is right now so just back up any file that you will attempt to better and if it stops working just revert.

Good luck.

---

### Post by mannheim on 2008-05-22
I've noticed this. I think it's a reason something like this (though I really don't know much about it).

When Windows machines are networked in a "workgroup" (a typical home network setup), then a user on Machine-A can access shared resources on Machine-B without supplying a password as long as the **username and password** of the user are the same on the two machines (and as long as the permissions allow). The reason is that the windows machines store a hash of the user's password, which is used in the authentication (somehow I don't understand): MachineA sends some info, based on the hash, to MachineB (which also has a stored password hash), and some authentication happens.

The samba server daemon on linux also stores a copy of password hash; so it can play the role of Machine-B here. This means that a Windows user account on MachineA can access samba shares on Machine-B. But it doesn't work the other way round: the usual linux setup on a client machine doesn't know anything about a Windows-type hash of any passwords, so can't use that to authenticate.

All this may be wrong! Someone who knows how this works might comment ...

---

### Post by Moso on 2008-05-23
Hi mannheim!  :)

I see your point but this is not the case.

All clients (Windows and Ubuntu) want to use the shared printer on the Ubuntu Server via cups/samba.

Windows clients can use the printer without being asked user/password ever one time.

Ubuntu clients MUST provide a user/password that exists as an account on server when adding the printer.

So, Windows clients use the printer with ANY local Windows user and without provide password.  Cups logs correctly the name of the Windows user that sended the job.

Ubuntu clients will always user that user/password provided when the printer were added to the Ubuntu client and all local users of the Ubuntu client that send jobs to the printer will be logged with the same user provided to add the printer...  :(

Still researching but... :confused:

---

### Post by Moso on 2008-05-25
Please, some Samba expert can help me with this question?

:popcorn:

---

### Post by Moso on 2008-05-26
bump! :(

---

### Post by opscure on 2008-05-28
I would take this question over to the samba mailing lists here:
[http://us1.samba.org/samba/archives.html](http://us1.samba.org/samba/archives.html)

Be sure to read the mailing list etiquette before you post.  Good luck with this issue.

---

