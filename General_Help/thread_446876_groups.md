---
title: "groups"
date: 2007-05-17
forum: General Help
---

### Post by Thingymebob on 2007-05-17
How come if enter  'id' in a terminal I'm a member of a load of groups that don't exist in System>Administration>Users and Groups

---

### Post by Thingymebob on 2007-05-18
Perhaps i wasn't that clear,
here is what I get if i enter 'id' in a the terminal:
```

will@ubuntu:~$ id
uid=1000(will) gid=1000(will) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin),1000(will),1002(lfs),1003(shared),1004(partition)

```

This is whats listed in System>Administration>Users and Groups
with gid in brackets
```

root(0)
users(100)
dhcp(101)
syslog(102)
klog(103)
ssl-cert(104)
crontab(105)
ssh(106)
messagebus(107)
avahi(108)
lpadmin(109)
haldaemon(110)
scanner(111)
slocate(112)
gdm(113)
thentheusers(>1000)

```

As you can see my id shows me as a member of groups
4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev)

It appears nothing below gid 100 is shown in the graphical groups manager, why not? does this not make this tool a little redundant or is there a sensible reason for this?

---

### Post by rsay on 2007-05-20
I've been wondering about this recently as well. There used to be a "Show all users and groups" button in users-admin that disappeared when I moved to Feisty. I have now had to edit the /etc/group file by hand a few times since I couldn't do what I wanted through the gui.

---

