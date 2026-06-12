---
title: "File system is not freed when files are deleted"
date: 2007-07-24
forum: General Help
---

### Post by KjetilK on 2007-07-24
I've got a weird problem. My /var/log ran full (supposedly, I didn't check really, but it got 100%), so I deleted a few old log files, and mv'ed some out.

I keep /var/log on a partition by itself, so that it won't take the system down when it goes full.

df says this:
/dev/mapper/all-log    1038336   1036824      1512 100% /var/log
while 
root@pooh:/var/log> du -sk .
126864  .

that's a pretty big difference... And I think du is right, I certainly can't see where the rest is...

It's an XFS files system, this is the fstab line:

/dev/mapper/all-log /var/log        xfs     defaults        0       2

And under there, there is a 3ware RAID controller, and two physical Seagate discs (IIRC).

My first thought was that it is the journal that somehow isn't cleared out and is taking up so much space, but I really don't know how this would work...

---

### Post by tsav87 on 2007-07-24
Did you check the trash bin icon?

haha, couldn't resist :D

I'm a n00b, so sorry for not being able to help.

---

### Post by xarmian on 2007-07-25
This is just a suggestion.. It looks like maybe you removed files which were still being accessed (such as /var/log/messages).. while rebooting should fix it, without rebooting you can try:

sudo /etc/init.d/sysklogd restart

If a process is accessing a file that has been removed, the space will not be freed until there are no processes accessing that file any longer.. restarting the log daemon kills the process that's accessing your log files and restarts it..

-Dave

---

