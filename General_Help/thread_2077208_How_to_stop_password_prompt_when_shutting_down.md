---
title: "How to stop password prompt when shutting down"
date: 2012-10-28
forum: General Help
---

### Post by Red Squirrel on 2012-10-28
Every time I want to restart or shut down, I get a password prompt.  I can understand if it was a server, but this is just a workstation.  I have a dual boot with win7 for gaming so I'm rebooting often, and this can get quite annoying. 

It only seems to do it when F@H is running, because it's run off a network share as a different user.  That user is universal to my whole network, it just makes life easier when it comes with file permissions for that share.  So I don't want to change the user. 

So how do I get rid of that password prompt without touching F@H?

I'm using Xubuntu 11.10.  Thanks in advance!

---

### Post by Red Squirrel on 2012-10-29
Bump, anyone?  This must be a common issue.   Thanks.

---

### Post by pqwoerituytrueiwoq on 2012-10-29
only time you should get a password prompt is if another user is login in, unless you are using poweroff or halt commands

---

### Post by Red Squirrel on 2012-10-29
I think the fah process running as another user is what is counting as another user logged in.  Can't I disable this prompt anyway?  I don't want to change that user, it's universal throughout my network.

---

### Post by pqwoerituytrueiwoq on 2012-10-30
try changing the user id number to anything below 1000

---

### Post by Red Squirrel on 2013-03-07
Ended up finding a solution, thought I'd post it for future reference in case someone else has this issue:

[http://www.ubuntugeek.com/how-can-you-make-shutdown-not-require-admin-password.html](http://www.ubuntugeek.com/how-can-you-make-shutdown-not-require-admin-password.html)

Method 1 is what I did.   This is SO much better.

---

