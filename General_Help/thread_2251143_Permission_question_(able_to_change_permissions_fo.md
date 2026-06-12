---
title: "Permission question (able to change permissions for users under specific folder)"
date: 2014-11-02
forum: General Help
---

### Post by eltiti55555 on 2014-11-02
[COLOR=#333333]Hello,[/COLOR]

[COLOR=#333333]As I understand it, If I want to give an user access to a file or folder I would need to add them to the group that has the right access to those specific files and folders, which can be easily done as root.[/COLOR]

[COLOR=#333333]Now, let's say that I have a person who has full access to their folder, and every folder and file underneath it (maybe 3 levels deep). Each of those 3 folders have 3 other people (one for each folder) who are only able to RWE their own personal folder (1 out of the 3), but nothing else.[/COLOR]

[COLOR=#333333]How can I make the person on top who has full access to their own folder, plus the 3 under them, be able to give the 3 people under him full access to any of the 3 folders under his domain, just as root can give and take away access from any user in the system.[/COLOR]

[COLOR=#333333]Thanks![/COLOR]

---

### Post by Rocket2DMn on 2014-11-02
If somebody else knows otherwise, please jump in, but I do not believe users have that fine-grained level of control.  The file system permissions in Linux allow setting a user and a group owner, so the permissions must be configured at that level.

It sounds like you want the top level user to have user ownership of the subdirectories so they can manipulate the permissions on them.  You cannot assign more than one user directory permissions without using groups.  I believe you would need to create a group for every combination of the three users.  The top level owner could then change the group ownership of the directories while holding the user ownership him/herself.

---

### Post by eltiti55555 on 2014-11-02
> **Rocket2DMn said:**
> If somebody else knows otherwise, please jump in, but I do not believe users have that fine-grained level of control.  The file system permissions in Linux allow setting a user and a group owner, so the permissions must be configured at that level.

It sounds like you want the top level user to have user ownership of the subdirectories so they can manipulate the permissions on them.  You cannot assign more than one user directory permissions without using groups.  I believe you would need to create a group for every combination of the three users.  The top level owner could then change the group ownership of the directories while holding the user ownership him/herself.

What if I used ACL? 

In short my point was to know if I could do something like : adduser username groupname  (as a regular user who has full access to a folder and everything beneath it) or can this be done only by root?

---

### Post by Rocket2DMn on 2014-11-02
With classic groups, only root can make those changes.  Groups are a property of the system (or even a set of systems if you are using directory services like AD or LDAP).

I haven't used ACL myself, but it appears that it should fulfill your need.  This is an extension to the standard UNIX file system permissions and any drives you want to use this on must be mounted with ACL enabled.  Of course, if the drive is ever mounted without it, the ACL permissions will not work.

If you're only dealing with a handful of users, you can feasibly manipulate the ACL permissions on a user level, like your original question seems to imply you want.  I haven't heard of any ACL-defined groups in the documentation I've read, but I suppose it's possible that there is such a thing.  If they do exist, I'd be interested to know about it.  If not, your groups still need to be setup on the system, which requires sudo/root privileges.

---

### Post by eltiti55555 on 2014-11-02
> **Rocket2DMn said:**
> With classic groups, only root can make those changes.  Groups are a property of the system (or even a set of systems if you are using directory services like AD or LDAP).

I haven't used ACL myself, but it appears that it should fulfill your need.  This is an extension to the standard UNIX file system permissions and any drives you want to use this on must be mounted with ACL enabled.  Of course, if the drive is ever mounted without it, the ACL permissions will not work.

If you're only dealing with a handful of users, you can feasibly manipulate the ACL permissions on a user level, like your original question seems to imply you want.  I haven't heard of any ACL-defined groups in the documentation I've read, but I suppose it's possible that there is such a thing.  If they do exist, I'd be interested to know about it.  If not, your groups still need to be setup on the system, which requires sudo/root privileges.

Is ACL enable by default? I have seen videos on how to set it up, and only 1 one of them the guy mounts the drive (not familiar with this), but in most people just create an ACL and add users and groups to it.

---

### Post by bab1 on 2014-11-02
> **eltiti55555 said:**
> [COLOR=#333333]Hello,[/COLOR]

[COLOR=#333333]As I understand it, If I want to give an user access to a file or folder I would need to add them to the group that has the right access to those specific files and folders, which can be easily done as root.[/COLOR]

[COLOR=#333333]Now, let's say that I have a person who has full access to their folder, and every folder and file underneath it (maybe 3 levels deep). Each of those 3 folders have 3 other people (one for each folder) who are only able to RWE their own personal folder (1 out of the 3), but nothing else.[/COLOR]

[COLOR=#333333]How can I make the person on top who has full access to their own folder, plus the 3 under them, be able to give the 3 people under him full access to any of the 3 folders under his domain, just as root can give and take away access from any user in the system.[/COLOR]
[COLOR=#333333]Thanks![/COLOR]

Only root can change ownership (e.g UID).  The owner (and root) can change the group (GID).  Full rights are only available to the owner of the directory or file.
> 
What if I used ACL?  In short my point was to know if I could do something like : adduser username groupname (as a regular user who has full access to a folder and everything beneath it) or can this be done only by root?"]

Only root can use the tool "adduser"  Root can set ACL's for groups.  Root can set group ACL's with either of these commands```
# setfacl -m "g:groupname:permissions"

# setfacl -m "g:gid:permissions"

```
In the end as @ Rocket2DMn has suggested; this is not the way to manage any branch of a file system.  It will quickly become un-manageable.  All future files and directories will be *created* with that users default ownership (user:usergroup).  Not with the group ownership of the directory above.

In the end each user needs to have a separate branch if you want that owner to have control of their files and folders.  Just as */home* is,

---

### Post by bab1 on 2014-11-02
> **eltiti55555 said:**
> Is ACL enable by default? I have seen videos on how to set it up, and only 1 one of them the guy mounts the drive (not familiar with this), but in most people just create an ACL and add users and groups to it.
If it is not then you (as root) can install the package for it.  You must declare the use of ACL's at mount time for ACL's to be used.

---

### Post by eltiti55555 on 2014-11-02
> **bab1 said:**
> If it is not then you (as root) can install the package for it.  You must declare the use of ACL's at mount time for ACL's to be used.

Thanks a lot for the clarifications. On the topic of ACL's, what would be the command to check if my system has them enabled by default?

---

### Post by bab1 on 2014-11-02
> **eltiti55555 said:**
> Thanks a lot for the clarifications. On the topic of ACL's, what would be the command to check if my system has them enabled by default?
dpkg -l |grep acl

---

### Post by eltiti55555 on 2014-11-02
> **bab1 said:**
> dpkg -l |grep acl

Thank you :)

---

### Post by eltiti55555 on 2014-11-02
On a complete different note, how can I force new passwords to be at least 7 characters long? Thanks!

---

### Post by eltiti55555 on 2014-11-02
Reading on another forum I was told that: "o[COLOR=#333333]nly root, or a sudoer can use adduser but a files owner can use setfacl to give permissions to another user on the system"

With that in mind, i[/COLOR]s there a way in which I could just make an user a file owner (using setfacl) to all the folders that are under his name. 

For example:
[http://postimg.org/image/r4zakid27/](http://postimg.org/image/r4zakid27/)


I would like to make the EA, President and VP file owners of every folder under VP, so that they can basically give and take away permissions with setfacl to the users who are part of those folders/files.

Technically all those folders already have file owners, but with ACLs I believe that I can sort of make other users file owners as well, correct?

---

### Post by bab1 on 2014-11-02
> **eltiti55555 said:**
> On a complete different note, how can I force new passwords to be at least 7 characters long? Thanks!

Off topic.  Start a new thread for this.

---

### Post by bab1 on 2014-11-02
> **eltiti55555 said:**
> Reading on another forum I was told that: "o[COLOR=#333333]nly root, or a sudoer can use adduser but a files owner can use setfacl to give permissions to another user on the system"

With that in mind, i[/COLOR]s there a way in which I could just make an user a file owner (using setfacl) to all the folders that are under his name. 

For example:
[http://postimg.org/image/r4zakid27/](http://postimg.org/image/r4zakid27/)


I would like to make the EA, President and VP file owners of every folder under VP, so that they can basically give and take away permissions with setfacl to the users who are part of those folders/files.

Technically all those folders already have file owners, but with ACLs I believe that I can sort of make other users file owners as well, correct?

Not going to happen.  No* sort of*, no *maybes*.  Ownership is not the same thing as permissions.  ACL's are for permissions only.  Permissions are for read (r) write (w) and execute (x).

---

### Post by eltiti55555 on 2014-11-02
> **bab1 said:**
> Not going to happen.  No* sort of*, no *maybes*.  Ownership is not the same thing as permissions.  ACL's are for permissions only.  Permissions are for read (r) write (w) and execute (x).

Well, as it turns out, if you are the owner of a folder, and have full permissions on it; you can use setfacl to give permissions to any user in the system to files and folder within that folder you own.

Makes sense?

---

### Post by bab1 on 2014-11-02
> **eltiti55555 said:**
> Well, as it turns out, if you are the owner of a folder, and have full permissions on it; you can use setfacl to give permissions to any user in the system to files and folder within that folder you own.

Makes sense?

Not really.  I was responding to your question of>  *[COLOR="#0000FF"]...is there a way in which I could just **make an user a file owner** (using setfacl)...?[/COLOR]*
The answer is:   ACL's are for permissions only.   So if you are talking about changing ownership; ACL's won't allow you to change ownership.

You have asked a couple of questions multiple times.  The facts still stand.  The owner of the file can change the **group ownership** and set *group permissions* on the file.  The owner of the file can't change the ownership of the file, but can change the permissions of the owner.  But to what end?  

If we are only talking about the ownership permissions; what would the advantage be for the owner to set ACL's for themselves?  The owner should be able to read and write to the file by default.

---

