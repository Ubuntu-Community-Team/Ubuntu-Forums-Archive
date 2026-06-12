---
title: "Need assistance with permissions/groups"
date: 2013-06-04
forum: General Help
---

### Post by Scrumps on 2013-06-04
I am trying to fix the way my permissions are acting. Right now, when a file is automatically added to the folder, it is added under the premise

torrent:users

With the following permissions
drwxrwx--- 

I need to find a way to change this so that it ends up adding it as

torrent:torrents

while keeping the same r/w permissions.

How would I go about doing this? 

My getfacl for the folder is listed like so:
getfacl: Removing leading '/' from absolute path names
# file: srv/torrent
# owner: torrent
# group: torrents
user::rwx
group::rwx
other::r-x


and the umask for the user should be set to 0007 so it should keep the r/w permissions that I like, but, I just can't figure out this group thing and how to keep it so that it is always torrent:torrents rather than torrent:user.

---

### Post by pqwoerituytrueiwoq on 2013-06-04
i found this the other day, it should be useful for you
[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

---

### Post by MidnightGrey on 2013-06-04
Hi Scrumps,

(Dont quote me on this, but) I believe the issue is that the username 'torrent' belongs to the usergroup 'users'.
Therefor any files created by the username 'torrent' will automatically be assigned to that usergroup. The only way around it would be to move the user 'Torrent' to another usergroup.

May I ask why you want to change the usergroup?

---

### Post by Scrumps on 2013-06-05
> **pqwoerituytrueiwoq said:**
> i found this the other day, it should be useful for you
[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

Unfortunately, this is where I get confused, I understand the uses of the last three digits, but not so much on the first. I also am completely confused with symbolic mode after reading that.

> **MidnightGrey said:**
> Hi Scrumps,

(Dont quote me on this, but) I believe the issue is that the username 'torrent' belongs to the usergroup 'users'.
Therefor any files created by the username 'torrent' will automatically be assigned to that usergroup. The only way around it would be to move the user 'Torrent' to another usergroup.

May I ask why you want to change the usergroup?

The way I have my groups set up is such that the user torrent is a part of the users group, and that the group torrents has only those users that I want to have access to anything. 

Since this is accessing a folder that will have a pretty large range of files and folders. But I don't want anyone or anything that isn't in the group torrents to have access to it.

---

### Post by steeldriver on 2013-06-05
If 'torrent' is the only user that writes to the dir, then I think it should be sufficient to make sure that the group 'torrents' is user 'torrent's *primary* group (aka 'initial login group') (it can belong to the 'users' group as well, but users should not be the primary group). You can change the group memberships with usermod -g (for the primary group) and usermod -aG (to append any secondary groups)

Alternatively you could use the directory's setgid bit so that *any* files getting written to it inherit its group (i.e. 'torrents') - similar to how I do /usr/local/src in the following example (only here my shared group is called 'staff'):

```

$ ls -ld /usr/local/src
drwxrw[COLOR=#0000ff]**s**[/COLOR]r-x 3 root [COLOR=#0000ff]**staff**[/COLOR] 4096 Jan 18 14:37 /usr/local/src

$ groups
steeldriver staff

$ touch /usr/local/src/test

$ ls -l /usr/local/src/test
-rw-rw-r-- 1 steeldriver [COLOR=#0000ff]**staff**[/COLOR] 0 Jun  5 17:56 /usr/local/src/test

```

---

### Post by Scrumps on 2013-06-05
The setgid bit also applies to permissions as well right? So wouldn't it pick up the r-x permissions for global others? 

I had that set up at one point, and I think I broke a lot of things with the setup, which is why I reverted it, I can definitely try it again though.

---

### Post by steeldriver on 2013-06-05
AFAIK you can set whatever permissions you like for 'other' (I just happened to chose r-x for my application) - the setgid is applied recursively only in the sense that any subdirectories created by members of your 'torrents' group will also be 'setgid torrents' so that files placed in them will also get group 'torrents' - the *permissions *will be determined by the creator's umask. The only gotcha I'm aware of is that the torrents group members' umasks should be such that any subdirs they create are group-writeable.

But tbh it sounds like for your particular application just setting the primary group of the user 'torrent' to 'torrents' instead of 'users' will get you where you want to be.

---

