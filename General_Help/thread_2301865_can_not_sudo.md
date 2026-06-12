---
title: "can not sudo"
date: 2015-11-05
forum: General Help
---

### Post by meowork2000 on 2015-11-05
I can not do anything on my machine that requires me to use sudo. I can log, in but I can not be a super user. My account is the only user account on the machine. When I try, I get this message.


no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
mike is not in the sudoers file. This incident will be reported.


I set it up a while back and all has worked fine. It is a basic lamp system. The last few times I tried to send an email to a gmail account it would error. So I tried to update but can not.

any help would be great.

thanks,

mike

---

### Post by bab1 on 2015-11-06
> **meowork2000 said:**
> I can not do anything on my machine that requires me to use sudo. I can log, in but I can not be a super user. My account is the only user account on the machine. When I try, I get this message.


no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
mike is not in the sudoers file. This incident will be reported.


I set it up a while back and all has worked fine. It is a basic lamp system. The last few times I tried to send an email to a gmail account it would error. So I tried to update but can not.

any help would be great.

thanks,

mike

I believe this is a Samba libpam-smbpass problem.  Do you have Samba installed?  At this point since you have no backup user that is a sudoer, you will have to use a LiveCD to boot into and repair the system.  The problem is with Samba and PAM syncing the user password with the Samba password.  See [**here**]("http://askubuntu.com/questions/477002/loadparm-c4864-leaking-memory") for more info.  Here is the [**entire google search**]("https://www.google.com/search?client=ubuntu&channel=fs&q=no+talloc+stackframe+at+..%2Fsource3%2Fparam%2Floadparm.c%3A4864%2C+leaking+memory&ie=utf-8&oe=utf-8").

I have ever had t repair the system for this problem but I have helped others.  I usually have at least 2 user accounts that are sudoers on every host as a back door for just this type of problem.

---

