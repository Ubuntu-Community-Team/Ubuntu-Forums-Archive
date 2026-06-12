---
title: "Managing users"
date: 2020-04-07
forum: General Help
---

### Post by xcfstarflight1 on 2020-04-07
Hi! 
I need to get some updated information to complete a couple of administrative tasks.
1. I go to control center and see my users there. Now i have been messing around some with users and groups that I downloaded from an older post :/
I want to make 1 regular user group for 3 users to be in that can use sudo command and also a shared folder. One fully administrator account.

2. When doing so I want to set up a shared folder between them.

Can someone explain to me how to do this either GUI or xterm but GUI preferred.
Thank you kindly.

---

### Post by TheFu on 2020-04-07
I&#8217;ve never trusted guis for user admin stuff.

When i teach user admin classes, i usually just ask questions to force the student to look up the answers for themselves.  Nobody will remember all the details, which is why we have manpages.

Users and groups for home setups are stored in 4 text files.  passwd, group, shadow and gshadow.  There are all sorts of different commands to modify those files, but start by reviewing the format, fields, layout of each.  They are really simple, line-based records.  Each has a manpage in section 5 of the manpages.  Open 2 terminals.  in one, more/less/cat the actual file.  in hte other, use the manpage for that file.

Once you figure out the connection between the group and passwd files, come back.

Sure, i can list all the commands, but without understanding those files, the underlying stuff in the files won't be as concrete.

Users that can use sudo without restrictions ARE administrators. There's no difference.  All permissions are controlled by group membership.  There&#8217;s nothing else.  No hidden names, groups, directories.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) has a chapter about users, groups, etc.  That's all you need.

Most people need a little help to setup directories that multiple users can share and have read-write access.  I&#8217;ve posted step-by-step instructions here a few times.  it comes down to groups and some seldom used permissions. Search for "working together" w/ chgrp and chmod.

None of these things have changed too much the last 30 yrs.

---

### Post by TheFu on 2020-04-08
```
           $ sudo gpasswd -M  user1,user2,user3  ourgroup
           $ mkdir -p /tmp/Workspace
           $ chmod g=rwxs Workspace
           $ ls -l Workspace
              drwxrws---   owner    group    Workspace/ 
           $ chgrp ourgroup Workspace
           $ ls -l Workspace
              drwxrws---   owner    ourgroup    Workspace/
```

The "s", w, x  in the group permissions matters.
The parent directory permissions control who can create files and subdirs.

---

