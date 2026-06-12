---
title: "URGENT PLEASE HELP!: Recover root directory file permissions"
date: 2007-02-20
forum: General Help
---

### Post by ruanza on 2007-02-20
Accidentally did a chmod -R 755 / !!!!

Anybody got any idea how to restore the permissions from console?

Any help would be appreciated.

Thanks
R

---

### Post by louis_nichols on 2007-02-20
well... I don't see a very big problem there. 755 is the default permission for most files on the system anyways, afaik.

I don't think there is a way to revert permissions to the old ones, like an undo button. If anything, you can search the web for default permissions for the files, but that would take an awful amount of time. The best way to do this I think would be to observe if you get errors because of wrong file permissions and treat those when needed.

---

### Post by ruanza on 2007-02-20
Thanks for the response, but the problem I now have is that sshd and mysqld won't start even after apt-get --reinstall install ssh

It just says can't start.

Which means I can't log in remotely.

Can't one reinstall the base package remotely? I can execute root commands via webmin still.

R

---

### Post by louis_nichols on 2007-02-20
Some executables and coniguration files do require different file permissions for security reasons.

I think you need to set the executables for sshd and mysqld to 640.

---

### Post by lkagan on 2007-02-20
It seems like a tool for restoring file permissions would be a great thing.  Mac OS X has this ability on it's CD.  I just did a little snooping around dpkg and I think I can write a script that will restore all the permissions.  I'll spend about an hour on it and then hand off whatever I come up with.  Hopefully I can get something working.  Expect another post from me soon.

Larry Kagan

---

### Post by lkagan on 2007-02-20
Hang tight, just  a bit more to do.

---

### Post by lkagan on 2007-02-20
Well, I didn't get done but here's what I have so far.  I'm not an everyday BASH scripter so there's a few things I don't know how to do.  The problem is that I can't separate the lines that show the file details correctly.  I'm sure someone with a little more BASH experience or a little more time can figure this one out.  I'll try to hit it again when I get a bit more time.

Larry Kagan

---

### Post by ruanza on 2007-02-22
Hi and thanks again for the replies,

I just thought I should give an update on what I did eventually to solve the problem.

It seems I either pressed Ctrl-C fast enough so that not all the files' rights were changed or apache did not mind the 755 chmod - because it was still running fine. So, I repaired the server remotely by mounting the backups via webmin, and untarred everything (overwriting all files on the live server with their correct versions).

Immediately ssh started working again, after which a reboot was necessary to sort out postfix.

Everything running normal again now. But if webmin wasn't installed....

R

---

### Post by jvisaac on 2008-05-23
i made a similar mistake but a little more severe.  i ran sudo chmod -r 777 /
now i can't run any sudo commands, change permissions, i can't even eject my cd because of permission issues. please help

---

