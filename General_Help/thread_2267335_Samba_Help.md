---
title: "Samba Help"
date: 2015-02-28
forum: General Help
---

### Post by fzaman2 on 2015-02-28
Hey all,

So I am having some issues getting Samba to work the way it should.  Here is what I have:

Server name: zserver
Users: fzaman, rzaman
ZFS file system for each user at ```
/tank/*user *
```as well as a Shared file system at ```
*/tank/Shared*
```

3 computers in the house, 2 Mac OS, 1 Windows along with the Ubuntu 14.04 server trying to access the Samba shares

Issues I am having:

I can read/write to /tank/fzaman from all 3 computers by logging in w/ fzaman username and password.  I have fzaman as a valid user for ```
/tank/rzaman
``` in smb.conf as well but can't access that share.

For user rzaman, I can't get anything to work...won't log into it from any computer.  It's like the user does not exit, but I checked to ensure user and password was created correctly.

I also can't access the Shared filesystem from any of the 3 computers with or without username.

Here is the printout for ```
cat /etc/samba/smb.conf
```

```
#======================= Global Settings =======================

[global]


## Browsing/Identification ###




   workgroup = ZWORKGROUP
   server string = Samba Server
   wins support = yes
   dns proxy = no    


;   wins server = w.x.y.z


#### Networking ####


;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = yes


#### Debugging/Accounting ####


   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0


;   panic action = /usr/share/samba/panic-action %d




####### Authentication #######


   server role = standalone server


;   passdb backend = tdbsam
;   obey pam restrictions = yes
;   unix password sync = yes
;   passwd program = /usr/bin/passwd %u
;   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


   pam password change = no
   map to guest = bad user


########## Domains ###########


;   logon path = \\%N\profiles\%U
#   logon path = \\%N\%U\profile
;   logon drive = H:
#   logon home = \\%N\%U
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
; add group script = /usr/sbin/addgroup --force-badname %g


############ Misc ############


;   include = /home/samba/etc/smb.conf.%m
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   usershare max shares = 100


   usershare allow guests = yes


#======================= Share Definitions =======================


;[homes]
;   comment = Home Directories
;   browseable = no
;   read only = yes
;   create mask = 0700
;   directory mask = 0700
;   valid users = %S


;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes


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


[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @lpadmin


[Shared]


path = /tank/Shared
public = yes
writable = yes
create mask = 0775
directory mask = 0775


[fzaman]
path = /tank/fzaman
public = no
valid users = fzaman
writable = yes


[rzaman]
path = /tank/rzaman
public = no
valid users = rzaman, fzaman
writable = yes
```

I am sure there are some simple settings I am missing, but after a couple days of working on this I probably need some help.

Thanks in advance.

---

### Post by bab1 on 2015-03-01
> **fzaman2 said:**
> Hey all,

So I am having some issues getting Samba to work the way it should.  Here is what I have:

Server name: zserver
Users: fzaman, rzaman
ZFS file system for each user at ```
/tank/*user *
```as well as a Shared file system at ```
*/tank/Shared*
```

3 computers in the house, 2 Mac OS, 1 Windows along with the Ubuntu 14.04 server trying to access the Samba shares

Issues I am having:

I can read/write to /tank/fzaman from all 3 computers by logging in w/ fzaman username and password.  I have fzaman as a valid user for ```
/tank/rzaman
``` in smb.conf as well but can't access that share.

For user rzaman, I can't get anything to work...won't log into it from any computer.  It's like the user does not exit, but I checked to ensure user and password was created correctly.

I also can't access the Shared filesystem from any of the 3 computers with or without username.

Here is the printout for ```
cat /etc/samba/smb.conf
```

```

#======================= Share Definitions =======================
[Shared]


path = /tank/Shared
public = yes
writable = yes
create mask = 0775
directory mask = 0775


[fzaman]
path = /tank/fzaman
public = no
valid users = fzaman
writable = yes


[rzaman]
path = /tank/rzaman
public = no
valid users = rzaman, fzaman
writable = yes
```

I am sure there are some simple settings I am missing, but after a couple days of working on this I probably need some help.

Thanks in advance.
Let's start with some info about the system.  Post the output of these terminal commands from the Samba server```

ls -l /tank

sudo pdbedit -L

```
This will tell me what the underlying ownership and permission are for the file system and the Samba users you have created.

The Linux file system is provides access to the shared directory not Samba.  The Samba share is application only access.  If the user is not in the Samba users database then you won't have access to the Samba share at all.

---

### Post by fzaman2 on 2015-03-01
> **bab1 said:**
> Let's start with some info about the system.  Post the output of these terminal commands from the Samba server```

ls -l /tank

sudo pdbedit -L

```
This will tell me what the underlying ownership and permission are for the file system and the Samba users you have created.

The Linux file system is provides access to the shared directory not Samba.  The Samba share is application only access.  If the user is not in the Samba users database then you won't have access to the Samba share at all.

For 

```
ls -l /tank
```

it returns

```

total 26drwxr-xr-x 3 fzaman root 3 Feb 28 16:24 fzaman
drwxr-xr-x 2 rzaman root 2 Feb 28 15:47 rzaman
drwxr-xr-x 2 root   root 2 Feb 28 15:47 shared
```

for

```
sudo pdbedit -L
```

it returns

```
fzaman:1000:Farakh Zaman
```

---

### Post by bab1 on 2015-03-01
> **fzaman2 said:**
> For 

```
ls -l /tank
```

it returns

```

total 26drwxr-xr-x 3 fzaman root 3 Feb 28 16:24 fzaman
drwxr-xr-x 2 rzaman root 2 Feb 28 15:47 rzaman
drwxr-xr-x 2 root   root 2 Feb 28 15:47 shared
```

for

```
sudo pdbedit -L
```

it returns

```
fzaman:1000:Farakh Zaman
```
You need to make rzaman a samba user; like this```
sudo smbpasswd -a rzaman
```...This should allow that user to use the share //SERVER_NAME/rzaman.  

If you also want to access this share then you need to have file system permissions.  The file permissions are: user:user-group:all-others.  The simple way to do this is to have both users in a common group and make that group the user-group owner of the directory.  Something like this```

drwxrw**[COLOR="#0000FF"]s[/COLOR]**r-x 2 rzaman [COLOR="#FF0000"]common[/COLOR] 2 Feb 28 15:47 rzaman
```...the above directory is owned by the user-group named [COLOR="#0000FF"]common[/COLOR].  You need to add both users to this group.  The directory also has the[COLOR="#0000FF"]** sgid **[/COLOR]bit set.  This forces all file and directories created in the directory to have the user-group [COLOR="#0000FF"]common[/COLOR].

The share named //SERVERNAME/shared should also have a common user-group.  If you are going to have more users that just the 2 you have now then you should use a another different user-group.
I generally use the builtin group *users* for a common group and make a new group if I have just a few users that need access to a share.  Is this what you want to do?  If so, I will walk you through the steps to set this up.

---

### Post by fzaman2 on 2015-03-03
> **bab1 said:**
> You need to make rzaman a samba user; like this```
sudo smbpasswd -a rzaman
```...This should allow that user to use the share //SERVER_NAME/rzaman.  

If you also want to access this share then you need to have file system permissions.  The file permissions are: user:user-group:all-others.  The simple way to do this is to have both users in a common group and make that group the user-group owner of the directory.  Something like this```

drwxrw**[COLOR=#0000FF]s[/COLOR]**r-x 2 rzaman [COLOR=#FF0000]common[/COLOR] 2 Feb 28 15:47 rzaman
```...the above directory is owned by the user-group named [COLOR=#0000FF]common[/COLOR].  You need to add both users to this group.  The directory also has the[COLOR=#0000FF]** sgid **[/COLOR]bit set.  This forces all file and directories created in the directory to have the user-group [COLOR=#0000FF]common[/COLOR].

The share named //SERVERNAME/shared should also have a common user-group.  If you are going to have more users that just the 2 you have now then you should use a another different user-group.
I generally use the builtin group *users* for a common group and make a new group if I have just a few users that need access to a share.  Is this what you want to do?  If so, I will walk you through the steps to set this up.

Hey...thanks so much.  I knew it was something simple I would be missing.  I added her as a user in Samba and that got that piece working.  

Yes, if you cold walk me through the setup of groups and changing folder owners that would be helpful too.

Again, thanks!

---

### Post by bab1 on 2015-03-03
The steps are simple.  The first thing to do is add the users to a common group.  Since this is going to be a public share with many users we will use the built in group named ***users***.  You can see this group with this command```
getent group users
```...on my personal machine it looks like this```
users:x:100:bab
```

To add the users you use this command```
sudo adduser <username> <group> 
```...substitute your user names and the user group of your choice.

If you want to create a user group use this command```
addgroup --gid (some gid number > 2000) <group name>
``` The --gid 2000 (or >) is so you don't use gid's that might be used to match a new users uid/gid's.  This is more a neatness thing and not essential.  

An example would look like this```
addgroup --gid 2000 shared
```

Now you need to change the group ownership of the /tank/shared with this command```
sudo chown root:<group> /tank/shared
```...if we use the user group named users it would be like this```
sudo chown root:users /tank/shared
```.

The directory should look like this```
drwxr-xr-x 2 root   users 2 Feb 28 15:47 shared
```...The permissions need to be set like this```
sudo chmod 775 /tank/shared
```

Now you need to add group-user inheritance so that the group ownership is preserved when new files or directories are created.  This is the command```
sudo chmod g+s /tank/shared
```

Now the /tank/shared directory is ready for the new public share.  The Samba share should look like this```

[Shared]
path = /tank/shared
guest ok =yes
create mask = 0664
directory mask = 0775
force [s]user[/s][COLOR="#FF0000"] group [/COLOR]  = users

```

The *writeable* parameter is not needed as the directory allows this already.  The parameter *public* is the same as *guest*.  I think guest is more to the point, but it really is a matter of taste.  The *force user * parameter is used when a _guest user with no login uses the share_.  In that case the user is *nobody* and the group is *nogroup*.  The force group insures that the user-group is always the group named  *users*.

I changed the /tank/Shared to /tank/shared.  Linux is case sensitive Shared is not the same as shared.  Linux people use lower case by habit.  It's consistent and you don't need the shift key.  ;-)

If you need more help just ask here.

---

### Post by fzaman2 on 2015-03-04
> **bab1 said:**
> The steps are simple.  The first thing to do is add the users to a common group.  Since this is going to be a public share with many users we will use the built in group named ***users***.  You can see this group with this command```
getent group users
```...on my personal machine it looks like this```
users:x:100:bab
```

To add the users you use this command```
sudo adduser <username> <group> 
```...substitute your user names and the user group of your choice.

If you want to create a user group use this command```
addgroup --gid (some gid number > 2000) <group name>
``` The --gid 2000 (or >) is so you don't use gid's that might be used to match a new users uid/gid's.  This is more a neatness thing and not essential.  

An example would look like this```
addgroup --gid 2000 shared
```

Now you need to change the group ownership of the /tank/shared with this command```
sudo chown root:<group> /tank/shared
```...if we use the user group named users it would be like this```
sudo chown root:users /tank/shared
```.

The directory should look like this```
drwxr-xr-x 2 root   users 2 Feb 28 15:47 shared
```...The permissions need to be set like this```
sudo chmod 775 /tank/shared
```

Now you need to add group-user inheritance so that the group ownership is preserved when new files or directories are created.  This is the command```
sudo chmod g+s /tank/shared
```

Now the /tank/shared directory is ready for the new public share.  The Samba share should look like this```

[Shared]
path = /tank/shared
guest ok =yes
create mask = 0664
directory mask = 0775
force user = users

```

The *writeable* parameter is not needed as the directory allows this already.  The parameter *public* is the same as *guest*.  I think guest is more to the point, but it really is a matter of taste.  The *force user * parameter is used when a _guest user with no login uses the share_.  In that case the user is *nobody* and the group is *nogroup*.  The force group insures that the user-group is always the group named  *users*.

I changed the /tank/Shared to /tank/shared.  Linux is case sensitive Shared is not the same as shared.  Linux people use lower case by habit.  It's consistent and you don't need the shift key.  ;-)

If you need more help just ask here.

Hey,

So I went through and updated the two users (fzaman, rzaman) to be in the group users.  I can now access /tank/fzaman and /tank/rzaman as I need to.  However the /tank/shared didn't work as well.  I thought maybe it was because I originally created that directory as /tank/Shared with a capital 'S' so I destroyed that ZFS filesystem and created /tank/shared with a lower case 's' and made sure ownership of it was for the group users...however I still get an error when I try to access it.

Any thoughts?

---

### Post by bab1 on 2015-03-05
> **fzaman2 said:**
> Hey,

So I went through and updated the two users (fzaman, rzaman) to be in the group users.  I can now access /tank/fzaman and /tank/rzaman as I need to.  However the /tank/shared didn't work as well.  I thought maybe it was because I originally created that directory as /tank/Shared with a capital 'S' so I destroyed that ZFS filesystem and created /tank/shared with a lower case 's' and made sure ownership of it was for the group users...however I still get an error when I try to access it.

Any thoughts?
Rather than guessing show the results of your work```

ls -l /tank

cat /etc/samba/smb.conf

getent group users
```

---

### Post by fzaman2 on 2015-03-05
> **bab1 said:**
> Rather than guessing show the results of your work```

ls -l /tank

cat /etc/samba/smb.conf

getent group users
```

Here is the output

```
fzaman@zserver:~$ ls -l /tanktotal 26
drwxr-xr-x 3 root fzaman 5 Mar  4 18:15 fzaman
drwxr-xr-x 2 root users  4 Mar  2 20:00 rzaman
drwxr-xr-x 2 root users  2 Mar  4 18:18 shared
fzaman@zserver:~$ cat /etc/samba/smb.conf
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




   workgroup = ZWORKGROUP
   server string = Samba Server
   wins support = yes
   dns proxy = no       


;   wins server = w.x.y.z


#### Networking ####


;   interfaces = 127.0.0.0/8 eth0
;   bind interfaces only = yes


#### Debugging/Accounting ####


   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0


;   panic action = /usr/share/samba/panic-action %d




####### Authentication #######


   server role = standalone server


;   passdb backend = tdbsam
;   obey pam restrictions = yes
;   unix password sync = yes
;   passwd program = /usr/bin/passwd %u
;   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .


   pam password change = no
   map to guest = bad user


########## Domains ###########


;   logon path = \\%N\profiles\%U
#   logon path = \\%N\%U\profile
;   logon drive = H:
#   logon home = \\%N\%U
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
; add group script = /usr/sbin/addgroup --force-badname %g


############ Misc ############


;   include = /home/samba/etc/smb.conf.%m
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   usershare max shares = 100


   usershare allow guests = yes


#======================= Share Definitions =======================


;[homes]
;   comment = Home Directories
;   browseable = no
;   read only = yes
;   create mask = 0700
;   directory mask = 0700
;   valid users = %S


;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes


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


[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
;   write list = root, @lpadmin


[Shared]


path = /tank/shared
guest ok = yes
create mask = 0664
directory mask = 0775
force user = users


[fzaman]
path = /tank/fzaman
public = no
valid users = fzaman
writable = yes


[rzaman]
path = /tank/rzaman
public = no
valid users = rzaman, fzaman
writable = yes


fzaman@zserver:~$ getent group users
users:x:100:fzaman,rzaman
fzaman@zserver:~$ 



```

---

### Post by Holger_Gehrke on 2015-03-05
I think it should be 'force **group** = users'. 'force user' makes samba switch to the given user, and there probably is no user named 'users' ...

---

### Post by bab1 on 2015-03-05
> **Holger_Gehrke said:**
> I think it should be 'force **group** = users'. 'force user' makes samba switch to the given user, and there probably is no user named 'users' ...
Yes you are correct.  I have corrected that above (in red).

---

### Post by bab1 on 2015-03-05
> **fzaman2 said:**
> Here is the output

```
fzaman@zserver:~$ ls -l /tanktotal 26
drwxr-xr-x 3 root fzaman 5 Mar  4 18:15 fzaman
drwxr-xr-x 2 root users  4 Mar  2 20:00 rzaman
drwxr-xr-x 2 root users  2 Mar  4 18:18 shared

```

There are 2 problems here.  First the permissions are not 07**[COLOR="#0000FF"]7[/COLOR]**5 for the shared directory.  It is set to 07[COLOR="#FF0000"]5[/COLOR]5.  The numbers I have highlighted in color are the use-group permissions.  The blue setting is for read, write and eXecute.  You need the write permission or you can't create or modify the files in the directory.  The red number is read only and the eXecute bit allows you to enter the directory.  This happens because the root user creates files and directories that the group and others permissions are read only.  Normal users on Ubuntu create directories with 0775 permissions so future files and directories will work as expected.

You need to change the permissions on the /tank/shared directory like this```
sudo chmod 0775 /tank/shared
```

You also need to preserve user-group inheritance.  If you do not do this, new files and directories will have the user-group of the creator (e.g. rzaman:rzaman)) What you want the files and directories to have the group-owner to always be the group named *users*.  (e.g.  rzaman:users or fzaman:users).

To set user-group inheritance you user this command```
sudo chmod g+s /tank/shared
```

I notice that /tank/rzaman needs this also.  With out it you have the same problem latter on.  You will not be able to create anything in the sub-directories that your wife creates.  You will have read only access only.

The directory permissions should look link the line in blue.  Right now it looks like the line in red```

drwx**[COLOR="#0000FF"]rws[/COLOR]**r-x
drwx**[COLOR="#FF0000"]r-x[/COLOR]**r-x

```

> 



The error that @Holger_Gehrke points out needs to be fixed also.  The correct share should be this (the corrected part is in blue)
```
[Shared]


path = /tank/shared
guest ok = yes
create mask = 0664
directory mask = 0775
force [COLOR="#0000FF"]**group**[/COLOR] = users
```

---

### Post by fzaman2 on 2015-03-06
thanks trying that out now...

---

### Post by fzaman2 on 2015-03-06
Ok, so I finally got it working!  Thanks for all of your help.  I was still having a problem w/ the shared file...I couldn't write to it so I inserted ```
writable = yes
``` into the smb.conf file under shared and that got it working.

Thanks again...now to go figure out how to get apache and vsftpd working next.  In case either of you are experts at that...feel free to chime in to those threads [here]("http://ubuntuforums.org/showthread.php?t=2268086&p=13240341#post13240341")

---

