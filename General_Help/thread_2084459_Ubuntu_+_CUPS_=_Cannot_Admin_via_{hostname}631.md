---
title: "Ubuntu + CUPS = Cannot Admin via {hostname}:631"
date: 2012-11-15
forum: General Help
---

### Post by LydaRA on 2012-11-15
PLEASE HELP!

I'm trying to build a new print server on Ubuntu 12.04 + CUPS.  (Coming over from other distros....want to standardize on Ubuntu, if I can make it work!)


I can use the basic Ubuntu System Settings to add a printer, but not the CUPS http://{hostname}:631 page for remote administration!  The page comes up and most functions appear fine.  

But try anything like the "Add Printer" button and a prompt asks "A username and password are being requested by [http://localhost:631](http://localhost:631).  The site says: "CUPS"--but then it doesn't appear to accepts ANY credentials (my sysop, root, nor Windows AD PrinterAdmins group members!!!  "The connection was reset" is all Firefox shows...  :-(

Any ideas are appreciated!

---

### Post by pkadeel on 2012-11-15
> **LydaRA said:**
> PLEASE HELP!

I'm trying to build a new print server on Ubuntu 12.04 + CUPS.  (Coming over from other distros....want to standardize on Ubuntu, if I can make it work!)


I can use the basic Ubuntu System Settings to add a printer, but not the CUPS http://{hostname}:631 page for remote administration!  The page comes up and most functions appear fine.  

But try anything like the "Add Printer" button and a prompt asks "A username and password are being requested by [http://localhost:631](http://localhost:631).  The site says: "CUPS"--but then it doesn't appear to accepts ANY credentials (my sysop, root, nor Windows AD PrinterAdmins group members!!!  "The connection was reset" is all Firefox shows...  :-(

Any ideas are appreciated!
It needs a user id and password of a user on the ubuntu machine.

---

### Post by LydaRA on 2012-11-15
Yes, I'm not even focused on the AD PrinterAdmins group yet.  But I cannot even get it to take root or sysop (obviously both local admin accounts on the Ubuntu server.

I saw somewhere else that I needed to add the local user cupsys to the shadow group.  But the command tells me that cupsys doesn't exist!

---

### Post by pkadeel on 2012-11-15
> I'm not even focused on the AD PrinterAdmins group yet.  But I cannot even get it to take root or sysopI couldn't exactly understand what you said sorry.
You can create a new user for accessing cups using the useradd command
or you can edit /etc/cups/cupsd.conf file and comment the "Require user @SYSTEM" for your desired portion i.e. change
```

  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

```to
```

  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
#    AuthType Default
#    Require user @SYSTEM
    Order allow,deny
  </Limit>

```while you are testing your system and have not started using it in production

---

### Post by LydaRA on 2012-11-15
cupsd.conf:

LogLevel warn
MaxLogSize 0
SystemGroup root sysop lpadmin HHP\PrinterAdmins
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseRemoteProtocols
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
DefaultAuthType Basic
WebInterface Yes
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow from @LOCAL
</Location>
<Location /admin>
  Order allow,deny
  Allow from @LOCAL
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow from @LOCAL
</Location>
<Policy default>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
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
<Policy authenticated>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

---

### Post by dannyboy79 on 2012-11-15
not sure this would help:
[http://ubuntuforums.org/showthread.php?p=1831119](http://ubuntuforums.org/showthread.php?p=1831119)

---

### Post by pkadeel on 2012-11-15
> **LydaRA said:**
> cupsd.conf:

LogLevel warn
MaxLogSize 0
SystemGroup root sysop lpadmin HHP\PrinterAdmins
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseRemoteProtocols
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
DefaultAuthType Basic
WebInterface Yes
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow from @LOCAL
</Location>
<Location /admin>
  Order allow,deny
  Allow from @LOCAL
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow from @LOCAL
</Location>
<Policy default>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
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
<Policy authenticated>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  [COLOR=Red]<Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>[/COLOR]
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
If I understood right and this is what you want then you have to change the highlighted text in the quote above to the below given text
```

<Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    #AuthType Default
    #Require user @SYSTEM
    Order deny,allow
  </Limit>

```

---

### Post by LydaRA on 2012-11-15
Yes, pkadeel--that did it!

So we've confirmed that the CUPS web services is still listening, but there is some authentication handling problem?  

What user does the CUPS process run as?  What permissions/group memberships does it need in Ubuntu?  (See my prior comment about "cupsys" not existing...)

---

### Post by LydaRA on 2012-11-15
dannyboy79:  You like several other posts I've seen recommend:  > **Allow CUPS to read the password file**
To do admin tasks remotely using the web interface, it will ask you for a password. In order to check this password CUPS needs to be able to read the password shadow file. To do this 'cupsys' needs to be a member of the group 'shadow'.

                [FONT=Lucida Console]adduser cupsys shadow[/FONT]

But I get:
> adduser: The user `cupsys' does not exist.


Does Ubuntu run this process as some other user???
[FONT=Lucida Console][/FONT]

---

### Post by pkadeel on 2012-11-15
> **LydaRA said:**
> dannyboy79:  You like several other posts I've seen recommend:  

But I get:



Does Ubuntu run this process as some other user???

the link dannyboy79 posted is a summarized version of a long manual.

My understanding is (I may be wrong) that cupsys user is not created automatically, you have to do it manually. After creating this user you assign the shadow group so that it can do the admin tasks.

You might be interested in the following ubuntu help page which eventually directs you to the CUPS Admin Manual here
[http://www.cups.org/doc-1.1/sam.html#13_4](http://www.cups.org/doc-1.1/sam.html#13_4)

Read these and you will understand what to do next. I hope the problem is solved.

---

### Post by LydaRA on 2012-11-15
I wish I did understand.  I've read the docs for 1.5 (the version bundled with Ubuntu 12.04).  And yet I don't see any mention of creating a user or specifying what user CUPS processes will run as.  I did see settings for authentication types to use the host UNIX users, but the system still doesn't seem to be able to handle comparing the incoming web credentials to the system and continue to the admin web pages...

I think this may be more of an issue with something about Ubuntu's setup of CUPS than CUPS internal?  Is there not a complete step-by-step guide for Ubuntu 12 installation of CUPS?

---

### Post by dannyboy79 on 2012-11-15
is there a lpadmin group? Add your username to that group.

here's the cups server guide for 12.04: [https://help.ubuntu.com/12.04/serverguide/cups.html](https://help.ubuntu.com/12.04/serverguide/cups.html)

---

### Post by redmk2 on 2012-11-15
> **dannyboy79 said:**
> is there a lpadmin group? Add your username to that group.

here's the cups server guide for 12.04: [https://help.ubuntu.com/12.04/serverguide/cups.html](https://help.ubuntu.com/12.04/serverguide/cups.html)
Exactly!

> [I][COLOR="DarkSlateGray"][I]**Configure printers**

This right is gained by adding the user to the "lpadmin" group.

Cups contains a setting called "SystemGroup" in the /etc/cusp/cupsd.conf that specifies who is allowed to manage printers. By default, it is set to "lpadmin". [/I][/COLOR][/I]

Search on *lpadmin *at [**_[COLOR="Blue"]this[/COLOR]_**]("https://wiki.ubuntu.com/Security/Privileges") site

---

### Post by LydaRA on 2012-11-15
Yes, the account is in the lpadmin group, as shown by 
> getent group | grep lpadmin
lpadmin:x:108:sysop,papercut,root


---

### Post by LydaRA on 2012-11-15
As posted earlier, I've also added root, sysop, and the Windows AD group to the SystemGroup line in cupsd.conf:
> SystemGroup root sysop lpadmin HHP\PrinterAdmins

Is that syntax correct?  Or is that a possible problem (listing UNIX users & groups, and AD users and groups together)?

---

### Post by redmk2 on 2012-11-15
> **LydaRA said:**
> As posted earlier, I've also added root, sysop, and the Windows AD group to the SystemGroup line in cupsd.conf:


Is that syntax correct?  Or is that a possible problem (listing UNIX users & groups, and AD users and groups together)?

No, the lpadmin group should hold only local users (from this localhost).  Linux has no nested groups.  I would expect that only users that have sudo rights can configure CUPS.  This means the user also should be a member of the sudo group (an administrator).  

lpadmin group```
redmk2@maui:~$ getent group|grep lpadmin
lpadmin:x:109:redmk2

```

Member of sudo group```
redmk2@maui:~$ getent group|grep sudo
sudo:x:27:redmk2

```

The groups redmk2 is a member of```
redmk2@maui:~$ getent group|grep redmk2
adm:x:4:redmk2
cdrom:x:24:redmk2
**sudo:x:27:redmk2**
dip:x:30:redmk2
plugdev:x:46:redmk2
**lpadmin:x:109:redmk2**
redmk2:x:1000:
sambashare:x:124:redmk2

```
Generally speaking, you should administer CUPS from the local host.  If you must do this remotly you can *ssh* to that host and use the lpadmin commands directly.  See```
man lpadmin
```... or config the CUPS admin web page to accept the ethernet connection.

---

### Post by LydaRA on 2012-11-16
```
getent group | grep lpadmin
lpadmin:x:108:sysop,papercut,root

getent group | grep sudo
sudo:x:27:sysop,papercut
```

So I still don't see how the CUPS process (whatever user that is) can access the UNIX users password file to verify the credentials passed in...

I find references to "cupsys" on some sites, but it appears that Ubuntu uses a "cups" name instead--although I fail to find either "cupsys" or "cups" as a user to add to the shadow group...

---

### Post by dannyboy79 on 2012-11-16
have you checked to see what user does run the cups server? I am now curious
```
ps aux | grep cups
```

i believe the problem with ubuntu's implementation of CUPS is because Ubuntu disables the root account by default. I admit after just googling and reading about CUPS I am confused about it just as much as you. Did you run 
sudo apt-get install cupsys
or
sudo apt-get install cups

---

### Post by redmk2 on 2012-11-16
> **LydaRA said:**
> ```
getent group | grep lpadmin
lpadmin:x:108:sysop,papercut,root

getent group | grep sudo
sudo:x:27:sysop,papercut
```

So I still don't see how the CUPS process (whatever user that is) can access the UNIX users password file to verify the credentials passed in...

I find references to "cupsys" on some sites, but it appears that Ubuntu uses a "cups" name instead--although I fail to find either "cupsys" or "cups" as a user to add to the shadow group...

The CUPS process is run by the system user *[SIZE="2"]lp[/SIZE]*.  This user is NOT the same as the user that administrates the system (e.g. lpadmin).  The cupsys reference is to an ubuntu package.  There is no user *cups*.

What is your login?  I assume you are a user with sudo rights.  Are you a member of the group *lpadmin*.  Are you able to administrate CUPS?

---

### Post by AlexDudko on 2012-11-16
> <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
AuthType Default
Require user @SYSTEM
Order deny,allow
</Limit>

This is default for Ubuntu (and maybe other sudo based distro's) and usually there's no need to change anything. It works good and allows logins with the admin user name and its password.
The admin user is the user which was created within the system installation procedure.
But if root user is set then to log in you must enter root as login name and root password. (This is usually default for su based distro's).

---

### Post by redmk2 on 2012-11-16
> **AlexDudko said:**
> This is default for Ubuntu (and maybe other sudo based distro's) and usually there's no need to change anything. It works good and allows logins with the admin user name and its password.
The admin user is the user which was created within the system installation procedure.
But if root user is set then to log in you must enter root as login name and root password. (This is usually default for su based distro's).
I believe you are correct.  All the files in /etc/cups/ are owned by root.  The only way that a user on a sudo based distro can can modify a file is to be a system admin (a member of the sudo group in the latest version of Ubuntu).

---

### Post by pkadeel on 2012-11-16
CUPS is run by root

To administer a single service remotely using root is not a good idea specially when you have to delegate limited access to someone else.
Additionally root login is disabled on ubuntu.

I cups the workaround is to allow a group or groups to do the administration. The default group is lpadmin i.e.
```

# Administrator user group...
SystemGroup lpadmin

```One can change it or add another group to it but the better way is to add the user to this group who will be responsible for cups administration.

I don't know about the server versions but on desktop version the default first user is also a member of lpadmin group. On server version i guess the user scheme is different and there is no user present for this purpose therefore a user needs to be created who will be a member of lpadmin group and can do the cups administration.

The cupsys user is obsolete I guess because everywhere in the documentation root is mentioned now and this is the user under which cups is running.

These are my findings so far.

Just tested the cups and remote administration by creating a new dummy user who is a member of lpadmin group only and it successfully logged in did administration tasks like adding and deleting printer, setting deafults for the printer, sharing over network etc. So now I can confirm the a user needs to be only the member of lpadmin group to handle cups administration.

---

