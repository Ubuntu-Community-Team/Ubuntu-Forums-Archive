---
title: "Security &amp; permissions related to Samba"
date: 2008-03-28
forum: General Help
---

### Post by RTAdams89 on 2008-03-28
First off, thanks for taking the time to read this. I am very proficient with Windows, but am new to Linux. Recently, a company I do freelance work for asked me about setting up a simple file server for their network of about 15 users. I've since come to Ubuntu to try to accomplish that. 

Right now I am trying everything in a virtual machine running Ubuntu 7.1. I've read tutorials on Samba and have managed to get it working for the most part, but I have a few questions regarding security.

First, to allow people access to the shares they have to have a local Ubuntu account. How do I prevent them from being able to log in locally or over SSH? Basically, all these users should be able to do is interact with the Samba server.

Second, the tutorials I have read tell me to add a section similar to this:
```
[allusers]
  comment = All Users
  path = /home/shares/allusers
  valid users = @users
  force group = users 
  create mask = 0660
  directory mask = 0771
  writable = yes
```

at the end of the smb.conf file. I understand that creates a share, but I don't understand all of the lines. I've read the Samba manual and the description of each parameter, but I'm still confused. Could some one explain in layman's terms what:

-the "@" in the valid users lien means
-the force group line does
-what the directory and create mask do
-why the "writable" line is needed since permissions for the folder are set elsewhere already

Last but not least, if I want a share to be accessible by a group (not a single user) how do I state that in the smb.conf file?

---

### Post by SpaceTeddy on 2008-03-29
> First, to allow people access to the shares they have to have a local Ubuntu account

this is only partly true. Samba can use the normal pam module to authenticate users, but if you do not want users to show up anywhere else, it would be better to use the internal samba configuration user manager. this can be done via smbpasswd.

to use it you need to run it as root - so try looking at the help with this command
```
smbpasswd --help
```
this will let you add users to samba without creating a local account for them. NOTE: this will mean that the users will NOT get personal homedrive !!!

> How do I prevent them from being able to log in locally or over SSH?
either you do what i described before - only adding the users for samba. Then SSH will not know about the accounts...

if that is not desired, you can restrict the ssh server to only allow specific users to login via it. This option can be added in the config in /etc/ssh/sshd_config
```
AllowUsers user1, user2, user3
```

then restart the ssh-server and only the specified users can login via ssh. all others will be blocked by wrong username/password even if they type in a valid login.

> -the "@" in the valid users lien means
it means group. anything specified with a @ infront there means that this applies to all people in the group instead of a single users. So in this case, it would means anyone who is a member of the group users (does this also answers you last question aswell?)

> -the force group line does
every user on ubuntu has a username (uid) and primary group (gid). by default, if a users creates a file, the file will have the uid and gid of the user who created it. With force-group you can overwrite the gid of a file that a user creates. 
Example: Lets say you have a user called joe who has the primary group staff. Joe is also able to log onto a share where normal users can read and write as long as the files belong to the goup "users". But any file that joe creates will have the gid of staff, not users (his primary group), thus nobody can do anything to the file. To prevent this, you can force shares to overwrite the default gid. In that case,  joes gid (staff) will be overwritten by users. Now everybody can do anything to the file.


> -what the directory and create mask do
the create and directory masks say what permissions new files get. These come directly from the filesystem and will also be handed down directly there. I have never figured out what the first number is for (just leave it 0 or ommit it) - but the other three work as follow:
rights for owner, right for group, right for anyone else. 
each of these is a number - consisting of three features. 
1 = the file can be executed
2 = the file can be written to
4 = the file can be read

so, lets say you have a mask of 0660 and it has the uid joe and the gid staff
this would mean that joe can read and write the file due to the first 6 (write + read = 2 + 4 = 6).Also, anyone in group staff gets the same right. Anyone else cannot do anything to the file, because of the 0 - they do not have any rights.

the same is true for the directory entry - they work the exact same way - BUT. for directory, to open them, you need to have the exectue right. that why a file is 0660 and a directory is 0771 (adding the extra 1 to every position gives anyone the right to browse the directory.)

> -why the "writable" line is needed since permissions for the folder are set elsewhere already
writeable is usually set via the file permissions down on the filesystem level. The writeable = yes is the default and can be left out. This option is afaik only for write-protecting shares entirely. For example, if you have a share where auto generated files get placed (i.e. faxes or pdf printouts) you do not want users to "accidentily" delete them. So you writeprotect the full share, and clean it via a script at night. 

so, i hope i made some sense and cleared a few questions :)

---

