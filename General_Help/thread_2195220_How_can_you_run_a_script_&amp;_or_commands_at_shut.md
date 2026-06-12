---
title: "How can you run a script &amp;/ or commands at shutdown?"
date: 2013-12-22
forum: General Help
---

### Post by sam_baker2 on 2013-12-22
hello,
how can you run a command(s) or a script at shutdown?
The ".bash_logout" doesn't work when you shutdown. I know
I can always first logout, then shutdown, and the logout would run,
but I would forget to do this alot.

There is something here:
[http://unix.stackexchange.com/questions/34963/running-script-before-shutdown-seemingly-not-working](http://unix.stackexchange.com/questions/34963/running-script-before-shutdown-seemingly-not-working)
, but it is beyond me.


using Xubuntu 12.04

---

### Post by ian-weisser on 2013-12-23
A better discussion is at [http://askubuntu.com/questions/78298/how-do-i-configure-upstart-to-run-a-script-on-shutdown-when-the-process-takes-lo](http://askubuntu.com/questions/78298/how-do-i-configure-upstart-to-run-a-script-on-shutdown-when-the-process-takes-lo)
Upstart jobs for shutdown are governed by: [http://upstart.ubuntu.com/cookbook/#id134](http://upstart.ubuntu.com/cookbook/#id134)

I would do it in Upstart. Something like:
```
# Upstart job: /etc/init/my_shutdown_job.conf
description "My shutdown job"

start on runlevel [06]
pre-start script
  /path/to/my/shutdown/script
end script
```
When you tell the system to shutdown (runlevel 0), Upstart will check the list of jobs that need to be started or stopped for that condition before actually executing the instruction. This job tells upstart to run the script before the change is executed.

Caveat: I have done a bunch of Upstart jobs, but have not tested this particular one.

---

### Post by Lars Noodén on 2013-12-23
Wouldn't that be just runlevels 0 and 6?  [Runlevel 5](http://www.debian-administration.org/articles/212) is just another normal mode of operation.

```

start on runlevel [06]

```

---

### Post by ian-weisser on 2013-12-23
Dratted fumbly-fingers. Thanks for pointing it out. Original edited to  [06]

---

### Post by sam_baker2 on 2013-12-24
Thanks guys, that worked.
On my Desktop at logout ( Xubuntu 12.04 ), I have these selections:
"Log Out" "Restart" "Shut Down" "Suspend"
I wish there was another one called "Log Out/Shutdown", so that one
could log out ( and thus have the logout file run ) and shutdown, all
with one mouse click, in case one forgets to logout first and then
shutdown. Then the etc/init folder would not have to be messed with.

---

