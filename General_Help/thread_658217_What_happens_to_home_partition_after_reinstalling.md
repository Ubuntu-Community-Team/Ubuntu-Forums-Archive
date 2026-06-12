---
title: "What happens to /home partition after reinstalling"
date: 2008-01-04
forum: General Help
---

### Post by vsiege on 2008-01-04
I was wondering...
My setup for **(sda)**
[INDENT]#1 primary 30 F ext3 /
#5 logical 5 F swap swap
#3 primary 465.1 F ext3 /home[/INDENT]
**(sdb)**
[INDENT]#1 primary 500.1 F ext3 /media/second[/INDENT]
If I choose to reinstall the OS (7.10) but NOT reformat the /home partition..
1. If I recreate the default user (lets say userA) will his home folder on /home be over-written or will it automatically change it to something like userA-1?
2. If after installation I recreate another user that was on the old build - what happens to thier preexisting dirtory in /home?
3. If you never recreate any of the old users and groups - what happens to the permissions on the files that were created during the last build? for instance a text file created by userB - but this time around you never create a userB - must you change the permissions with su?

---

### Post by p_quarles on 2008-01-04
During setup, you'll have the option of choosing which partitions to format. Simply choose *not *to format the home partition, and make sure that it *is *mounted as /home.

If you create a user with the same name as your old account, it will automatically use your old home folder.

---

### Post by mojoman on 2008-01-04
> **p_quarles said:**
> During setup, you'll have the option of choosing which partitions to format. Simply choose *not *to format the home partition, and make sure that it *is *mounted as /home.

If you create a user with the same name as your old account, it will automatically use your old home folder.

Under Debian-based distros I think it's a good idea to make sure that the users have the same id # as well (e.g. 1001), just as you would when you share /home between distros.

---

### Post by vsiege on 2008-01-06
OK.

So before an install take down all user and group
1. id's
2. correct spellings of their names

Then make sure i do not format the home drive and mount it as /home.

Since you cannot switch the default user's ID until after installation thats OK to have the discrepancy as long as you fix this right away?

---

### Post by vsiege on 2008-03-01
just this last one and I can say it's solved:
Since you cannot switch the default user's ID until after reinstall, is thats OK to have the discrepancy as long as you fix this right away?

---

### Post by Anduu on 2008-03-01
To make life easier create a new Administrative user that you can get rid of after everything is sorted out.

Be prepared for some fiddling...Last time I reinstalled I created a user with the same name and had some problems.The old user had an id of 1001 so the home dir had permissions for 1001 while the recreated one turned out being 1002.
With some creative chowning and shuffling user id's I got my /home directory associated with the new user.

---

### Post by vsiege on 2008-03-02
Lemme see if I got order down correctly... 
[LIST=1]
[*]as you install create a different Administrative user name for Linux and MySQL
[*]after installation log in and check Users and Groups
[*]now from here do we delete the new Administrator
[*]make sure all users have thier old ID's
[/LIST]
Does the old admin now take over as the new admin?

---

