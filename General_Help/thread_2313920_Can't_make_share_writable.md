---
title: "Can't make share writable"
date: 2016-02-16
forum: General Help
---

### Post by Weidbrewer on 2016-02-16
I cannot for the life of me get my samba shares to be writable ever since upgrading to 14.04.  (Been having a lot of trouble with Samba in general, since the GUI manager seems to be toast...)  I've read through a bunch of threads, and nothing I've seen in them seems to work.  Am I missing something obvious?

```
[global]
workgroup = WORKGROUP
writable = Yes
server string = Samba Server %v
netbios name = ubuntu
security = share
map to guest = bad user
dns proxy = no

[videos]
path = /media/raid/videos
writable = Yes
public = yes
guest ok = yes
guest only = yes
guest account = nobody
browsable = yes
```


....I hat eto be that guy, but this was so much easier when Samba Config GUI was available...

---

### Post by gordintoronto on 2016-02-17
I would look further at the "guest" lines. I have set up writable shares entirely from Nautilus, no command line or editing files. It might be relevant that I use the same name and password on all my systems.

---

### Post by Weidbrewer on 2016-02-17
Well...then how do you set it up from Nautilus?  I don't care how I get there as long as it works. system-config-samba was the only other way I've done it, and that seems to be borked in 14.04.

---

### Post by Morbius1 on 2016-02-18
There are two kinds of access at play here: Samba access and Linux access.

Your share allows guest write access. The permissions on /media/raid/videos may not. Find out if "videos" allows write access to others and if the entire path allows access:
```
ls -al /media/raid
```

[COLOR=#0000cd]*Just a side note*[/COLOR]: Share level security no longer exists ( security = share ). system-config-samba allows you to set it that way because it's never been updated. If you run the following it will tell you that:
```
testparm -s
```
The good news is that samba will not only ignore it but replace it with the default ( security = user ) so it's taken care of.

[COLOR=#0000cd]*Another side note*[/COLOR]: You put this line in the wrong place:
> guest account = nobody
In belongs in the [global] section not a share definition section.

Here again samba comes to the rescue since "guest account = nobody" is the default and doesn't need to be added to smb.conf at all.

---

### Post by Weidbrewer on 2016-02-18
Yes, write permissions should be set correctly on the file directory as well - or at least I've chmod'd them as such in the past:

```
drwxrwxrwx  21 <my name> <my name>    8192 Feb 15 21:55 videos
```


system-config-samba keeps coming up, and I've been trying to point out that it doesn't work for me, but I haven't been phrasing it well.  I've been fighting with that as long as I've been using 14.04.  I find plenty of threads that have the same problem, but everyone says, "It's a known bug, and there's no fix."

```
$ system-config-samba
Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 45, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 82, in __init__
    self.samba_data = sambaParser.SambaParser(self)
  File "/usr/share/system-config-samba/sambaParser.py", line 185, in __init__
    self.parseFile ()
  File "/usr/share/system-config-samba/sambaParser.py", line 228, in parseFile
    section = SambaSection (token.value)
  File "/usr/share/system-config-samba/sambaParser.py", line 49, in __init__
    raise Error ("section %s already defined" % (name))
NameError: global name 'Error' is not defined

```

Also, there's a crash error for it every time the computer boots.

---

### Post by gordintoronto on 2016-02-18
I'm currently using Xubuntu and Linux Mint, neither of which use Nautilus. If memory serves, I could right-click on a folder, and there was a "share" option.

Oddly, system-config-samba lives on in Xubuntu.

> **Weidbrewer said:**
> Well...then how do you set it up from Nautilus?  I don't care how I get there as long as it works. system-config-samba was the only other way I've done it, and that seems to be borked in 14.04.

---

### Post by Morbius1 on 2016-02-19
> File "/usr/share/system-config-samba/sambaParser.py", line 49, in __init__
    raise Error ("section %s already defined" % (name))
NameError: global name 'Error' is not defined
You have the same section in smb.conf defined twice - most likely your [global] section.

Post your entire smb.conf please:
```
cat /etc/samba/smb.conf
```
> Yes, write permissions should be set correctly on the file directory as 
well - or at least I've chmod'd them as such in the past:```

drwxrwxrwx  21 <my name> <my name>    8192 Feb 15 21:55 videos 

```
Great. And what about the folder above it:
```
ls -dl /media/raid
```
And the folder above that:
```
ls -dl /media
```

---

### Post by Weidbrewer on 2016-02-19
Here's the report out:

```
$ ls -al /media/raid
total 10876
drwxrwxrwx  36 root    root       4096 Jan 24 17:44 .
drwxr-xr-x   5 root    root       4096 Jan 24 15:25 ..
-rwxr-xr-x   1 root    root       2336 Aug 14  2011 auto-image.sh
-rw-------   1 <my name> <my name>  12288 Jul 23  2011 .auto-image.sh.swp
drwxrwxrwx  21 <my name> <my name>   8192 Feb 15 21:55 videos


$ ls -al /media/
total 24
drwxr-xr-x   5 root root 4096 Jan 24 15:25 .
drwxr-xr-x  24 root root 4096 Feb 13 23:30 ..
drwxrwxrwx  36 root root 4096 Jan 24 17:44 raid
drwxr-x---+  2 root root 4096 Feb  2 22:04 <my name>

```

```
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
	server string = %h s, but the directory is empty.erver (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
interfaces = eth1

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
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
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[global]
workgroup = WORKGROUP
writable = Yes
server string = Samba Server %v
netbios name = ubuntu
security = share
map to guest = bad user
dns proxy = no

[videos]
path = /media/raid/videos
writable = Yes
public = yes
guest ok = yes
guest only = yes
guest account = nobody
browsable = yes
```

---

### Post by Morbius1 on 2016-02-20
This error in launching system-config-samba:
> File "/usr/share/system-config-samba/sambaParser.py", line 49, in __init__
raise Error ("section %s already defined" % (name))
NameError: global name 'Error' is not defined 
Is caused by this:
> [global]
workgroup = WORKGROUP
writable = Yes
server string = Samba Server %v
netbios name = ubuntu
security = share
map to guest = bad user
dns proxy = no
You already have a [global] section at the top of the file. Incorporparate the "netbios name = ubuntu" into the first [global] section at the top of the file - I like to add these things under the workgroup = WORKGROUP" line so I can easily see the modifications I have made.

Then delete the [global] section you have at the bottom of the file.

Then restart smbd:
```
sudo service smbd restart
```

---

### Post by Weidbrewer on 2016-02-20
Edited that part:

```
[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   	workgroup = WORKGROUP
	netbios name = ubuntu
# server string is the equivalent of the NT Description field
	server string = %h s, but the directory is empty.erver (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no
``` 


(the original entry lower is commented out, just so that it is there if we need to reference it.)  Still can't write to that file. Also, now I'm back to the error I remember from trying to run system-config-samba:


```
$ system-config-samba
Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 45, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 116, in __init__
    self.samba_user_data = sambaUserData.SambaUserData(self)
  File "/usr/share/system-config-samba/sambaUserData.py", line 46, in __init__
    self.readSmbPasswords()
  File "/usr/share/system-config-samba/sambaUserData.py", line 63, in readSmbPasswords
    raise RuntimeError, (_("You do not have permission to execute %s." % pdbeditcmd))
RuntimeError: You do not have permission to execute /usr/bin/pdbedit.

```


Specifically this part:

```
RuntimeError: You do not have permission to execute /usr/bin/pdbedit.
```


This is the location that was also causing the Samba GUI to crash.

Earlier, someone mentioned Nautilus, so I went back and tried that again, so that I could mark the actual error I get, and that is:

```
'net usershare' returned error 255: net usershare add: cannot share path /media/raid/ftp as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this.
```


Time was, I'd just use the Samba GUi, open it, mark the folder I wanted to share, mark it for write access, and i was off to the races.  When I upgraded to 14.04, this broke.  Figured it was a problem with the upgrade, so I did a completely fresh install, and it still crashes.  So....that's what brings us here.

---

### Post by bab1 on 2016-02-20
> **Weidbrewer said:**
> ... I'm back to the error I remember from trying to run system-config-samba:


```
$ system-config-samba
Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 45, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 116, in __init__
    self.samba_user_data = sambaUserData.SambaUserData(self)
  File "/usr/share/system-config-samba/sambaUserData.py", line 46, in __init__
    self.readSmbPasswords()
  File "/usr/share/system-config-samba/sambaUserData.py", line 63, in readSmbPasswords
    raise RuntimeError, (_("You do not have permission to execute %s." % pdbeditcmd))
RuntimeError: You do not have permission to execute /usr/bin/pdbedit.

```


Specifically this part:

```
RuntimeError: You do not have permission to execute /usr/bin/pdbedit.
```


This is the location that was also causing the Samba GUI to crash.

Earlier, someone mentioned Nautilus, so I went back and tried that again, so that I could mark the actual error I get, and that is:

```
'net usershare' returned error 255: net usershare add: cannot share path /media/raid/ftp as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this.
```


Time was, I'd just use the Samba GUi, open it, mark the folder I wanted to share, mark it for write access, and i was off to the races.  When I upgraded to 14.04, this broke.  Figured it was a problem with the upgrade, so I did a completely fresh install, and it still crashes.  So....that's what brings us here.

I'm a longtime successful user of Samba, but never a user of system-config-samba.  I don't see anything broken when you see the errors you are getting now that you have a cleaned up smb.conf file.  A non-root user never has the right to execute a binary file such as pdbedit or create a subdirectory or a share samba share in a directory that is root owned such as /media.

Typically usershares are created in the users /home/<user> directory.

What happens if you run system-config-samba as root?

---

### Post by Morbius1 on 2016-02-21
> Also, now I'm back to the error I remember from trying to run system-config-samba:
When you install system-config-samba it adds a launcher in your menu labelled "Samba". When selected it runs this command:
```
gksu system-config-samba
```
If you are going to run it from a terminal use the same command.

> 'net usershare' returned error 255: net usershare add: cannot share path /media/raid/ftp as we are restricted to only sharing directories we own.
    Ask the administrator to add the line "usershare owner only = false" 
    to the [global] section of the smb.conf to allow this.
Say what you will about the appropriateness of a samba usershare or it's implementation through nautilus-share it has the best error messages in Linux. It not only tells you there is an error but tells you exactly how to fix it. In this case however I would recommend not allowing everyone on your system the ability to share each others folders. If you want to use Nautilus to share your folders and you don't own the folder run nautilus as root:
```
gksu nautilus
```

---

### Post by Weidbrewer on 2016-02-21
Sorry,  **Morbius1**, I honestly didn’t follow any of that.


I just want to be able to use Samba again, like I could in the previous LTS.  I'm aware that the launcher uses the same command...I'm saying that it doesn't work.  It seems to be flat-out broken in 14.04.  Sharing via Nautilus doesn't work like it's supposed to, either.  This is a vanilla install of 14.04, and Samba was installed straight from the repos, so there's got to be SOMETHING that's causing it not to work.

Before I upgraded, I could write to my shares from any of my other devices, and I need to get that capability back again.  Is this just something that Ubuntu has locked down in 14.04 to protect us from ourselves, or something?  Is there nothing that can be done???

I've been at this for almost 2 months now, and I'm at wit's end.  Not to beat a dead horse, but in every previous version of Ubuntu I've used, this was a 30-second, click a few things and move on process.

---

### Post by Morbius1 on 2016-02-22
> **Weidbrewer said:**
> Sorry,  **Morbius1**, I honestly didn&#8217;t follow any of that.


I just want to be able to use Samba again, like I could in the previous LTS.  I'm aware that the launcher uses the same command...I'm saying that it doesn't work.  It seems to be flat-out broken in 14.04. 
:)
The launcher does not use the same command sequence that you are using. This is what happens when I run the command the way you did:
> morbius@vxub1404:~$ [COLOR=#0000cd]**system-config-samba**[/COLOR]
Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 45, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 116, in __init__
    self.samba_user_data = sambaUserData.SambaUserData(self)
  File "/usr/share/system-config-samba/sambaUserData.py", line 46, in __init__
    self.readSmbPasswords()
  File "/usr/share/system-config-samba/sambaUserData.py", line 63, in readSmbPasswords
    raise RuntimeError, (_("You do not have permission to execute %s." % pdbeditcmd))
RuntimeError: You do not have permission to execute /usr/bin/pdbedit.

It's the exact same error message you posted.

If I run it the way the launcher runs it it opens without errors:
```
gksu system-config-samba
```
As for the Nautilus way of sharing folders and this error message:
> 'net usershare' returned error 255: net usershare add: cannot share path /media/raid/ftp as we are restricted to only sharing directories we own.
I don't know any other way to explain that than the way I did above. Although since the target folder is labelled "ftp" it was probably best nautilus-share didn't work.

It would appear that I cannot help you.

[COLOR=#0000cd]*I would offer one piece of advice however and it may not be relevant to this exact situation but I'm not a fan of upgrading Ubuntu or any Linux from one version to the next.*[/COLOR] [And I certainly wouldn't have done what you did:]("http://ubuntuforums.org/showthread.php?t=2240033")
> Just trying to upgrade from 12.04 to 14.04.

---

### Post by Weidbrewer on 2016-02-22
To attempt to clarify a few things - the only reason that I am doing ANY of this from the command line is because the launcher does not work.  As I said earlier in the thread, I get a crash error for the Samba gui on boot, and the launcher itself just crashes.  If I could do this through that or nautilus or ANY other way, I would be...but I can't.  I'm trying to figure out *why.*

Second thing - I know that in-place upgrades can cause issues.  As I also mentioned earlier, I originally thought that that might have been the root of my problems, so I did a completely new installation (Actually, to be completely technical, it's not even the same system drive anymore, since I was doing a hardware upgrade at the time anyway.)  This is why I pointed out that this was a plain, not modified installation of basic 14.04

As for everything you were saying above about not owning the folder and not letting everyone on my system share each other's folders...I'm not sure where that's coming from.  It's just me.  This is my system, and I happen to use a few machines on it - there's no one else involved here.


So, to recap - Clean install of 14.04, no other changes.  Installed Samba and Samba GUI.  Ran Samba GUI from launcher.  Samba will not start and I get errors every which way I look at it.   While I can finally mount things (by manually editing the config file) so that I can see them on other machines, I cannot write to these shares.  These issues have only come up in 14.04.  In 12.04, everything worked fine.  

Final note:  No idea how or why that file is labeled FTP...how do I change that?

---

### Post by Morbius1 on 2016-02-22
You've posted two error messages when you ran system-config-samba and in both cases you were given remedies. If you have further issues with it you haven’t described the error message.

[COLOR=#0000cd]*From a procedural standpoint the only difference from using system-config-samba launcher in 12.04 and 14.04 is that the launcher in both cases invokes gksu. Gksu was installed by default in 12.04 and as far as I remember it ( it's been a while ) it's not in 14.04*[/COLOR]

You only posted one error message about nautilus-share ( usershares ) and you were told why that happened and given a remedy for that.
> While I can finally mount things (by manually editing the config file) so that I can see them on other machines
Great. Now you don't need system-config-samba or Nautilus to create your shares.
> ... I cannot write to these shares.
Well, it's not because of the permissions on /media (755 ), /media/raid ( 777 ), or /media/raid/videos ( 777 ). So the problem must be the subfolders underneath "videos".

For the benefit of those who wish to continue with this thread you should post the permissions of the contents of "videos"
```
ls -al /media/raid/videos
```

---

### Post by Weidbrewer on 2016-02-22
There's nothing else in that folder.  It's just an empty directory at present.

```
$ ls -al /media/raid/videos
total 8
drwxrwxrwx  2 <my name> <my name>    1 Feb 22 17:55 .
drwxrwxrwx 37 root    root    4096 Feb 22 17:55 ..
-rw-r--r--  1 nobody  nogroup    0 Feb 22 18:00 test

```

Of note, that last one is just a test text file I've been trying to create remotely that keeps erroring out and saying that I don't have permission.  The file generates, but none of the content will save.  (nano /dev/videos/test, then adding some random text and trying to save.)



As for the main part that I wasn't understanding, I did not realize that "gksu" was some separate program.  (Like, how people will use nano or gedit to create text files, when both are ultimately the same thing.)  I thought that it was a variation on "sudo" that I wasn't aware of.  I was thrown off by how you kept referring to if I wanted to "share your folders and you don't own the folder run nautilus as root."   As I *do* own these folders, I was not following why I needed to even try that.

As such, I tried, and found out that gksu was something I had to install.  I did so, and it does not recognize my password when I try to use it.  So, rather that continue to go in circles because you are thinking that I'm understanding something and me assuming that I was understanding, please just tell me what needs to be done with "gksu."  Again - this is all new to me and was never needed in 12.04.

---

