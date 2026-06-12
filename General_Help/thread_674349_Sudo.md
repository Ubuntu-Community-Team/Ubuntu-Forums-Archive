---
title: "Sudo"
date: 2008-01-21
forum: General Help
---

### Post by mattyboy11 on 2008-01-21
I have added user to me computer and i want to install some thing in that user but i gave it no admin rights. Is there a way of loging in as he other user to install some thing. 

usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

this what happens when i type this

louise@matt:~$ sudo -u matthew|#1000usage:
>
>
>install wine
usage: sudo -K | -L | -V | -h | -k | -l | -v
install: missing destination file operand after `wine'
Try `install --help' for more information.

can you help

---

### Post by heindsight on 2008-01-21
Your user needs to be listed in /etc/sudoers to be able to use sudo.

try using:
```
su -l username
```

EDIT
That sudo command you tried looks a bit strange, so just to clarify:
```

usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }


```
means that the sudo command can be used either with exactly one of the options -K, -L, -V, -h, -k, -l or -v, OR
with options -H, -P, -S or -b (or some combination of these) as well as a -p option (which must be followed by an 
argument specifying what prompt it should give), and a -u option, which must be followed by either a username or 
a numeric user id. This must be followed either by -e followed by a list of file names, or by -i or -s or a command.

---

### Post by aysiu on 2008-01-21
**Point and Click Method**
Go to System > Administrator > Users & Groups

Double-click the new user's name. Click the User Privileges tab. Then make sure all the boxes are checked/ticked.

**Command-line Method**
```
sudo adduser *newusername* admin
```

---

