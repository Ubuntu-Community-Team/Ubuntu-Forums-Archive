---
title: "ionice will not run as a nonprivilaged user."
date: 2007-07-11
forum: General Help
---

### Post by syssyphus on 2007-07-11
I am trying to use ionice, but I get the following error when I run it as a normal, non-root user:

$ ionice -c3 touch  test
ioprio_set: Operation not permitted

so this works if I run the following:

$ sudo ionice -c3 touch  test
ll 
...
-rw-r--r-- 1 root        root             0 2007-07-11 10:26 test
...

I would like to run ionice as a normal user, not as root... any ideas?

thanks.

---

### Post by syssyphus on 2007-07-11
ok, I found some info finally... this is kind of lame, so hopefully a solution is found so that a normal user can run a program at an idle i/o priority.

[https://bugzilla.novell.com/show_bug.cgi?id=147944](https://bugzilla.novell.com/show_bug.cgi?id=147944)

from the link above: 
"
Let me fill in the explanation here as well...

In general, idle io should only be used on resources that are not globally
interesting as you can run into an idle io process holding a resource that
someone else needs, but the idle process wont get to do io while someone else
is performing io. That means the idle io process can postpone a higher priority
process indefinitely, if you keep the disk busy. This is why idle io was made
root only, as it needs to be used carefully to avoid a malicious user blocking
access to eg /etc/passwd.

So the cron worry is that a regular user could peturb eg updatedb to lock out
an important file. I don't think it's a real worry, as the hold time would be
short anyways.
"

---

### Post by syssyphus on 2007-07-11
more info:

[http://www.stupids.org/?p=25](http://www.stupids.org/?p=25)

this article refers to an "io timeslice" not sure how that can be altered... ionice -n maybe?

---

### Post by syssyphus on 2007-07-11
ok, so here is what he was referring to:

a regular user can run the following, which will run the process in the "best effort" scheduling class, (the default).

The -n7 option defines "how big a time slice a given process will receive on each scheduling window."

so.... -n0 would be the default, or largest time slice, -n7 would be the lowest.

so to make a long story short, if you want to de-prioritize a process the best you can do as a normal user is probably something like this:

nice ionice -c2 -n7 "command..."

---

