---
title: "Samba Active Directory Permissions on Share Folder"
date: 2019-11-08
forum: General Help
---

### Post by erudes91 on 2019-11-08
Hey everyone, I have I think a simple question about Samba integration with AD permissions:

We have a special folder on this Ubuntu server in which we store music for our users

The idea is that only two users can have write permissions on the share folder, all the others should have read only.

This is my smb.con file and also my Windows settings:

[https://imgur.com/a/0Io4SqP](https://imgur.com/a/0Io4SqP)

[https://imgur.com/a/ecBNJpj](https://imgur.com/a/ecBNJpj)

So what changes do I need to perform in order for only our 2 users to be able to copy files on the folder and all domain users should have read only?

---

### Post by TheFu on 2019-11-08
Can't see images, but if you want different permissions via samba, the easy solution is to make 2 different "shares" - 1 for the group of users with read-only and 1 for the group with read-write.

---

### Post by erudes91 on 2019-11-08
Images can be seen by clicking on the links, simple as that.

Unfortunately your suggestions is not valid on my scenario, we need to set this up on the same shared folder, and I am pretty sure that this can be accomplished by modifying something on the config files (represented on images)

---

### Post by uRock on 2019-11-08
> **erudes91 said:**
> Images can be seen by clicking on the links, simple as that.

Unfortunately your suggestions is not valid on my scenario, we need to set this up on the same shared folder, and I am pretty sure that this can be accomplished by modifying something on the config files (represented on images)

If you'd like users to view your images, then it'd be best to use the paperclip icon in the Advanced Reply window to upload them. Some users have strict policies against visiting 3rd party sites to view images and some users don't use browsers that will load images at all. You can also post the output of the command in the first image using code tags.

---

### Post by erudes91 on 2019-11-08
Thanks for the tip, here are the images!

[ATTACH=CONFIG]284355[/ATTACH][ATTACH=CONFIG]284354[/ATTACH]

---

### Post by TheFu on 2019-11-09
We don't use AD here.  Searching these forums found this : 
[https://ubuntuforums.org/showthread.php?t=874982](https://ubuntuforums.org/showthread.php?t=874982)

```
valid users=@WRITE_LIST @READ_LIST
write list=@WRITE_LIST
read list=@READ_LIST
public=No
browseable=No

```
The smb.conf manpage says:```

       read list (S)

           This is a list of users that are given read-only access to a
           service. If the connecting user is in this list then they will not
           be given write access, no matter what the read only option is set
           to. The list can include group names using the syntax described in
           the invalid users parameter.

           Default: read list =

           Example: read list = mary, @students
...
       write list (S)

           This is a list of users that are given read-write access to a
           service. If the connecting user is in this list then they will be
           given write access, no matter what the read only option is set to.
           The list can include group names using the @group syntax.

           Note that if a user is in both the read list and the write list
           then they will be given write access.

           Default: write list =

           Example: write list = admin, root, @staff
```
The group of users with write need to have the native Unix group permissions of rwx and g+s on all the directories.  Those commands are at the "share level."  I haven't tested any of this.

Perhaps it will work?  I should have posted images of the settings, so copy/paste wasn't possible, sorry.

---

