---
title: "Moving Files"
date: 2021-09-16
forum: General Help
---

### Post by eipapp on 2021-09-16
Currently running Ubuntu 20.04 and I want to move a file that I downloaded onto my desktop but now want to move that file to my documents folder but it won't let me.
Is there a workaround ?

Thanks,
Bruce

---

### Post by psychohermit on 2021-09-16
Open a terminal in your desktop folder.  sudo mv filename ../Documents

--glenn

---

### Post by TheFu on 2021-09-16
> **psychohermit said:**
> Open a terminal in your desktop folder.  sudo mv filename ../Documents

--glenn

A typo?
[LIST]
[*]sudo isn't needed. sudo abuse is how people get into permission problems.  If there is a permissions issue, fix that first.  In general, running **sudo chown -R $USER:$USER ~/** is safe. If you've screwed with groups at all, this may break some things, but on a typical Ubuntu desktop, it is completely safe - even for people like me who do odd things around permissions, groups, and working with multiple, different userids.
[*]**mv ./filename ~/Documents/** is the proper command, assuming your terminal PWD is the same a where the "filename" is located.  That could be in ~/Desktop/ or it could be in some other place. Depends on the DE being used and how ingrained the use of XDG stuff is.  Type 'pwd' to see the Present Working Directory - sometimes also called CWD - Current Working Directory.  
[*]Usually, when a new terminal is started, the pwd will be ~/ <---- that's the same as $HOME - the HOME directory of the current userid.  
[/LIST]

Always remember, Linux is multi-user. Files have owners, groups, and only the owner of a file can modify permissions.

**$HOME == ~/ == ~userid/**
Any of those are the same almost anywhere you type them.  Obviously, replace "userid" with your username on the system.  For me, that would be **~thefu/  == ~/ == $HOME**

Usually, in a default setup, ~thefu == /home/thefu as well, but that isn't mandatory.  The first examples work regardless of the actual directory name.  The information is pulled from the password database, where ever that come from.  It could be /etc/passwd file or some LDAP server or from MS-Active Directory or from an x.500 directory server or NIS or NIS+ services.  It just depends.
There are lots of ways to check this value.
```
$ echo $HOME
[COLOR="#00FF00"]/export/home/thefu[/COLOR]
```
or
```
$ getent passwd thefu
thefu:x:1000:1000:TheFu:[COLOR="#00FF00"]/export/home/thefu[/COLOR]:/bin/bash
```
The directory could point almost anywhere and it doesn't need to have the username in it. That is just convention so humans don't get confused.
These are all the same for the username "thefu":
```
cd $HOME
cd ~
cd ~thefu
```

---

