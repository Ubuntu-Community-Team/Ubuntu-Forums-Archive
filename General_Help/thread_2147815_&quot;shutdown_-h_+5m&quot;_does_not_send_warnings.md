---
title: "&quot;shutdown -h +5m&quot; does not send warnings to the console."
date: 2013-05-23
forum: General Help
---

### Post by bchurchill on 2013-05-23
When I execute

```
shutdown -h +5
```

I expect it to send a warning message to every console I'm logged in to every minute (or something like that).  For me this isn't working quite right... I don't get any messages printed to any of my local consoles.  However, I do get messages sent to ssh sessions.  Even if I 'ssh localhost' I will get warnings on that screen.

Could this be because I'm using login shells?  To make RVM work (for ruby development), bash is always invoked with --login.  Could this be part of the problem?  Is there a workaround that doesn't compromise RVM?

---

### Post by tgalati4 on 2013-05-23
While in RVM, run the *who* command to see who is logged in.  Only those logged into that environment would be notified.  To send a notification outside of the virtual machine, you would have to run* wall* or* notify-send* or both.

---

### Post by bchurchill on 2013-05-23
To be precise, shutdown is being invoked by a cron-job which is not being run from the RVM environment.  To avoid confusion, RVM isn't a virtual machine, it's just an environment for controlling ruby packages, so it's not like this should be a problem.  I actually don't think RVM itself is an issue at all (I could be wrong), but maybe there's something to do with login shells?  For all I know it might have nothing to do with either of them.  Any suggestions for how to get a better diagnosis?

Also running 'write _username_' has the same problem.

---

### Post by tgalati4 on 2013-05-23
Can you substitute the *wall* command for *shutdown* and see if that invokes correctly?

```
wall simple_message.txt
```

---

