---
title: "Group permissions problem"
date: 2008-03-30
forum: General Help
---

### Post by torer1 on 2008-03-30
I do have a problem that is driving me nuts. To summarize:


[LIST]
[*]I do have a directory with permission set to 1775 and owner set to torer1:users.
[*]Logging on as user "torer1" works as expected. Full read and write permissions.
[*]Logging on as user mia (who is a member of group "users") always gives read access.
[*]Logging on through a tty terminal or using a PuTTY terminal gives write access.
[*]... but accessing the folder using either Nautilus, the gnome Terminal or any other program running under gnome (i.e. amarok) is not permitted. In Nautilus, the icon indicates the directory being write protected (a lock symbol on the folder).
[/LIST]

Some more details:
[LIST]
[*]The directory [music] is a nfs share mounted as /home/mia/music/
[*] The above problem only occurs in the destination computer - i.e. the nfs client.
[*]The users group is defined having the same gid and the same members in both the source and destination computer.
[*]Setting permissions to 1777 will give full read/write access to the directory.
[*]Accessing the folder in the source computer (nfs server) with the same credentials is not a problem.
[/LIST]

---

### Post by nick_h on 2008-03-30
Have you tried 0775 instead of 1775?

---

### Post by torer1 on 2008-03-30
> **nick_h said:**
> Have you tried 0775 instead of 1775?

Yes, I am at my wits end. I have tried 0775 with the same owner:group, and I have tried creating a new group just in case something was messed up with the existing users group. Nothing works out.

What I cannot understand is why there is a difference accessing - trying to write - in the directory from a TTY login, compared from the gnome terminal login.

---

### Post by nick_h on 2008-03-30
Have you tried running the *whoami* or *id* commands to see if your permissions differ in the different environments?

---

### Post by torer1 on 2008-03-30
I just did so.

The *whoami* returns identical results - "mia", corresponding to the logged in user. 

The result of the *id* query just might be interesting - although I am not able to judge ...

Well, the output running id from the TTY gives:

```

uid=1001(mia) gid=1001(mia) groups=4(adm),20(dialout),21(fax),24(cdrom),
25(floppy),26(tape),29(audio),30(dip),37(operator),39(irc),44(video),46(plugdev),
100(users),104(scanner),106(fuse),110(admin),140(music),1001(mia)

```

... but the output in the gnome terminal is:

```

uid=1001(mia) gid=1001(mia) groups=4(adm),20(dialout),21(fax),24(cdrom),24(cdrom),24(cdrom),
25(floppy),25(floppy),25(floppy),26(tape),29(audio),29(audio),29(audio),
30(dip),30(dip),30(dip),37(operator),39(irc),44(video),44(video),44(video),
46(plugdev),46(plugdev),46(plugdev),100(users),100(users),100(users),
104(scanner),106(fuse),110(admin),140(music),1001(mia)

```

I also get a simular result with *groups* from gnome terminal. I don't know if having some of the groups in triplicate signals something important or not, but it does make me suspicious ...

---

### Post by pranab on 2008-03-31
I am having the same problem. Let us say I create a new group (and a user) called data, then I edit the /etc/group file and add a user to this group like so:
 data:x:1002:user1

Now I create a dir (/home/mydata) with 770 permission and user and group as 'data'. But user1 cannot cd to the this dir. 

Issuing id comman logged in as user1 also shows some strange behavior:
Issuing just 'id' returns every group except the new 'data' group.
Issuing 'id user1' returns all the groups for user1 including the new one.

Seems like a restart or re-login may propagate the changes. But this is a new feature/bug for me since I have never encountered the need to restart the system for changing group membership. 

Is there a command that will update the info across all users and groups?

---

### Post by pranab on 2008-03-31
I have no idea how that emoticon got into my last post.

---

### Post by nick_h on 2008-03-31
> I don't know if having some of the groups in triplicate signals something important or not, but it does make me suspicious ...
I get the same output from the *id* command from the TTY and Gnome terminal.  The groups in triplicate does look odd.

What version of Ubuntu are you using?

In Hardy, there is a bug [#178059](https://bugs.launchpad.net/ubuntu/+source/coreutils/+bug/178059) which is not the same but may be related.

---

