---
title: "Permissions Gone Wild"
date: 2007-01-20
forum: General Help
---

### Post by cssutto on 2007-01-20
I am using Dapper 6.06 on a ThinkPad.

New installation from Ubuntu CD.

My email set up is Mutt, Nullmailer.

Nullmailer has folders in /var/spool/nullmailer:
queue
trigger
tmp

I can set these folders with chmod 755 and the email works fine.

I can shut the machine down and reboot it and the trigger and tmp folders will be set to 600.

With the permissions at 600, SMTP can not get an email file out of queue and send it.  It can not use trigger or tmp.  So I have to go to the command line and set them back to 755.

Also, not all the time, but frequently, I will compose and email and tell mutt to send it.

Nothing happens.

I then look at the message, which is stored in queue until SMT cycles, and it has been stored with a permission of 600 and SMTP can not read it, so it does not get sent.

I have looked everywhere and I can not find out what is changing these permissions.

Is there some way I can set them and lock them so no exec file can change them?

This is driving me nuts because I can never tell when an email is going and when it is not.

I must constantly look at the nullmailer/queue folder's contents to see whether they have been changed to 600.

Help will be appreciated.

I forgot.  umask is 022.

CSSJR

---

### Post by mssever on 2007-01-21
Here's a kludge you can try: In /etc/rc.local, insert the commands to chmod those directories. Then, every time you boot, the permissions will be set correctly.

Also, if you're using the ext2/3 filesystem, have a look at the chattr man page. There might be something helpful in there.

---

### Post by cssutto on 2007-01-21
Thanks.

That worked.

But I would like to find out how and why it was happending.

I am still going to have the trouble with outgoing emails because they are made 600 after the boot, during the sending process.

CSSJR

---

### Post by mssever on 2007-01-21
The only thing I can think of is to hunt through the mailer's configuration. I'm not familiar with nullmailer, but certainly something is mis-configured somewhere. The kludge I gave you shouldn't be necessary.

---

