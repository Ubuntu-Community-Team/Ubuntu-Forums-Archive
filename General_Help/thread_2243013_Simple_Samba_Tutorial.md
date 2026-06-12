---
title: "Simple Samba Tutorial?"
date: 2014-09-05
forum: General Help
---

### Post by 2CV67 on 2014-09-05
Having upgraded a Desktop PC & a Netbook to 14.04.1, I am now unable to get either File-sharing or Printing to work between them.

A few years back, I followed this old thread with some success:
[http://ubuntuforums.org/showthread.php?t=1685718](http://ubuntuforums.org/showthread.php?t=1685718)

but when I try to step through it now, things don't fit or don't work.

Is there a Dummy-level guide somewhere for getting file-sharing & printing working in 14.04?
Of course I have found any number of highly complicated (and often outdated) articles on Samba but nothing at my low level...

Thanks for any help!

---

### Post by TheFu on 2014-09-05
My samba config file from 1996 has been working with only very slight modifications all these years. 2 or 3 minor changes.
Most people probably wouldn't run into those settings - added wide-links around 5-10 yrs ago. The years blend as we get older. ;(

These days, you can use Nautilus to share folders for simple needs. Howtogeek has a guide with all the point-n-click crap.

Otherwise, please post the smb.conf with all comments removed - there's a **testparm** option for that.  **smbtree** output might be helpful too.

---

### Post by 2CV67 on 2014-09-05
Thanks for your interest!

But I really need DUMMY-level suggestions.

I will look at Nautilus sharing, but will probably need Samba anyway for family Windows machines.

I am trying to work my way through this:
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html)
But have only got to Test n°1...

Here is the output of "testparm smb.conf":
(I didn't find out about "smbtree" yet...)
```

chris@Acer-TC:~$ cd /etc/samba
chris@Acer-TC:/etc/samba$ ls
gdbcommands  smb.conf  smbusers  tls
chris@Acer-TC:/etc/samba$ testparm smb.conf
Load smb config files from smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Desktop]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	server role = standalone server
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	read only = No
	guest ok = Yes

[Desktop]
	path = /home/chris/Desktop
	read only = No
	guest ok = Yes
chris@Acer-TC:/etc/samba$ 
```

---

### Post by TheFu on 2014-09-05
Nautilus provides an interface to setup samba CIFS shares. Did you look for the article mentioned?

---

### Post by bab1 on 2014-09-06
> **2CV67 said:**
> 
Having upgraded a Desktop PC & a Netbook to 14.04.1, I am now unable to get either File-sharing or Printing to work between them.

What isn't working correctly?  What specific errors do you see
> 

But I really need DUMMY-level suggestions.

It doesn't get much more simple than installing the *samba package* (i.e. sudo apt-get install samba).  This installs the Samba server.  Then all you need to do is add a share at the bottom of the smb.conf file.  If you can't see the server or you can see the server but not the share, then you have some basic networking misconfigured.  Usually this is a hosts/DNS or TCP/IP problem.  The samba package install is very consistent from Ubuntu  12.04LTS to Ubuntu 14.04 LTS.  Even considering the fact that 12.04 uses Samba v3 (3.6 currently) and 14.04 uses Samba v4 (4.1 currently.  Samba v4 is a complete rewrite of the smbd and nmbd daemons.  These provide ALL the file sharing and browsing functions.  Note: it is possible to have sharing without the browsing.  Have you tried to connect directly with the share (e.g. smb://SERVER_IP_ADDRESS/share-name)?
> 
I will look at Nautilus sharing, but will probably need Samba anyway for family Windows machines.

These are really Samba "usershares".  They were designed to allow a non-root user to share directories inside that users home directory.  The caveat is:  You can only share to yourself or to EVERYONE.  No fine grained security at all.
> 

I am trying to work my way through this:
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html)
But have only got to Test n°1...

Mostly this just testing to see if you have TCP/IP network connectivity and some sort of name services.  Kind of what I said above.

My suggestion is to make sure the smb.conf file has only the default settings including not adding any shares at the bottom.  Reboot the Samba daemon like this```
sudo service smbd restat
```...then see if you can browse the Samba server by name.  If not we can start the "above DUMMY-level" testing.

---

### Post by 2CV67 on 2014-09-06
Well - this morning, after a good nights sleep (but really after reboots all round, I suppose) everything is working!
But I don't know why, or which actions fixed anything...

Now, I can see Netbook from Desktop & vice-versa in Nautilus.
I can even see them twice - once directly and once inside 'Windows shares > WORKGROUP'. (Why is that?)
I can see shares I created in Samba "Desktop" & default shares I never touched "Public".
Yesterday I could see Desktop shares from Netbook, but not Netbook shares from Desktop.
And I don't know what of all the attempts actually changed that, because it didn't show immediately.

Yesterday, Netbook saw the USB Printer on desktop, created in Samba (Canon-PIXMA-iP4300) OK, but attempted printing resulted in "Held for authentication".
Running the Printer Troubleshooter resulted in a new Printer (Canon-iP4300) being added.
After which, Printing via Canon-iP4300 worked.
Then, Printing via Canon-PIXMA-iP4300 started to work too...
I wonder why?

This morning, Canon-PIXMA-iP4300 is no longer visible on Desktop, but I can still print through it from Netbook!

My previous experiences with Samba have been very similar (inducing hair-tearing rage!) and no doubt future experiences will be the same.

The problem is that I cannot find a SIMPLE, STEP-BY-STEP PROCEDURE FOR SETTING UP SAMBA FOR SIMPLE TASKS, written so a 6-year-old could follow it.

Comments like:
"there's a testparm option for that. smbtree output might be helpful too"
"Usually this is a hosts/DNS or TCP/IP problem."
"Have you tried to connect directly with the share (e.g. smb://SERVER_IP_ADDRESS/share-name)?"
"My suggestion is to make sure the smb.conf file has only the default settings including not adding any shares at the bottom."
"sudo service smbd restat" (typo?)
...just add to my distress.

If I wanted to rub everything out & start again (and I do), then:
What should I do first?
What should I do next?
Etc, etc.
What things do I have to do to get changes into effect (smbd restart? nmbd restart? logout? Reboot? Sleep on it?.....).

I need "Samba for Dummies".
I am probably not alone.

But thanks again for your help!

---

### Post by 2CV67 on 2014-09-06
> **TheFu said:**
> Nautilus provides an interface to setup samba CIFS shares. Did you look for the article mentioned?

I suppose you mean this one?
[http://www.howtogeek.com/116309/use-ubuntus-public-folder-to-easily-share-files-between-computers/](http://www.howtogeek.com/116309/use-ubuntus-public-folder-to-easily-share-files-between-computers/)

Yes - in fact I already had it in my bookmarks under Samba, from a previous life.

He certainly makes it look very simple (good!) but left me with unanswered questions (less good).
The following apply to the article before the PFS section:
1. Without PFS can I still do file sharing with Linux & with Windows PCs? (I suppose so).
2. Do I need to do the same setup procedure on each Linux PC on the network? (I suppose so).
3. He recommends allowing Guest access, whereas others say it is risky. (I think I can take the risk with whatever I will have in shared folders).
4. He doesn't really cover Permissions, which has caused me problems in the past...
5. What about Groups & passwords?
6. Does all that work without ever touching a Samba share?
7. If this is so simple, why do most people bother with creating samba shares?

Should I completely uninstall Samba, then start again, following this article?
I would quite like to have a simple method, which I can probably remember & repeat when necessary.

Then there's printing, but that's another story...

---

### Post by 2CV67 on 2014-09-06
Oh dear...

I stupidly decided to try wiping everything clean & making a fresh start, following the HTG article.
And now I am in a real mess.

I deleted all printers from Desktop (DT) & Netbook (NB).
In synapt, I Completely Removed Samba in DT & NB.
In DT, I deleted a group called sharer which I had created myself.
I noticed sambashare groups were still present.

I rebooted DT OK.
Rebooting NB, at Login after p/w I got "Failed to add entry for user Chris".
Login completes after a second "Enter".
This problem persists after every p/w entry, I think...

On DT & NB, I removed everybody from sambashare group (to get back to original configuration?).

Then I started to follow the guide.
I went to my Public folder > Properties & checked "Share this folder".
I accepted the invite to Install the Service, but that brought up a warning "System Program Problem".
At that point there was a window open but greyed out asking if I wanted to install "libpam smbpass" (or similar), but the choices were not available, so I closed that window.
Now, when I look at Public > Properties & select "Share this folder" & "Create Share" I get this error message:
```

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.
```

I did try to restart smbd, but no success:

```
chris@Acer-TC:~$ sudo restart smbd
[sudo] password for chris: 
restart: Unknown instance: 
chris@Acer-TC:~$ 
```

I started this thread just to see if there was a simple guide somewhere.
Now, I actually need some expert assistance, I think.

I would be very grateful for any suggestions! :oops:

---

### Post by bab1 on 2014-09-06
> **2CV67 said:**
> Well - this morning, after a good nights sleep (but really after reboots all round, I suppose) everything is working!
But I don't know why, or which actions fixed anything...

Sleep always make things appear better.  ;-)  Rebooting makes Samba re-read the configuration file (smb.conf)
> 

Now, I can see Netbook from Desktop & vice-versa in Nautilus.
I can even see them twice - once directly and once inside 'Windows shares > WORKGROUP'. (Why is that?)

Your not seeing them twice.  You are seeing the same thing via different clickable icons.  > 
I can see shares I created in Samba "Desktop" & default shares I never touched "Public".
Yesterday I could see Desktop shares from Netbook, but not Netbook shares from Desktop.
And I don't know what of all the attempts actually changed that, because it didn't show immediately.

Ahhhhhh, but it did show eventually.  Patience helps.  It can take up to 15 minutes for new configurations to appear when browsing for shares.
> 

Yesterday, Netbook saw the USB Printer on desktop, created in Samba (Canon-PIXMA-iP4300) OK, but attempted printing resulted in "Held for authentication".
Running the Printer Troubleshooter resulted in a new Printer (Canon-iP4300) being added.
After which, Printing via Canon-iP4300 worked.
Then, Printing via Canon-PIXMA-iP4300 started to work too...
I wonder why?

It was configured for you.......
> 

This morning, Canon-PIXMA-iP4300 is no longer visible on Desktop, but I can still print through it from Netbook!

My previous experiences with Samba have been very similar (inducing hair-tearing rage!) and no doubt future experiences will be the same.

The problem is that I cannot find a SIMPLE, STEP-BY-STEP PROCEDURE FOR SETTING UP SAMBA FOR SIMPLE TASKS, written so a 6-year-old could follow it.

Samba is not a trivial application.  It has hundreds of options (parameters) allowing it to be configured for almost any type of situation.  The default samba package has been configured to provide the default settings that are the most sane for the majority of folks using it.  There is no more simple procedure than installing the samba package and adding a share at the bottom of the smb.conf file.
> 

Comments like:
"there's a testparm option for that. smbtree output might be helpful too"
"Usually this is a hosts/DNS or TCP/IP problem."
"Have you tried to connect directly with the share (e.g. smb://SERVER_IP_ADDRESS/share-name)?"
"My suggestion is to make sure the smb.conf file has only the default settings including not adding any shares at the bottom."
"sudo service smbd restat" (typo?)
...just add to my distress.

I would take the time to learn how the system works instead of just being petulant about it all.  You don't have to know everything about the car you drive, but it helps to know when and where to add oil to the engine or how to fill the radiator with coolant if needed.
> 

If I wanted to rub everything out & start again (and I do), then:
What should I do first?
What should I do next?
Etc, etc.
What things do I have to do to get changes into effect (smbd restart? nmbd restart? logout? Reboot? Sleep on it?.....).

What do you mean by "rub out"?  You can return to the default Samba file sharing by copying back or recreating the original default smb.conf.  Samba file sharing has only has one configuration file (e.g. smb.conf).  There is no reason to reinstall the samba package just to get a default copy of that configuration file.  See the instructions in my previous post that starts with "My suggestion is..."
> 

I need "Samba for Dummies".
I am probably not alone.

But thanks again for your help!
It doesn't get much dumber than the instructions I provided.  You need to learn the basics at some point.  If for no other reason than to stop irritating yourself.  Do you at least know how to use the terminal command line and edit text files as the root user?  There are plenty of "Linux for Dummies"  and "Samba for Dummies" books available for you to read.  It's difficult to give instructions on this forum when you have to start with "Plug the computer in to the electrical outlet".

---

### Post by TheFu on 2014-09-06
> I started this thread just to see if there was a simple guide somewhere.
Simple is completely subjective.
Groups add complexity.
Passwords add complexity.
Using a non-internal drive adds complexity, especially if not running a Linux file system.
Printing adds complexity.  
Thousands of other, tiny differences from a default installation add complexity. 
**When is "simple" not simple anymore?**  I dunno.

Recently found a nice, simple, primer for Linux - [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) (free pdf book) - skimming the first 100 pgs will payback 1000x and make stuff like setting up tools like samba much easier. Seems like restarting the daemon was all that was necessary after making a change. Easy to forget for anyone.

Anyway - happy it is working for you.

---

### Post by bab1 on 2014-09-06
> **2CV67 said:**
> Oh dear...

I stupidly decided to try wiping everything clean & making a fresh start, following the HTG article.
And now I am in a real mess.

Self inflicted wounds are the worst kind.
> 
I deleted all printers from Desktop (DT) & Netbook (NB).
In synapt, I Completely Removed Samba in DT & NB.

In Synaptic "Completely Remove" does not remove everything.  You must use PURGE to remove everything.  Even then you might have to use the command line to get all the dependencies removed (i.e. libpam smbpass).   
> 

In DT, I deleted a group called sharer which I had created myself.
I noticed sambashare groups were still present.

I rebooted DT OK.
Rebooting NB, at Login after p/w I got "Failed to add entry for user Chris".
Login completes after a second "Enter".
This problem persists after every p/w entry, I think...

Not sure what that means.  "I think..." is not acceptable.  It either is or is not.  In diagnosing a problem it is good to know which it really is.
> 
On DT & NB, I removed everybody from sambashare group (to get back to original configuration?).

Then I started to follow the guide.
I went to my Public folder > Properties & checked "Share this folder".
I accepted the invite to Install the Service, but that brought up a warning "System Program Problem".
At that point there was a window open but greyed out asking if I wanted to install "libpam smbpass" (or similar), but the choices were not available, so I closed that window.
Now, when I look at Public > Properties & select "Share this folder" & "Create Share" I get this error message:
```

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.
```

As you have removed Samba you can't expect Samba to work.  Since smbd is the Samba server daemon (process) restarting it is not possible at this point.
> 
I did try to restart smbd, but no success:

```
chris@Acer-TC:~$ sudo restart smbd
[sudo] password for chris: 
restart: Unknown instance: 
chris@Acer-TC:~$ 
```

You need to be exact.  The incantation to restart smbd (if it was installed) is: ***sudo service smbd restart***
> 

I started this thread just to see if there was a simple guide somewhere.
Now, I actually need some expert assistance, I think.

I would be very grateful for any suggestions! :oops:
I would use these 3 commands one at a time from the terminal command line```

sudo apt-get purge samba cifs utils

sudo apt-get autoremove

sudo apt-get autoclean

```
That should clean up Ubuntu so you can add back the correct packages.

There was no reason to remove user groups or delete users from groups.  But since that has been done I would leave it alone for right now.

Now you should be able to add back the complete samba packages.  Again from the command line you can do this to test the  install Samba ```
sudo apt-get -s install samba cifs-utils 
```...If there are no errors you can just remove the "-s" to install Samba. Then I would reboot the machine and wait some time before seeing if each machine appears.

Be patient and deliberate.  It's really not as bad as it seems.

---

### Post by bab1 on 2014-09-06
> **TheFu said:**
> 
Anyway - happy it is working for you.
Talk about salt in the wounds!

The OP has manage to bork the whole thing and now has no Samba sharing at all.   ](*,)

---

### Post by 2CV67 on 2014-09-06
Thank you for your patience!!

I started following your suggestions, but have run into a question already:
```
chris@Acer-TC:~$ sudo apt-get purge samba cifs utils
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cifs
E: Unable to locate package utils
chris@Acer-TC:~$ 

```
Is that OK, or should it be 
```
sudo apt-get purge samba cifs-utils
```

---

### Post by bab1 on 2014-09-06
> **2CV67 said:**
> Thank you for your patience!!

I started following your suggestions, but have run into a question already:
```
chris@Acer-TC:~$ sudo apt-get purge samba cifs utils
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cifs
E: Unable to locate package utils
chris@Acer-TC:~$ 

```
Is that OK, or should it be 
```
sudo apt-get purge samba cifs-utils
```

Yes I left the "-" out.  Sorry about that.

[COLOR="#0000FF"]Edit:  The take away form that is that all objects need to have contiguous characters.  The space is how the script (apt-get) knows what the objects are and how many to look for.  This is a bash convention.  Bash is the command line shell. [/COLOR]

---

### Post by 2CV67 on 2014-09-06
OK - I ran the purge > autoremove > autoclean > -s install > install sequence & can now see Samba in Synapt as "installed".

But it does not appear in the Dash when called, and attempting to "Create Share" brings up the same error message:
```
'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.
```

---

### Post by bab1 on 2014-09-06
> **2CV67 said:**
> OK - I ran the purge > autoremove > autoclean > -s install > install sequence & can now see Samba in Synapt as "installed".

I assume what you mean here is that ultimately you have done this```
sudo apt-get install samba cifs-utils
``` 
> 
But it does not appear in the Dash when called, 

It does not appear in Dash.  It is a server and provides services.  There should be no direct user interaction with the server itself (smbd). > and attempting to "Create Share" brings up the same error message:
```
'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.
``` Post he output of this```
ps -ef | grep mbd
```...this should show 2 smbd processes and 1 nmbd process.

I want to see the smb.conf file.  Post the output of this (in its entirety)```
cat /etc/samba/smb.conf
```[COLOR="#0000FF"]

Edit: What directory are you trying to share? [/COLOR]

---

### Post by 2CV67 on 2014-09-06
Previously, Samba appeared in Dash & opened a GUI.

Since my last post, I installed system-config-samba and now "it" appears in Dash, but clicking produces a p/w prompt, then nothing.

Anyway, here are the outputs you asked for:

```
chris@Acer-TC:~$ ps -ef | grep mbd
root      1855     1  0 21:04 ?        00:00:00 nmbd -D
chris     3548  3478  0 21:19 pts/1    00:00:00 grep --color=auto mbd
chris@Acer-TC:~$ cat /etc/samba/smb.conf
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



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
;	passdb backend = tdbsam

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
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	username map = /etc/samba/smbusers
	security = user
;	encrypt passwords = yes
;	guest ok = no
;	guest account = nobody

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
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
	writeable = yes
	guest ok = yes
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[Desktop]
	path = /home/chris/Desktop
	writeable = yes
;	browseable = yes
	guest ok = yes
chris@Acer-TC:~$ 
```

And again - many thanks for your patience!

Your edit:

I usually share "Public" file & "Desktop" for all users on all machines in my local network.

---

### Post by bab1 on 2014-09-06
> **2CV67 said:**
> Previously, Samba appeared in Dash & opened a GUI.
Since my last post, I installed system-config-samba and now "it" appears in Dash, but clicking produces a p/w prompt, then nothing.

This app is not really part of Samba.  It also relies on gksu (gksudo) which is not installed by default anymore.  I don't use this as it is really simple to create shares by editing the smb.conf file directly.
> 

Anyway, here are the outputs you asked for:

```
chris@Acer-TC:~$ ps -ef | grep mbd
root      1855     1  0 21:04 ?        00:00:00 nmbd -D
chris     3548  3478  0 21:19 pts/1    00:00:00 grep --color=auto mbd

```

Samba is not running at this time.  Reboot the machine and try the command again.  Post the results you get.
> 
```



chris@Acer-TC:~$ cat /etc/samba/smb.conf
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



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
;	passdb backend = tdbsam

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
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	username map = /etc/samba/smbusers
	security = user
;	encrypt passwords = yes
;	guest ok = no
;	guest account = nobody

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
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
	writeable = yes
	guest ok = yes
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[Desktop]
	path = /home/chris/Desktop
	writeable = yes
;	browseable = yes
	guest ok = yes
chris@Acer-TC:~$ 
```

And again - many thanks for your patience!

Your edit:

I usually share "Public" file & "Desktop" for all users on all machines in my local network.
At this point we need to determine if you really have the Samba server daemon installed (smbd) before we can move to the issue of shares.  The Samba server daemon should be running whenever you boot up the machine.

Here is what I get when I use *ps -ef | grep mbd* ```
ps -ef | grep mbd
root       841     1  0 08:52 ?        00:00:00 smbd -F
root       873   841  0 08:52 ?        00:00:00 smbd -F
root       875     1  0 08:52 ?        00:00:00 nmbd -D

```

---

### Post by 2CV67 on 2014-09-06
I have gksu anyway.

After reboot:

```
chris@Acer-TC:~$ ps -ef | grep mbd
root      1842     1  0 21:49 ?        00:00:00 nmbd -D
chris     2882  2813  0 21:51 pts/1    00:00:00 grep --color=auto mbd
chris@Acer-TC:~$ 
```

---

### Post by bab1 on 2014-09-06
> **2CV67 said:**
> I have gksu anyway.

After reboot:

```
chris@Acer-TC:~$ ps -ef | grep mbd
root      1842     1  0 21:49 ?        00:00:00 nmbd -D
chris     2882  2813  0 21:51 pts/1    00:00:00 grep --color=auto mbd
chris@Acer-TC:~$ 
```

This tells me that Samba is not installed or not installed correctly.  Let's see if it is installed at all.  Post the output of these commands```
sudo 
ls -l /usr/sbin/smbd

service smbd restart

```
The first command should show if the actual smbd binary is installed.  The second one MAY start the smbd daemon if the first command indicates the smbd binary really exists.

---

### Post by 2CV67 on 2014-09-06
```
chris@Acer-TC:~$ sudo ls -l /usr/sbin/smbd
[sudo] password for chris: 
-rwxr-xr-x 1 root root 65448 Aug  2 00:37 /usr/sbin/smbd
chris@Acer-TC:~$ service smbd restart
stop: Unknown job: smbd
start: Unknown job: smbd
chris@Acer-TC:~$ 
```

---

### Post by bab1 on 2014-09-06
> **2CV67 said:**
> ```
chris@Acer-TC:~$ sudo ls -l /usr/sbin/smbd
[sudo] password for chris: 
-rwxr-xr-x 1 root root 65448 Aug  2 00:37 /usr/sbin/smbd

```

This shows that the smbd binary is installed.
> 
```


chris@Acer-TC:~$ service smbd restart
stop: Unknown job: smbd
start: Unknown job: smbd
chris@Acer-TC:~$ 
```
You forgot to use sudo in the incantation (**sudo** service smbd restart).

---

### Post by 2CV67 on 2014-09-06
:oops: Yeah - I prefer GUI, but let's not start on that now! ;)

```
chris@Acer-TC:~$ sudo service smbd restart
[sudo] password for chris: 
stop: Unknown instance: 
smbd start/running, process 3987
chris@Acer-TC:~$ 

```

---

### Post by bab1 on 2014-09-06
> **2CV67 said:**
> :oops: Yeah - I prefer GUI, but let's not start on that now! ;)

```
chris@Acer-TC:~$ sudo service smbd restart
[sudo] password for chris: 
stop: Unknown instance: 
smbd start/running, process 3987
chris@Acer-TC:~$ 

```

So now what do you get from this (again)```
ps -ef | grep mbd
```

---

### Post by 2CV67 on 2014-09-06
```
chris@Acer-TC:~$ ps -ef | grep mbd
root      1842     1  0 21:49 ?        00:00:00 nmbd -D
chris     4262  4192  0 22:44 pts/1    00:00:00 grep --color=auto mbd
chris@Acer-TC:~$ 
```

---

### Post by bab1 on 2014-09-06
> **2CV67 said:**
> ```
chris@Acer-TC:~$ ps -ef | grep mbd
root      1842     1  0 21:49 ?        00:00:00 nmbd -D
chris     4262  4192  0 22:44 pts/1    00:00:00 grep --color=auto mbd
chris@Acer-TC:~$ 
```

Very odd.  Let's look using a different command.  Post the output of this```
pgrep -l mbd
```

[COLOR="#0000FF"]Edit: My guess is this will fail also.  Which leads me to believe that the actual /etc/init.d/smbd link is broken and therefore the daemon is not being initialized. [/COLOR]

---

### Post by 2CV67 on 2014-09-06
```
chris@Acer-TC:~$ pgrep -l mbd
1842 nmbd
chris@Acer-TC:~$ 
```

---

### Post by bab1 on 2014-09-06
> **2CV67 said:**
> ```
chris@Acer-TC:~$ pgrep -l mbd
1842 nmbd
chris@Acer-TC:~$ 
```

Let's see if the init.d link is broken.  Post the output of this ```
ls -l /etc/init.d/smbd
```

The output should look like this```
lrwxrwxrwx 1 root root 21 Jun 23 13:25 /etc/init.d/smbd -> /lib/init/upstart-job

```

---

### Post by 2CV67 on 2014-09-06
```
chris@Acer-TC:~$ ls -l /etc/init.d/smbd
-rwxr-xr-x 1 root root 1930 Apr  1 19:46 /etc/init.d/smbd
chris@Acer-TC:~$ 
```

---

### Post by bab1 on 2014-09-06
> **2CV67 said:**
> ```
chris@Acer-TC:~$ ls -l /etc/init.d/smbd
-rwxr-xr-x 1 root root 1930 Apr  1 19:46 /etc/init.d/smbd
chris@Acer-TC:~$ 
```
This is a little different than mine but it gets us to the binary's start script I believe.   It used to be a link to that script.  Post the output of this ```
cat /etc/init.d/smbd
```...If I'm correct this is the script that initiates the Samba daemon.

I want to see how it starts the smbd process.

---

### Post by 2CV67 on 2014-09-06
```
chris@Acer-TC:~$ cat /etc/init.d/smbd
#!/bin/sh

### BEGIN INIT INFO
# Provides:          smbd
# Required-Start:    $network $local_fs $remote_fs
# Required-Stop:     $network $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Should-Start:      slapd cups
# Should-Stop:       slapd cups
# Short-Description: start Samba SMB/CIFS daemon (smbd)
### END INIT INFO


PIDDIR=/var/run/samba
SMBDPID=$PIDDIR/smbd.pid

# clear conflicting settings from the environment
unset TMPDIR

# See if the daemons are there
test -x /usr/sbin/smbd || exit 0

. /lib/lsb/init-functions

case $1 in
	start)
		if init_is_upstart; then
			exit 1
		fi
		SERVER_ROLE=`samba-tool testparm --parameter-name="server role"  2>/dev/null | tail -1`
		if [ "$SERVER_ROLE" = "active directory domain controller" ]; then
		    exit 0
		fi

		log_daemon_msg "Starting SMB/CIFS daemon" smbd
		# Make sure we have our PIDDIR, even if it's on a tmpfs
		install -o root -g root -m 755 -d $PIDDIR

		if ! start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/smbd -- -D; then
			log_end_msg 1
			exit 1
		fi

		log_end_msg 0
		;;
	stop)
		if init_is_upstart; then
			exit 0
		fi

		log_daemon_msg "Stopping SMB/CIFS daemon" smbd

		start-stop-daemon --stop --quiet --pidfile $SMBDPID
		# Wait a little and remove stale PID file
		sleep 1
		if [ -f $SMBDPID ] && ! ps h `cat $SMBDPID` > /dev/null
		then
			# Stale PID file, remove it (should be removed by
			# smbd itself IMHO).
			rm -f $SMBDPID
		fi

		log_end_msg 0

		;;
	reload)
		log_daemon_msg "Reloading /etc/samba/smb.conf" smbd

		start-stop-daemon --stop --quiet --signal HUP --pidfile $SMBDPID

		log_end_msg 0
		;;
	restart|force-reload)
		if init_is_upstart; then
			exit 1
		fi
		$0 stop
		sleep 1
		$0 start
		;;
        status)
		status_of_proc -p $SMBDPID /usr/sbin/smbd smbd
		exit $?
		;;
	*)
		echo "Usage: /etc/init.d/smbd {start|stop|reload|restart|force-reload|status}"
		exit 1
		;;
esac

exit 0
chris@Acer-TC:~$ 

```

---

### Post by bab1 on 2014-09-06
> **2CV67 said:**
> ```
chris@Acer-TC:~$ cat /etc/init.d/smbd
#!/bin/sh

....

/usr/sbin/smbd -- -D; 

....

```See if you can start Samba with this```
sudo /usr/sbin/smbd -- -D
```

Post the output of this if you get no errors```
pgrep -l mbd
```

---

### Post by 2CV67 on 2014-09-06
```
chris@Acer-TC:~$ sudo /usr/sbin/smbd -- -D
[sudo] password for chris: 
chris@Acer-TC:~$ pgrep -l mbd
1842 nmbd
chris@Acer-TC:~$
```

---

### Post by bab1 on 2014-09-06
> **2CV67 said:**
> ```
chris@Acer-TC:~$ sudo /usr/sbin/smbd -- -D
[sudo] password for chris: 
chris@Acer-TC:~$ pgrep -l mbd
1842 nmbd
chris@Acer-TC:~$
```

Well that is entirely unexpected.  I have use that exact command to start Samba on one of my servers.  It should always work. All the scripts (including the GUI) directly call this binary.  The /usr/sbin/smbd is the heart of Samba sharing.  If yours doesn't work, it surly must be wounded.  At the worst it should have choked and sent errors tot he terminal for you to see.

If we can't directly call this binary we only have 2 choices:  1) purge all Samba packages and try again or 2) reinstall Ubuntu itself and carefully install Samba in a structured methodical way (This is my choice as we already have tried the other option).  By structured I mean we install the bits in the order I say.

When the OS is installed the client side Samba parts are installed automatically.  This should be the cifs-utils.  At that point I want to see what the various parts look like.  After I see that this is all installed and working correctly we can install Samba server and configure it.

I've installed and configured 100's of Samba servers and never had this kind of problem.  From my perspective it's just easier to reinstall everything,  You do have COMPLETE BACKUPS OF ALL YOUR DATA.  Yes?  Correct?

---

### Post by 2CV67 on 2014-09-06
Yes, I do have 2 independent backups of all my data, but would still be looking at a couple of days tidying up to get back to where I am now.
So I can do a reinstall of Ubuntu, but if there are quicker things to try first...

---

### Post by 2CV67 on 2014-09-06
I think this is where I stop for tonight!

If I/we decide on reinstalling Ubuntu, I can do that myself, up to the Samba part.

If you have any other ideas to test, then I will try them tomorrow morning.

Thank you VERY much for your help!

---

### Post by bab1 on 2014-09-06
> **2CV67 said:**
> Yes, I do have 2 independent backups of all my data, but would still be looking at a couple of days tidying up to get back to where I am now.
So I can do a reinstall of Ubuntu, but if there are quicker things to try first...

No quick things to try anymore.  We can't even make Samba server initiate the two server daemons needed to function.  

No guessing or "hunting and pecking".  It is more a matter of facing the fact that the entire Samba server system is mortally wounded.  We have already tried to purge Samba and start over.  So logically the next step is to install everything back to the default.  Install the OS, let me help with the Samba part.

I will be available next week so that should not be a problem.  Just post here and I will respond.

---

