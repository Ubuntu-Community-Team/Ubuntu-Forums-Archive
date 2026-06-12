---
title: "group permissions"
date: 2015-10-22
forum: General Help
---

### Post by maclenin on 2015-10-22
I have users alpha (sudo) and beta (non-sudo) on the same system.

I would like to give user beta access to the user alpha home directory.

id alpha yields:
```
id alpha
uid=100(alpha) gid=100(alpha) groups=100(alpha)
```
id beta yields:
```
id beta
uid=200(beta) gid=250(other) groups=250(other)
```
Is this access best granted by adding user beta to the user alpha group is this way:
```
usermod -a -G alpha beta
```
Thanks for any guidance!

---

### Post by ajgreeny on 2015-10-22
I think adding users to groups is the way to go for you; you can then set group permissions to be rwx, rw, or just r, if that is what you want with the chmod command; you can set different permissions to the directories in your /home if you want the second user to have access to only some but not all of them.

It is very flexible but takes a bit of getting used to if permissions is not something you have used before.

Your command should work but you can also use:-
Adding a user to a group:
```
sudo adduser user group
```
Removing a user from a group:
```
sudo deluser user group
```

---

### Post by maclenin on 2015-10-24
Thanks for the reply! I think you have me heading down the right path - though a few "sticky" bits remain:

User a wants to give user b access to /home/a/shared/, to allow user b to move files to and from the directory and to allow both user a and user b the ability to read and write files created by either within /home/a/shared/.

Are the read and write aspects resolved by the creation of a "user private group" (if I am using the term properly) - in this way - with user a being the understood owner of /home/a/shared/:
```
usermod -a -G a b
chmod g+s /home/a/shared/
```

Assuming the above is correct - how would this configuration affect the ability of user b to move or copy files to and from /home/a/shared/? Would those files moved or copied by user b to /home/a/shared/ also be readable / writable by user a?

Thanks for any additional wisdom!

---

### Post by bab1 on 2015-10-24
> **maclenin said:**
> Thanks for the reply! I think you have me heading down the right path - though a few "sticky" bits remain:

User a wants to give user b access to /home/a/shared/, to allow user b to move files to and from the directory and to allow both user a and user b the ability to read and write files created by either within /home/a/shared/.

Are the read and write aspects resolved by the creation of a "user private group" (if I am using the term properly) - in this way - with user a being the understood owner of /home/a/shared/:
```
usermod -a -G a b
chmod g+s /home/a/shared/
```

Assuming the above is correct - how would this configuration affect the ability of user b to move or copy files to and from /home/a/shared/? Would those files moved or copied by user b to /home/a/shared/ also be readable / writable by user a?

Thanks for any additional wisdom!

You are not using the term User Private Group correctly.  To read more about User Private Groups see [**here**]("https://www.google.com/search?q=user+private+group&btnG=Go!&gws_rd=ssl").  I would not add different user to any users User Private Group.

The correct way to use groups to manage ownership and permissions with Linux is to create a common group (e.g a group named common) and modify the directory you want to share (e.g. sudo chgrp common /home/a/shared/).  Then set the SGID bit on the root directory that you are sharing (e.g. sudo chmod g+s //home/a/shared/).  Any file or directory created in the shared directory now has the user-group of common.  The umask causes the permissions to be 664 for files and 775 for directories.

---

### Post by maclenin on 2015-10-25
Thanks for the reply - perhaps I was almost there:

user a
gid a <----- is this the point where the notion of "upg" comes into play? uid and gid are the same. user a has a user private group (gid) a?
group a

user b
gid c <----- does user b not have a "upg", by virtue of the fact that the gid is not shared with the uid - and will not have a upg until user b is added to a "common" group - in the way you articulate it in your reply?
group c

> 
[https://wiki.debian.org/UserPrivateGroups#How_It_Works](https://wiki.debian.org/UserPrivateGroups#How_It_Works)

Though it seems I might be able to add user b to the user a group a: To intentionally add one or more (supervisor) users to a (sub-) users UPG and thus allow the supervisor full access to the sub-user's resources (without breaking the umask relaxation UPG scheme).

But I prefer your notion of creating a separate "common" area / group.... Would that common group then be shared - in effect - by the user a and user b user private groups?

Just trying to hammer out my understanding....

Thanks, again.

---

### Post by bab1 on 2015-10-25
> **maclenin said:**
> Thanks for the reply - perhaps I was almost there:

user a
gid a <----- is this the point where the notion of "upg" comes into play? uid and gid are the same. user a has a user private group (gid) a?
group a
As long as there are** no other users** in this group.  
> 
user b
gid c <----- does user b not have a "upg", by virtue of the fact that the gid is not shared with the uid - and will not have a upg until user b is added to a "common" group - in the way you articulate it in your reply?
group c

The entire reason to have UPG is to eliminate the effects of having a separate user group.  With UPG, only the user (creator) has read/write permissions to a file.  The use of UPG means that the umask system can be left as it always has been.  

If you actually were to add a supervisor to the user-group of a particular user you would (in my mind) be breaking the convention.  There is no need to do that anyway.  If you are a sudoer then you can gain access by invoking sudo.  If you are using the root account then you always have access.  There NEVER is a reason to add a user to the UPG group of any user.

Not everything that you read on the Internet is correct...
> 
But I prefer your notion of creating a separate "common" area / group.... Would that common group then be shared - in effect - by the user a and user b user private groups?

Just trying to hammer out my understanding....

Thanks, again.
A group in common is not UPG at all.  You can have different group ownership of separate parts of the file system.  I store shared data at: */srv/share/samba/*.  The ownership is: root:smbusers:others.  The users that have access are part of the *smbusers* group.  Users can be members of multiple groups.  They would still have their own UPG that is used in their home directory.  You can have both scenarios (UPG and shared) simultaneously.

The trick is to use the SGID bit on the root of the shared file system (e.g. /srv/share/samba) to provide group inheritance for the shared data.  If you don't set the SGID bit the data would be created using the UPG group of the user.

What exactly are you trying to do?  Would you like to create a shared file system?  I do not recommend you create a shared area of your home directory.  You should be a sudoer (admin) on the system to set up a shared directory.  Do you have sudo rights?

[COLOR="#0000FF"]Edit:  A much better description of the reasoning behind UPG is [**this**]("https://security.ias.edu/how-and-why-user-private-groups-unix").[/COLOR]

---

### Post by maclenin on 2015-11-02
...just trying to separate wheat from chaff....

...user alpha and user bravo would enjoy sharing a group whiskey. 

a. create user alpha and bravo
```
sudo useradd alpha
sudo passwd alpha
```
...user alpha enjoys ~/ <--- upg (umask 002) / create new dir (775): rwx rwx r x / create new file (664): rw rw r <--- 'x' disabled by default for new file

```
sudo useradd bravo
sudo passwd bravo
```
...user bravo enjoys ~/ <--- upg (umask 002) / create new dir (775): rwx rwx r x / create new file (664): rw rw r <--- 'x' disabled by default for new file

b. create group whiskey
```
sudo groupadd whiskey
```

c. add user alpha and bravo to group whiskey
```
sudo usermod -a -G alpha whiskey
sudo usermod -a -G bravo whiskey
```
...whiskey needs a place to be dispensed - how about /srv/share/pub, for example?

d. make the pub
```
sudo mkdir /srv/share/pub
```

e. associate whiskey with the pub
```
sudo chown root:whiskey /srv/share/pub
```

f. permit users alpha and bravo to share their whiskey at the pub
```
sudo chmod **2**775 /srv/share/pub
```

...whiskey allows alpha and bravo to share files / directories / move documents to and fro the pub, for the setgid bit (**2**775 or g+**s**).

questions:

root@xubuntu:/srv/share/pub$ ls -la shows *root whiskey* <--- the "controlling" owner of the group (whiskey) / directory (pub)?
alpha@xubuntu:/srv/share/pub$ ls -la shows *alpha whiskey* <--- user given access to whiskey and the pub via sudoer / root?
bravo@xubuntu:/srv/share/pub$ ls -la shows *bravo whiskey* <--- user given access to whiskey and the pub via sudoer / root?

...upg is a description of the experience each user enjoys within their ~/ context - and takes on special meaning when it's applied to a group context (i.e. whiskey at the pub), which should usually be governed by different (umask 022) rules?

How does one associate an "application" to a group - i.e. this group can only run this list of executables - or perform these functions?

You bring up samba - so - how is the samba paradigm different from the shared directory concept deployed via upg?

Thanks, again, for any and all comments / criticism / etc....

references:

[http://articles.slicehost.com/2010/7...ions-and-types](http://articles.slicehost.com/2010/7...ions-and-types)
[https://security.ias.edu/how-and-why-user-private-groups-unix](https://security.ias.edu/how-and-why-user-private-groups-unix)

---

### Post by bab1 on 2015-11-02
> **maclenin said:**
> 

questions:

root@xubuntu:/srv/share/pub$ ls -la shows *root whiskey* <--- the "controlling" owner of the group (whiskey) / directory (pub)?

The owner is not "controlling" in this instance.  The group has just as much control.  The owner is just the creator.  The umask is based on the creator's ID.
> 
alpha@xubuntu:/srv/share/pub$ ls -la shows *alpha whiskey* <--- user given access to whiskey and the pub via sudoer / root?
The user alpha has access due to permissions of the directory /srv/share/pub (drwx**[COLOR="#FF0000"]rwx[/COLOR]**r-x) listed in red.  The permissions of **[COLOR="#FF0000"]r[/COLOR]**ead and [COLOR="#FF0000"]w[/COLOR]rite and e**[COLOR="#FF0000"]X[/COLOR]**ecute provide that.  Sudo has nothing to do with directory access in this instance.> 
bravo@xubuntu:/srv/share/pub$ ls -la shows *bravo whiskey* <--- user given access to whiskey and the pub via sudoer / root?

The user bravo has the same access as the user alpha so the above applies exactly the same.
> 
...upg is a description of the experience each user enjoys within their ~/ context - and takes on special meaning when it's applied to a group context (i.e. whiskey at the pub), which should usually be governed by different (umask 022) rules?

The UPG is a access control scheme.  It applies to directories and files created anywhere in the Linux file system.  If the user *alpha* creates a file in it's home directory the ownership should still be *alpha:alpha*.  The access control of /srv/share/pub is set specifically by the SGID bit which overrides the UPG setting.
> 
How does one associate an "application" to a group - i.e. this group can only run this list of executables - or perform these functions?

There are layers of access control, but the basic eXecution rights are set via the permissions.  If a file has the user:group execute bits set on a script of binary blob (774 for the file) then the user and all of those in the user-group can execute the file.  You don't associate the application, you grant eXecution rights.
> 
You bring up samba - so - how is the samba paradigm different from the shared directory concept deployed via upg?

Only as an example and mostly out of habit.  Samba is a set of services that allows a user to mount a portion of remote file system to the local host (computer).  The same access control is applied.

---

### Post by maclenin on 2015-11-05
More (related) questions:

1. user and group creation - root (or a sudoer) are the only two (types of) users permitted to create / manage users and groups?
2. group permissions (alpha) - user alpha has access to the group (and the directory) because root or a sudoer assigned user alpha to the group - or the group to user alpha.... Other users, not assigned to the group, would NOT have access to the directory - unless "o" permissions were modified (by root or a sudoer) to allow "other" access?
3. group permissions (bravo) - same as alpha.
4. upg / sgid - so, essentially, chmod **2**XXX (can XXX be anything?) sets the "gid" - or, effectively, the group's umask (as defined by the group creator('s umask)) for every operation performed within a directory by members of the group assigned the directory (if XXX is 775, then the umask would be 0002)?
4.a. chmod **g+s** will set the gid bit based on how the current group permissions are set? So - if they are currently **r **(drwx**r**--r--) - or 744, then **g+s** will set the "group" umask to 0033?
5. execution rights - if I wanted only users who were members of the "ffx" group to be able to run firefox, how would I set that up? chown root:ffx /usr/bin/firefox? then assign users to the ffx group? Would I need to set the uid bit?
6. samba - I understand, in theory, that samba allows users on different systems to "share" across systems, similarly to what we create, locally, with the upg configuration....
7. If I wanted to create a folder accessible to all - to read(-only) decrees.txt written by root - but not writeable (or executable) by anyone other than root...as root I could create a "door" group, "senate_door" directory, chown root:door, and chmod 744 /srv/shared/senate_door/ (without the "bits" set)?

Thanks for your patience.

---

### Post by bab1 on 2015-11-05
> **maclenin said:**
> More (related) questions:

1. user and group creation - root (or a sudoer) are the only two (types of) users permitted to create / manage users and groups?

The root user is the only user that can create / manage users and groups.  The sudo user can become the root user to execute the commands.  Sudo stands for **[SIZE=2]S[/SIZE]**witch **[SIZE=2]U[/SIZE]**ser and **[SIZE=2]Do[/SIZE]** (some command). 
> 
2. group permissions (alpha) - user alpha has access to the group (and the directory) because root or a sudoer assigned user alpha to the group - or the group to user alpha.... Other users, not assigned to the group, would NOT have access to the directory - unless "o" permissions were modified (by root or a sudoer) to allow "other" access?

3. group permissions (bravo) - same as alpha.
The combination of ownership and permission is what allows or denies user access.  Both of above are correct.
> 

4. upg / sgid - so, essentially, chmod **2**XXX (can XXX be anything?) sets the "gid" - or, effectively, the group's umask (as defined by the group creator('s umask)) for every operation performed within a directory by members of the group assigned the directory (if XXX is 775, then the umask would be 0002)?

**UPG** is a strategy to provide the users with a* private primary group* (no users in it) with the same name as the user (i.e. jsmith:jsmith or john:john).  The tool **chmod** is used to change existing permissions of a file or directory (F/D for here on).  The umask is the filter by which all F/D permissions are set when they are created.  The default umask for root F/D 755/644 while mortal users (human accounts) are 775/664 with Ubuntu. > 

4.a. chmod **g+s** will set the gid bit based on how the current group permissions are set? So - if they are currently **r **(drwx**r**--r--) - or 744, then **g+s** will set the "group" umask to 0033?

The command chmod never sets the umask.  It sets the permissions on* previously created* F/D.  The chmod setting of "g+s" sets the sgid bit on a directory, > 

5. execution rights - if I wanted only users who were members of the "ffx" group to be able to run firefox, how would I set that up? chown root:ffx /usr/bin/firefox? then assign users to the ffx group? Would I need to set the uid bit?
If you want to limit users for executing a script you can *change the group ownership and set the permissions appropriately*.  No, you don't need to set the UID bit.> 
6. samba - I understand, in theory, that samba allows users on different systems to "share" across systems, similarly to what we create, locally, with the upg configuration....
This is not really correct, but Samba is a topic all on its own.
> 
7. If I wanted to create a folder accessible to all - to read(-only) decrees.txt written by root - but not writeable (or executable) by anyone other than root...as root I could create a "door" group, "senate_door" directory, chown root:door, and chmod 744 /srv/shared/senate_door/ (without the "bits" set)?
Why do all of that?  Just set the permissions to 755 on the directory and 644 on the file.

All of this is documented in the various man pages for sudo umask chmod chown etc.  Try something like this```
man umask
```
There is plenty of this on the web also.  You can Google using any of the terms.

A good link for the basic terms is [**this**]("http://www.zzee.com/solutions/unix-permissions.shtm")

---

### Post by maclenin on 2015-11-06
Thank you - and I hear you re: RTFM (a catch-all for read the "F"abulous man pages and google)...though there are times when human intervention - to flesh out the man pages and help distil the truth from the internet - proves vital....
> Not everything that you read on the Internet is correct...

1., 2. and 3. Great - I'll put these to rest.

4. and 4.a. and 5. group permissions (and upg?)....

root creates a shared_group
root (default umask 0022) creates a directory with (default) permissions (755) drwxrxrx / files (644) rwrr
root chown root:shared_group directory
root creates mortal user (default umask 0002 / (775) drwxrwxrx / (664) rwrwr) alpha and (by default?) a (u)pg "alpha" 
root creates mortal user (default umask 0002 / (775) drwxrwxrx / (664) rwrwr) bravo and (by default?) a (u)pg "bravo"
root adds user alpha to shared_group 
root adds user bravo to shared_group 

IF root invokes **chmod g+s directory**, with default permissions, then (2755) drwx**rsx**rx / (644) rwrr - no?
umask of user alpha and user bravo irrelevant. upg irrelevant. No?
root (umask + chmod + s) defined shared_group / directory permissions (**rsx**) relevant. Creators can read and write, other shared_group members can only read.

IF root invokes **chmod 2775 directory**, then (2775) drwx**rws**rx / (664) rwrwr - no?
umask of user alpha and user bravo irrelevant. upg irrelevant. No?
root (umask + chmod + s) defined shared_group / directory permissions (**rws**) relevant. Creators and other shared_group members can read and write.

Which begs: How is UPG relevant in this shared_group context?

6. samba - yep - under separate cover....

7. see 4.

Thanks, again!

---

### Post by bab1 on 2015-11-06
> **maclenin said:**
> ...

4. and 4.a. and 5. group permissions (and upg?)....

root creates a shared_group
root (default umask 0022) creates a directory with (default) permissions (755) drwxrxrx / files (644) rwrr
root chown root:shared_group directory
root creates mortal user (default umask 0002 / (775) drwxrwxrx / (664) rwrwr) alpha and (by default?) a (u)pg "alpha" 
root creates mortal user (default umask 0002 / (775) drwxrwxrx / (664) rwrwr) bravo and (by default?) a (u)pg "bravo"
root adds user alpha to shared_group 
root adds user bravo to shared_group 

IF root invokes **chmod g+s directory**, with default permissions, then (2755) drwx**rsx**rx / (644) rwrr - no?

This is correct.  Adding the sgid bit does not change the access permissions.
> 

umask of user alpha and user bravo irrelevant. upg irrelevant. No?

The users umask is not relevant unless the user creates a file or directory.  The users UPG is still configured for anything outside this context.  Think about what happens when the user creates a new file in their home directory.  
> 

root (umask + chmod + s) defined shared_group / directory permissions (**rsx**) relevant. Creators can read and write, other shared_group members can only read.

IF root invokes **chmod 2775 directory**, then (2775) drwx**rws**rx / (664) rwrwr - no?

Yes.  Root always needs to set sgid and the appropriate permissions.
> 

umask of user alpha and user bravo irrelevant. upg irrelevant. No?

The users umask is relevant only when creating a file or a subdirectory of the shared directory.  See above re: UPG.
> 

root (umask + chmod + s) defined shared_group / directory permissions (**rws**) relevant. Creators and other shared_group members can read and write.

Correct...
> 

Which begs: How is UPG relevant in this shared_group context?

It is not relevant other than to know that it is the starting point.  The user's primary group is still UPG configured, but the sgid bit of the directory ultimately determines the file's user-group owner.  **When the sgid bit is set **on a directory and a new file is created in the that directory,  **the file will inherit the group of the directory* _(not of the user group who created the file)_***.

I think you need to create this file structure and see how it really works first hand.  There is no substitute for real experience.

---

