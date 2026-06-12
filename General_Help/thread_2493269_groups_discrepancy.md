---
title: "groups discrepancy"
date: 2023-12-09
forum: General Help
---

### Post by pkrawczun on 2023-12-09
Hello there. Here is some output from my Ubuntu terminal

```
user123@user123:~$ groups
user123 adm cdrom sudo dip plugdev lpadmin lxd sambashare nordvpn
user123@user123:~$ groups user123
user123 : user123 qwerty2
user123@user123:~$ whoami
user123

```

user 123 is the sole user on this computer. Shouldn't both group commands produce the same output? It is the same user.

---

### Post by MAFoElffen on 2023-12-09
??? Yes it should.

On mine:
```

mafoelffen@Mikes-ThinkPad-T520:~$ groups
mafoelffen adm cdrom sudo dip plugdev kvm render lpadmin whoopsie lxd sambashare libvirt

mafoelffen@Mikes-ThinkPad-T520:~$ groups mafoelffen
mafoelffen : mafoelffen adm cdrom sudo dip plugdev kvm render lpadmin whoopsie lxd sambashare libvirt

```
It is wrong, and I have never seen that before.

I am at a loss why yours is different. I don't even have any ideas on that. Dang. Sorry.

---

### Post by TheFu on 2023-12-09
I trust the 'id' command to report the truth.  In theory, all of these should be using the same system call getpwent() to find that information.

```
DESCRIPTION
       The getpwent() function returns a pointer to a structure containing the
       broken-out fields of a record from the password database (e.g., the lo&#8208;
       cal  password  file  /etc/passwd, NIS, and LDAP).  The first time getp&#8208;
       went() is called, it returns the first entry;  thereafter,  it  returns
       successive entries.
```


There is also, getgrouplist()
```
DESCRIPTION
       The  getgrouplist() function scans the group database (see group(5)) to
       obtain the list of groups that user belongs  to.   Up  to  *ngroups  of
       these groups are returned in the array groups.
...
RETURN VALUE
       If the number of groups of which user is a member is less than or equal
       to *ngroups, then the value *ngroups is returned.

       If  the  user  is  a member of more than *ngroups groups, then getgrou&#8208;
       plist() returns -1.  In this case, the value returned in  *ngroups  can
       be used to resize the buffer passed to a further call getgrouplist().

```

There is an argument that limits the number of groups returned, to prevent some nasty possible bugs.  NFS is known to only support 20 groups. Few installations care about this. 

So, the most likely answer is that different programs use different methods to get the list.  I stopped looking for other methods to get the list of groups, but I'd bet there were 2 more C calls that did it slightly different as well.  Adding complications to this are that processes have a "real group" and "effective group". This is beyond the sometimes long list of groups an admin on a typical Linux system may be a member.  I think systemd adds some group memberships dynamically too - that's all we need, right?

---

### Post by pkrawczun on 2023-12-09
After a reboot this problem went away and the *group* command works as it should

```
user123@user123:~$ groups
user123 qwerty2
user123@user123:~$ groups user123
user123 : user123 qwerty2
user123@user123:~$ whoami
user123
```

But I'm not in the *sudo* group anymore and cannot "sudo su". I rebooted again and went to "Advanced Options for Ubuntu" --> "root" and added myself back to the group using

```
usermod -G sudo user123
```.

Group does this now


```
user123@user123:~$ groups
user123 sudo
user123@user123:~$ groups user123
user123 : user123 sudo
user123@user123:~$ whoami
user123
```

So this is what happened. I've been playing with the usermod command earlier today and typed something like this:


```
usermod -G qwerty2 user123
```

I thought this should add user123 to group called qwerty2, which it did, but it also removed me from all the other groups, except for the user123 group. Why did this happen?

---

### Post by pkrawczun on 2023-12-09
OK, I can see now there is a error in the book I'm using. It should be

```
usermod -a -G sudo user123
```

To append. Without the "-a" flag, everything is removed. SOLVED

---

### Post by TheFu on 2023-12-09
> **pkrawczun said:**
> After a reboot this problem went away and the *group* command works as it should

...

I thought this should add user123 to group called qwerty2, which it did, but it also removed me from all the other groups, except for the user123 group. Why did this happen?

I didn't read everything ... busy day with deadlines here.

Systemd broke a number of things related to user and group management. Adding a user to a group always required restarting the shell or running the 'newgrp' command for the change to be seen within that shell only.  See, groups are read at shell/program start - and have always been that way.  Usually, the most complete way to have group membership changes seen, even before systemd, was to logout of the system and login again.  Since the initial login shell - before a GUI runs caches the group membership.  Then all launched programs under that login will see the same groups.

This has always confused non-admin people.

Now, with systemd involved, a full reboot, not just logout and login again, may be required for group membership to be updated.  It is a know bug, which has been unfixed/rejected.

As to the commands you used to modify group membership - some modify the primary group and some modify the non-primary group. It has always been this way - at least the last 30 yrs.  _**Read the manpage carefully for these programs**_ ... or just do like I do on non-NIS+/non-LDAP systems. Edit the /etc/group file directly so there's no confusion for what is actually happening.  Primary group is in the /etc/passwd file. Non-primary groups are in the /etc/group file. Simple, unless you make changes that aren't consistent with the requirements of those 2 files and the "shadow" files.  They aren't complex, but don't screw it up. ;)  Changing/adding groups is usually safe, but people have locked themselves out of systems screwing with the entry in the passwd file.

---

### Post by MAFoElffen on 2023-12-09
There are still some more device and applications groups that you need to re-add yourself back to, to get to where you were:
```

user123@user123:~$ groups
user123 [COLOR=#ff0000]adm cdrom[/COLOR] sudo [COLOR=#ff0000]dip plugdev lpadmin lxd sambashare nordvpn[/COLOR]

```
(From your first post...)

---

