---
title: "samba warning message"
date: 2016-05-15
forum: General Help
---

### Post by mitch24 on 2016-05-15
Hey guys,

When i'm trying to create a samba file share from my ubuntu 16.04LTS machine to my windows 7 machine but when I click on samba i get the following error message "Some lines couldn't be understood while reading the configuration file /etc/samba/smb.conf. These may be unknown configuration directives for Samba plugins but could also be configuration errors.". I've tried googling the problem but nothing online seems to be clicking to me, could anyone here please shed some light on what I may of done wrong?

When I click show_details i have the following issues on the following lines
20: password level=6
49: enable spoolss= yes
53: update encrypted= yes

Cheers in advance guys!

---

### Post by Linuxisfast on 2016-05-15
What does testparm -s reveal, is smbd.service enabled as well as nmbd.service?

---

### Post by bab1 on 2016-05-15
> **mitch24 said:**
> Hey guys,

When i'm trying to create a samba file share from my ubuntu 16.04LTS machine to my windows 7 machine but when I click on samba i get the following error message "Some lines couldn't be understood while reading the configuration file /etc/samba/smb.conf. These may be unknown configuration directives for Samba plugins but could also be configuration errors.". I've tried googling the problem but nothing online seems to be clicking to me, could anyone here please shed some light on what I may of done wrong?
Are you referring to *system-config-samba*? When you say "I click on samba".  Samba server has not GUI interface.  > 

When I click show_details i have the following issues on the following lines
20: password level=6
49: enable spoolss= yes
53: update encrypted= yes

Cheers in advance guys!
The defaults for the above are listed in the man pages for *smb.conf*, which is the configuration file for Samba File Server daemon (smbd).  ```
man smb.conf
```

The only parameter listed is this```

Default: enable spoolss = yes

```...the others I have to assume have been added in error.  How did you configure the Samba server?  Please post the output of this terminal command```
cat /etc/samba/smb.conf
```
You should post the output using [noparse]```
  
```[/noparse] code blocks.  This preserves the text formatting and makes the output easier to read.  The easiest way to do the is to click on the [SIZE=5]**#**[/SIZE] icon at the top of the reply editor and pasting the text between the blocks.

---

### Post by mitch24 on 2016-05-15
testparm -s reveals

```

root@localhost:~# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "null passwords" option is deprecated
Unknown parameter encountered: "password level"
Ignoring unknown parameter "password level"
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Processing section "[share]"
Loaded services file OK.
WARNING: socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
This warning is printed because you set one of the
following options: SO_SNDBUF, SO_RCVBUF, SO_SNDLOWAT,
SO_RCVLOWAT
Modern server operating systems are tuned for
high network performance in the majority of situations;
when you set 'socket options' you are overriding those
settings.
Linux in particular has an auto-tuning mechanism for
buffer sizes (SO_SNDBUF, SO_RCVBUF) that will be
disabled if you specify a socket buffer size. This can
potentially cripple your TCP/IP stack.

Getting the 'socket options' correct can make a big
difference to your performance, but getting them wrong
can degrade it by just as much. As with any other low
level setting, if you must make changes to it, make
 small changes and test the effect before making any
large changes.

WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE

# Global parameters
[global]
    netbios name = MITCHELL
    server string = Samba file and print server
    interfaces = 127.0.0.1/8 192.168.0.0/24
    bind interfaces only = Yes
    security = USER
    client schannel = No
    server schannel = No
    allow trusted domains = No
    obey pam restrictions = Yes
    guest account = smbguest
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    passwd chat timeout = 120
    username map = /etc/samba/smbusers
    username level = 6
    unix password sync = Yes
    log file = /var/log/samba/samba.log
    max log size = 1000
    name resolve order = 192.168.0.255
    client signing = No
    server signing = No
    client use spnego = No
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = cups
    machine password timeout = 120
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
    delete user script = /usr/sbin/userdel '%u'
    add group script = /usr/sbin/groupadd '%g'
    delete group script = /usr/sbin/groupdel '%g'
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
    delete user from group script = /usr/sbin/userdel '%u' '%g'
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    logon script = %G.bat
    logon path = \\%L\profiles\%u
    logon drive = m:
    logon home = \\%L\homes\%u
    os level = 33
    preferred master = No
    local master = No
    domain master = No
    dns proxy = No
    remote announce = 192.168.0.255
    remote browse sync = 192.168.0.255
    idmap uid = 16777216-33554431
    idmap gid = 16777216-33554431
    template shell = /dev/null
    winbind separator = @
    winbind cache time = 360
    winbind use default domain = Yes
    winbind trusted domains only = Yes
    winbind nested groups = No
    winbind nss info = no
    idmap config * : range = 16777216-33554431
    idmap config * : backend = tdb
    hosts allow = 127. 192.168.0.
    cups options = raw
    follow symlinks = No


[homes]
    comment = Home Directories
    path = /home
    valid users = %U
    read only = No
    locking = No
    strict locking = No


[netlogon]
    comment = Network Logon Service
    path = /var/lib/samba/netlogon
    locking = No
    strict locking = No


[profiles]
    comment = User Profiles
    path = /var/lib/samba/profiles
    read only = No
    create mask = 0600
    directory mask = 0700
    directory mode = 0700
    locking = No
    strict locking = No


[printers]
    comment = All Printers
    path = /var/spool/samba
    printable = Yes
    browseable = No
    locking = No
    strict locking = No


[pdf-documents]
    comment = Converted PDF Documents
    path = /var/lib/samba/pdf-documents
    admin users = %U
    read only = No
    guest ok = Yes
    locking = No
    strict locking = No


[pdf-printer]
    comment = PDF Printer Service
    path = /tmp
    guest ok = Yes
    printable = Yes
    printing = bsd
    print command = /usr/bin/gadmin-samba-pdf %s %u
    lpq command = 
    use client driver = Yes


[share]
    comment = Ubuntu Media Server
    path = /media/mitchell/a1715c51-565e-4387-ac39-e63adba09bf4
    read only = No
    create mask = 0755
    guest ok = Yes



```

```


service smbd status
&#9679; smbd.service - LSB: start Samba SMB/CIFS daemon (smbd)
   Loaded: loaded (/etc/init.d/smbd; bad; vendor preset: enabled)
   Active: active (running) since Wed 2016-05-11 08:54:45 AEST; 5 days ago
     Docs: man:systemd-sysv-generator(8)
  Process: 1802 ExecStart=/etc/init.d/smbd start (code=exited, status=0/SUCCESS)
    Tasks: 3 (limit: 512)
   CGroup: /system.slice/smbd.service
           &#9500;&#9472;1827 /usr/sbin/smbd -D
           &#9500;&#9472;1833 /usr/sbin/smbd -D
           &#9492;&#9472;1949 /usr/sbin/smbd -D

May 15 19:38:01 localhost smbd[18604]:   Ignoring unknown parameter "update encrypted"
May 15 19:38:01 localhost smbd[18604]: [2016/05/15 19:38:01.696236,  0] ../lib/param/loadparm.c:732(lpcfg_map_parameter)
May 15 19:38:01 localhost smbd[18604]:   Unknown parameter encountered: "password level"
May 15 19:38:01 localhost smbd[18604]: [2016/05/15 19:38:01.696291,  0] ../lib/param/loadparm.c:1617(lpcfg_do_global_parameter)
May 15 19:38:01 localhost smbd[18604]:   Ignoring unknown parameter "password level"
May 15 19:38:01 localhost smbd[18604]: [2016/05/15 19:38:01.696533,  0] ../lib/param/loadparm.c:732(lpcfg_map_parameter)
May 15 19:38:01 localhost smbd[18604]:   Unknown parameter encountered: "update encrypted"
May 15 19:38:01 localhost smbd[18604]: [2016/05/15 19:38:01.696564,  0] ../lib/param/loadparm.c:1617(lpcfg_do_global_parameter)
May 15 19:38:01 localhost smbd[18604]:   Ignoring unknown parameter "update encrypted"
May 15 19:38:01 localhost smbd[18604]: pam_unix(samba:session): session closed for user smbguest



```

```

root@localhost:~# service nmbd status
&#9679; nmbd.service - LSB: start Samba NetBIOS nameserver (nmbd)
   Loaded: loaded (/etc/init.d/nmbd; bad; vendor preset: enabled)
   Active: active (running) since Wed 2016-05-11 08:54:45 AEST; 5 days ago
     Docs: man:systemd-sysv-generator(8)
  Process: 1344 ExecStart=/etc/init.d/nmbd start (code=exited, status=0/SUCCESS)
    Tasks: 1 (limit: 512)
   CGroup: /system.slice/nmbd.service
           &#9492;&#9472;1801 /usr/sbin/nmbd -D

May 11 08:54:24 localhost systemd[1]: Starting LSB: start Samba NetBIOS nameserver (nmbd)...
May 11 08:54:43 localhost nmbd[1344]:  * Starting NetBIOS name server nmbd
May 11 08:54:45 localhost nmbd[1788]: [2016/05/11 08:54:45.036972,  0] ../lib/param/loadparm.c:732(lpcfg_map_parameter)
May 11 08:54:45 localhost nmbd[1788]:   Unknown parameter encountered: "password level"
May 11 08:54:45 localhost nmbd[1788]: [2016/05/11 08:54:45.092548,  0] ../lib/param/loadparm.c:1617(lpcfg_do_global_parameter)
May 11 08:54:45 localhost nmbd[1788]:   Ignoring unknown parameter "password level"
May 11 08:54:45 localhost nmbd[1801]: [2016/05/11 08:54:45.094985,  0] ../lib/util/become_daemon.c:135(daemon_status)
May 11 08:54:45 localhost nmbd[1801]:   STATUS=daemon 'nmbd' : No local IPv4 non-loopback interfaces available, waiting for interface
May 11 08:54:45 localhost nmbd[1344]:    ...done.
May 11 08:54:45 localhost systemd[1]: Started LSB: start Samba NetBIOS nameserver (nmbd).



```

---

### Post by mitch24 on 2016-05-15
> Are you referring to *system-config-samba*? When you say "I click on samba".  Samba server has not GUI interface.

I mean the GUI (not too sure what it's called because i'm still quite new to Ubuntu) [IMG]http://ubuntuhandbook.org/wp-content/uploads/2014/05/samba-configuration-tool.png[/IMG]

```

root@localhost:~# cat /etc/samba/smb.conf
[global]
netbios name = mitchell
server string = Samba file and print server
workgroup = WORKGROUP
security = user
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24
bind interfaces only = yes
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 6
password level = 6
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = 192.168.0.255
wins support = no
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
passdb backend = tdbsam
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script=/usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home
valid users = %U
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
locking = no
strict locking = no

[netlogon]
comment = Network Logon Service
path = /var/lib/samba/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
strict locking = no

[profiles]
comment = User Profiles
path = /var/lib/samba/profiles
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
create mode = 0600
directory mask = 0700
locking = no
strict locking = no

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
locking = no
strict locking = no

[pdf-documents]
path = /var/lib/samba/pdf-documents
comment = Converted PDF Documents
admin users = %U
available = yes
browseable = yes
writeable = yes
guest ok = yes
locking = no
strict locking = no

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =

[share]
comment = Ubuntu Media Server    
path = /media/mitchell/a1715c51-565e-4387-ac39-e63adba09bf4
browsable = yes
guest ok = yes
read only = no
create mask = 0755

```

I edited the original through a text editer

---

### Post by mitch24 on 2016-05-15
I've been doing abit of research and I do have gadmin-samba installed but I removed it via the synaptic package manager, when I go to make sure that it's gone by using the following command 

```
apt-get purge gadmin-samba
```

I get the following error message

> root@localhost:~# apt-get purge gadmin-samba
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Have you seen this error message before? People have said to delete the folder but I don't want to do anything unless I know what the folder does or contains

---

### Post by bab1 on 2016-05-15
> **mitch24 said:**
> I've been doing abit of research and I do have gadmin-samba installed but I removed it via the synaptic package manager, when I go to make sure that it's gone by using the following command 

```
apt-get purge gadmin-samba
```

I get the following error message



Have you seen this error message before? People have said to delete the folder but I don't want to do anything unless I know what the folder does or contains
This exactly what I was looking for.  Whenever I see parameters in the smb.conf file that don't even exist such as```
WARNING: The "null passwords" option is deprecated
Unknown parameter encountered: "password level"
Ignoring unknown parameter "password level"
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
```
... and junk like this```
ARNING: socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
This warning is printed because you set one of the
following options: SO_SNDBUF, SO_RCVBUF, SO_SNDLOWAT,
SO_RCVLOWAT
Modern server operating systems are tuned for
high network performance in the majority of situations;
when you set 'socket options' you are overriding those
settings.
Linux in particular has an auto-tuning mechanism for
buffer sizes (SO_SNDBUF, SO_RCVBUF) that will be
disabled if you specify a socket buffer size. This can
potentially cripple your TCP/IP stack.

Getting the 'socket options' correct can make a big
difference to your performance, but getting them wrong
can degrade it by just as much. As with any other low
level setting, if you must make changes to it, make
 small changes and test the effect before making any
large changes.
```...I know that another user has been sucked into using gadmin-samba.

The cure: Purge all the samba packages and start over.  This next time just install **samba** and **samba-common** and **cifs-utils**.  Nothing else is needed.  Do not modify the smb.conf file at all.  Just add the shares you want at the very bottom of the file.  If you don't understand or want help ask before you do anything.

---

### Post by mitch24 on 2016-05-15
Cheers for your help. I just used the following command to remove samba 

> sudo apt-get remove --purge samba

But when I go into /etc/samba directory it's still there....[COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR]

---

### Post by bab1 on 2016-05-16
> **mitch24 said:**
> Cheers for your help. I just used the following command to remove samba 



But when I go into /etc/samba directory it's still there....[COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR]
It meaning the smb.conf file?  If you want just rename it with this command```
sudo mv [s] /etc/samba/smbconf[/s]  /etc/samba/smb.conf /etc/samba/smb.gadmin
```

Then install the samba packages with this command```
sudo apt-get install samba samba-common cifs-utils
```

---

### Post by mitch24 on 2016-05-16
So I did what you said and now I get the error message 

> E: Sub-process /usr/bin/dpkg returned an error code(1)

---

### Post by bab1 on 2016-05-16
Yes that's a typo.  I'll fix it in the original post.

---

### Post by mitch24 on 2016-05-16
I get that error message when I go to install samba samba-common cifs-utils

---

### Post by bab1 on 2016-05-16
> **mitch24 said:**
> I get that error message when I go to install samba samba-common cifs-utils
What error message?

---

### Post by mitch24 on 2016-05-16
[COLOR=#000000][I]>  E: Sub-process /usr/bin/dpkg returned an error code(1) 

this is the error message[/I][/COLOR]

---

### Post by mitch24 on 2016-05-16
Also, what is supposed to happen when I reinstall samba? is there meant to be a new smb.conf file in the /etc/samba directory?

---

### Post by bab1 on 2016-05-16
> **mitch24 said:**
> [COLOR=#000000][I]

this is the error message[/I][/COLOR]
Searching with Google on that error message reveals a lot.  See [**here**]("https://www.google.com/search?client=ubuntu&channel=fs&q=E%3A+Sub-process+%2Fusr%2Fbin%2Fdpkg+returned+an+error+code%281%29&ie=utf-8&oe=utf-8").

I have been using Ubuntu since 2006 and have never had this kind of problem.  My guess is you have lots of failed attempts with application installs.  It appears something is corrupted with some of the basic install or in the repository lists.  What it could be I wouldn't have a clue.

In these kinds of situations, I become real practical.  I'm not really interested in the why of the situation.  I'm more interested in the bottom line.  That is, a functioning OS and applications.  I'd just reinstall the entire thing.  This means Ubuntu and all the applications.  Then you can re-populate the data from the backups.  It's one of the reasons to keep backups of all the data and a separate partition for the /home directory and, if you can, also the data partition (i.e. /srv/).    

For me the compete install and configuration is the only way to go.  It's only about an hour's worth of work.

[COLOR="#0000CD"]Edit:  I'm going to amend my thoughts with this attempt to clean everything out without re-installing the OS.  Try these commands and see if this works [/COLOR]```

sudo apt-get clean
sudo apt-get autoremove
sudo apt-get -f
sudo apt-get install samba
```
[COLOR="#0000CD"]If this works we can continue tomorrow.[/COLOR]

---

### Post by bab1 on 2016-05-16
> **mitch24 said:**
> Also, what is supposed to happen when I reinstall samba? is there meant to be a new smb.conf file in the /etc/samba directory?
If you can re-install samba you will have an unmolested binary of the server and lib's as well as a new copy of the smb.conf file.

---

