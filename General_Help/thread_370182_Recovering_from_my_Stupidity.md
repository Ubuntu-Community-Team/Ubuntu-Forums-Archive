---
title: "Recovering from my Stupidity"
date: 2007-02-25
forum: General Help
---

### Post by farscott on 2007-02-25
I did something really stupid, and I hope someone can help me recover.  I installed ubuntu 6.10 on my Dell Dimension C840 with a dual-boot option for Windows XP Pro.  That part went well, but I did something really stupid.

Since I have other Linux boxes, I try to use a system to manage the root passwords.  I went into the users and groups section, set the password for root, and (here it comes) fiddled with the check boxes for privileges.  Here is my bind.

My user account, scott, can no longer access the system administration tools, and root can no longer use X when logging in.  How do I fix this?  If I can get root to use X when I log in, I think I can return the privilege for scott to access the system.

---

### Post by taurus on 2007-02-25
Boot into recovery mode and post the output of this command from a terminal.

```
id scott
```

Basically, scott needs to belong to groups adm & admin in /etc/group for sudo/gksudo to work.

---

### Post by farscott on 2007-02-25
Here are the result

uid=1000(scott) gid=1000(scott) groups=1000(scott),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner)

---

### Post by taurus on 2007-02-25
You need to add your name, scott, to group admin in /etc/group.  While still in the recovery mode, do

```
nano -B /etc/group
```
When you are done, exit with <Ctrl>x.  Answer the questions with Y and Return.

Now, if you run that "id scott" command again, you should see admin on that list.  If you do, then reboot and see if user scott can run sudo/gksudo again.

```
shutdown -r now
```

---

### Post by farscott on 2007-02-25
Okay, that did it.

One more question.  I would like to return the privileges for root to the default.  Am I correct that all of the boxes for root should be unchecked?    How about the same for scott?  

Thanks for the help.

---

### Post by taurus on 2007-02-25
You don't have to add root to any group because root can do anything on your machine.  Therefore, try not to log in as root if you don't know what you are doing.  Instead, use the sudo/gksudo command instead.  And as for user scott, that you have right now is fine.  No need to edit anything or add scott to anymore groups.

---

### Post by farscott on 2007-02-25
I really should have read more before I fiddled with those settings.  I did not understand the meaning of the terms, and I missed the implications of the sudo command.

Thanks for getting me back on the path.

---

