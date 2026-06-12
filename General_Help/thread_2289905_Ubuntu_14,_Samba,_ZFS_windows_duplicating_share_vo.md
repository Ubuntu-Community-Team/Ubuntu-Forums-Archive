---
title: "Ubuntu 14, Samba, ZFS windows duplicating share volumes"
date: 2015-08-07
forum: General Help
---

### Post by Nolege on 2015-08-07
Hello, 

I have Linux media 3.16.0-45-generic #60~14.04.1-Ubuntu x86_64 GNU/Linux. I can connect to this public / no password share on my network (desired). However when I connect using using my windows machine I see the shares. They are duplicated to some extent and the ones prefixed with PLEX_ require authentication. I do not understand why this is happening on ubuntu. I did not see on solaris, freebsd, or RHEL.

My samba configuration is as follows:
```

[global]
workgroup = *************
server string = *************
log file = /var/log/samba.log
max log size = 1000
syslog = 10
panic action = /usr/share/samba/panic-action %d
server role = standalone server
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
usershare allow guests = yes
security = user
map to guest = bad user
guest account = **********
usershare allow guests = yes




# Below are the ZFS filesystem shares
[Camera]
path = /PLEX/Camera
comment = Camera
browseable = yes
read only = no
create mode = 0754
public = yes
writeable = yes
guest only = Yes
guest ok = Yes


[Movies]
path = /PLEX/Movies
comment = Movies
browseable = yes
read only = no
create mode = 0754
public = yes
writeable = yes
guest only = Yes
guest ok = Yes


[Music]
path = /PLEX/Music
comment = Music
browseable = yes
read only = no
create mode = 0754
public = yes
writeable = yes
guest only = Yes
guest ok = Yes


[Photos]
path = /PLEX/Photos
comment = Photos
browseable = yes
read only = no
create mode = 0754
public = yes
writeable = yes
guest only = Yes
guest ok = Yes


[TV Shows]
path = /PLEX/TV\ Shows
comment = TV Shows
browseable = yes
read only = no
create mode = 0754
public = yes
writeable = yes
guest only = Yes
guest ok = Yes

```

=== ZFS Configuration (All datasets configured the same) ===
```

$ zfs list
NAME USED AVAIL REFER MOUNTPOINT
PLEX 2.10T 9.91T 175K /PLEX
PLEX/Camera 387M 9.91T 387M /PLEX/Camera
PLEX/Movies 2.00T 9.91T 2.00T /PLEX/Movies
PLEX/Music 16.1G 9.91T 16.1G /PLEX/Music
PLEX/Photos 162K 9.91T 162K /PLEX/Photos
 
PLEX/TV Shows 90.4G 9.91T 90.4G /PLEX/TV Shows


$ zfs get all PLEX/Movies
NAME PROPERTY VALUE SOURCE
PLEX/Movies type filesystem -
PLEX/Movies creation Tue Aug 4 20:01 2015 -
PLEX/Movies used 2.00T -
PLEX/Movies available 9.91T -
PLEX/Movies referenced 2.00T -
PLEX/Movies compressratio 1.00x -
PLEX/Movies mounted yes -
PLEX/Movies quota none default
PLEX/Movies reservation none default
PLEX/Movies recordsize 128K default
PLEX/Movies mountpoint /PLEX/Movies default
PLEX/Movies sharenfs off default
PLEX/Movies checksum on default
PLEX/Movies compression lz4 local
PLEX/Movies atime on default
PLEX/Movies devices on default
PLEX/Movies exec on default
PLEX/Movies setuid on default
PLEX/Movies readonly off default
PLEX/Movies zoned off default
PLEX/Movies snapdir hidden default
PLEX/Movies aclinherit restricted default
PLEX/Movies canmount on default
PLEX/Movies xattr on default
PLEX/Movies copies 1 default
PLEX/Movies version 5 -
PLEX/Movies utf8only off -
PLEX/Movies normalization none -
PLEX/Movies casesensitivity sensitive -
PLEX/Movies vscan off default
PLEX/Movies nbmand off default
PLEX/Movies sharesmb on local
PLEX/Movies refquota none default
PLEX/Movies refreservation none default
PLEX/Movies primarycache all default
PLEX/Movies secondarycache all default
PLEX/Movies usedbysnapshots 0 -
PLEX/Movies usedbydataset 2.00T -
PLEX/Movies usedbychildren 0 -
PLEX/Movies usedbyrefreservation 0 -
PLEX/Movies logbias latency default
PLEX/Movies dedup off default
PLEX/Movies mlslabel none default
PLEX/Movies sync standard default
PLEX/Movies refcompressratio 1.00x -
PLEX/Movies written 2.00T -
PLEX/Movies logicalused 2.00T -
PLEX/Movies logicalreferenced 2.00T -
PLEX/Movies snapdev hidden default
PLEX/Movies acltype off default
PLEX/Movies context none default
PLEX/Movies fscontext none default
PLEX/Movies defcontext none default
PLEX/Movies rootcontext none default
PLEX/Movies relatime off default
PLEX/Movies redundant_metadata all default
 
PLEX/Movies overlay off default

```

== FS ==
```

ls -la /PLEX
total 142
drwxr-xr-x 7 ********* root 7 Aug 5 17:44 **.**
drwxr-xr-x 23 root root 4096 Aug 4 19:46 **..**
drwxr-xr-x 3 ********* root 16 Jun 15 2014 **Camera**
drwxr-xr-x 2 ********* root 175 Aug 3 18:26 **Movies**
drwxr-xr-x 14 ********* root 14 Jul 24 2014 **Music**
drwxr-xr-x 2 ********* root 2 Aug 4 20:31 **Photos**
 
drwxr-xr-x 8 ********* root 8 Aug 5 20:56 [B]TV Shows
[/B]
```The user matches the guest user. The only issue is the shares show up on windows as:

PLEX_Movies (Auth required)
Movies (No Auth required)

PLEX_Music (Auth required)
Music (No Auth required)

PLEX_Camera (Auth required)
Camera (No Auth required)
... etc.

```

$ smbtree 

\\MEDIA ***********
\\MEDIA\PLEX_Photos Comment: /PLEX/Photos << I do not know where these are configured
\\MEDIA\PLEX_Camera Comment: /PLEX/Camera << I do not know where these are configured
\\MEDIA\PLEX_Movies Comment: /PLEX/Movies << I do not know where these are configured
\\MEDIA\PLEX_Music Comment: /PLEX/Music << I do not know where these are configured
\\MEDIA\Camera Camera
\\MEDIA\Movies Movies
\\MEDIA\Music Music
\\MEDIA\Photos Photos
\\MEDIA\TV Shows TV Shows
\\MEDIA\IPC$ IPC Service (***********)
 
\\MEDIA\PLEX_TV_Shows Comment: /PLEX/TV Shows

```

I do get this which might be a problem, but I am unsure with ubuntu

```

$ smbstatus 


Samba version 4.1.6-Ubuntu
PID Username Group Machine 
-------------------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED


Service pid machine Connected at
-------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED
Failed to traverse sessions: NT_STATUS_ACCESS_DENIED

No locked files

```
 
I am stumped as to why these ghost shares are showing up. Any help you can offer would be appreciated. Forgive any poor grammar or misspelling, hit the sauce out of frustration.

---

### Post by bab1 on 2015-08-08
> **Nolege said:**
> Hello, 

I have Linux media 3.16.0-45-generic #60~14.04.1-Ubuntu x86_64 GNU/Linux. I can connect to this public / no password share on my network (desired). However when I connect using using my windows machine I see the shares. They are duplicated to some extent and the ones prefixed with PLEX_ require authentication. I do not understand why this is happening on ubuntu. I did not see on solaris, freebsd, or RHEL.

My samba configuration is as follows:

```
[global]
workgroup = *************
server string = *************
log file = /var/log/samba.log
max log size = 1000
syslog = 10
panic action = /usr/share/samba/panic-action %d
server role = standalone server
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
usershare allow guests = yes
security = user
map to guest = bad user
guest account = **********
usershare allow guests = yes

```
# Below are the ZFS filesystem shares
```

[Camera]
path = /PLEX/Camera
comment = Camera
browseable = yes
read only = no
create mode = 0754
public = yes
writeable = yes
guest only = Yes
guest ok = Yes

[Movies]
path = /PLEX/Movies
comment = Movies
browseable = yes
read only = no
create mode = 0754
public = yes
writeable = yes
guest only = Yes
guest ok = Yes

[Music]
path = /PLEX/Music
comment = Music
browseable = yes
read only = no
create mode = 0754
public = yes
writeable = yes
guest only = Yes
guest ok = Yes

[Photos]
path = /PLEX/Photos
comment = Photos
browseable = yes
read only = no
create mode = 0754
public = yes
writeable = yes
guest only = Yes
guest ok = Yes

[TV Shows]
path = /PLEX/TV\ Shows
comment = TV Shows
browseable = yes
read only = no
create mode = 0754
public = yes
writeable = yes
guest only = Yes
guest ok = Yes

```
I assume these are just Samba shares as defined in the /etc/samba/smb.conf file above; right ???> 

== FS ==
```
ls -la /PLEX
total 142
drwxr-xr-x 7 ********* root 7 Aug 5 17:44 **.**
drwxr-xr-x 23 root root 4096 Aug 4 19:46 **..**
drwxr-xr-x 3 ********* root 16 Jun 15 2014 **Camera**
drwxr-xr-x 2 ********* root 175 Aug 3 18:26 **Movies**
drwxr-xr-x 14 ********* root 14 Jul 24 2014 **Music**
drwxr-xr-x 2 ********* root 2 Aug 4 20:31 **Photos**
 
drwxr-xr-x 8 ********* root 8 Aug 5 20:56 **TV Shows**

```
The user matches the guest user. The only issue is the shares show up on windows as:

PLEX_Movies (Auth required)
Movies (No Auth required)

PLEX_Music (Auth required)
Music (No Auth required)

PLEX_Camera (Auth required)
Camera (No Auth required)
... etc.

```
$ smbtree 

\\MEDIA ***********
        \\MEDIA\PLEX_Photos     Comment: /PLEX/Photos << I do not know where these are configured
        \\MEDIA\PLEX_Camera     Comment: /PLEX/Camera << I do not know where these are configured
        \\MEDIA\PLEX_Movies     Comment: /PLEX/Movies << I do not know where these are configured
        \\MEDIA\PLEX_Music     Comment: /PLEX/Music << I do not know where these are configured
        \\MEDIA\Camera     Camera
        \\MEDIA\Movies     Movies
        \\MEDIA\Music     Music
        \\MEDIA\Photos     Photos
        \\MEDIA\TV Shows     TV Shows
        \\MEDIA\IPC$     IPC Service (***********)
 
        \\MEDIA\PLEX_TV_Shows     Comment: /PLEX/TV Shows

```

I do get this which might be a problem, but I am unsure with ubuntu

```

$ smbstatus 


Samba version 4.1.6-Ubuntu
PID Username Group Machine 
-------------------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED


Service pid machine Connected at
-------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED
Failed to traverse sessions: NT_STATUS_ACCESS_DENIED


No locked files
```
The above needs to be run by root to work properly.  For Ubuntu this means using sudo ```
$ sudo smbstatus
```> 
 
I am stumped as to why these ghost shares are showing up. Any help you can offer would be appreciated..
When posting text output from the terminal you should use the [noparse]```
 
```[/noparse] code blocks to wrap the text in.  The easiset way to do that ( as I have done) is to click on the [SIZE=6]**# **[/SIZE] icon at the top of the advanced editor that you use to reply with and paste the text between the code blocks. 

_Your problem is usually the result of configuring the shares twice. _ Once in the ***smb.conf*** file and then again via the GUI interface.  We can check that by seeing what is in the usershares directory.  Please post the output of this command```
ls -l /var/lib/samba/usershares
```...there should be NO shares defined here if you have defined the shares in the *smb.conf* file.

---

### Post by Nolege on 2015-08-12
Okay, that fixed my issue. I am running Ubuntu Server so there is no GUI. However, these user shares did exist. I was not aware these existed on 14. Thank you for your help.

---

### Post by bab1 on 2015-08-13
> **Nolege said:**
> Okay, that fixed my issue. I am running Ubuntu Server so there is no GUI. However, these user shares did exist. I was not aware these existed on 14. Thank you for your help.
Even though they existed on the server, most likely they were made from a Samba client with a GUI ( a desktop).

---

