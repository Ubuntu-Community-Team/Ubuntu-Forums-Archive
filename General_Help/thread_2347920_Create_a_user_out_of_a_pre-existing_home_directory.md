---
title: "Create a user out of a pre-existing /home directory"
date: 2016-12-29
forum: General Help
---

### Post by marmaladejackson on 2016-12-29
Hi All!

My motherboard failed and I had to rebuild a new system :(.  I had Ubuntu installed on a small SSD and a 2TB drive as /home.  I formatted the SSD and did a fresh install and re-mounted the 2TB as /home.  During the install, I created a new admin user, */home/brian2*.  My pre-existing directory with all my stuff, */home/brian* is untouched.  I want to create a user *(brian)* and have it log into the */home/brian* directory.  Is that possible?  I did some trial and error with test users, but it won't complete the logon.

[ATTACH=CONFIG]272903[/ATTACH]


Thanks!

---

### Post by Keith_Helms on 2016-12-30
The problem is that brian is not really brian.  Sound confusing?  When you create users and groups in Linux, they are kept in 2 tables - /etc/passwd and /etc/group and each text name is assigned a unique number - the uid and gid.  Those numbers are what are used in all directory and file entries and not the actual name.  So, brian on your old system may have been assigned uid 1000 and brian2 was assigned uid 1000 on your new system.  That means that brian2 probably appears to own all the files under /home/brian.

What you'll need to do is create user brian on the new system and then change the ownership of everything from /home/brian on down to that new user with the following command:
```
sudo chown -R brian:brian /home/brian
```

When adding the new user, you'll probably see warnings similar to these:
```
Adding user `another' ...
Adding new group `another' (1001) ...
Adding new user `another' (1001) with group `another' ...
The home directory `/home/another' already exists.  Not copying from `/etc/skel'.
adduser: Warning: The home directory `/home/another' does not belong to the user you are currently creating.
```

Note: If you want a user added after the system was installed to work just like the "admin" user, you will probably have to give that user the ability to use sudo by adding it to the sudo group with the following command.  Obviously you'll have to sign in as brian2 to do this.
```
sudo usermod -aG sudo brian
```

---

### Post by marmaladejackson on 2016-12-30
Thanks Keith!  That did it for me!  /home/brian is back in business!

---

