---
title: "Deleting and adding user (edgy server)"
date: 2006-12-15
forum: General Help
---

### Post by jboehm on 2006-12-15
Hi,

I've got a user that was created via a Mythtv install that appears to be mal formed.  I has a login and password and I can login to that user but its not showing up in the gdmsetup user pull down windows.  And it is not executing these configs and scripts on login

/usr/share/xsessions/mythtv.desktop
/usr/local/bin/mythtv.sh

It also appears to not have a shell set up correctly. Things like file completion are not working.

Is there a way to fix this?  How do I, from the command line, delete this user and recreate it?

Thanks,
Jon

---

### Post by superm1 on 2006-12-15
> **jboehm said:**
> Hi,

I've got a user that was created via a Mythtv install that appears to be mal formed.  I has a login and password and I can login to that user but its not showing up in the gdmsetup user pull down windows.  And it is not executing these configs and scripts on login

/usr/share/xsessions/mythtv.desktop
/usr/local/bin/mythtv.sh

It also appears to not have a shell set up correctly. Things like file completion are not working.

Is there a way to fix this?  How do I, from the command line, delete this user and recreate it?

Thanks,
Jon

The user doesn't show up because the uid is less than 1000.

The default shells aren't set up either because this user is intended only for launching mythfrontend or mythbackend and not much else really.  If you want to set up bash to be your shell, you will need to modify /etc/passwd and update the shell for that mythtv user to be /bin/bash.

To login to that session, you will have to choose the session option on the gdm login screen and choose the mythtv session.

---

