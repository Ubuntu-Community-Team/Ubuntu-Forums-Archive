---
title: "Problems scheduling a command with 'at'"
date: 2007-10-30
forum: General Help
---

### Post by turbotron on 2007-10-30
Hey everyone.

I'm running Feisty, and haven't fiddled with the installation much. But today I tried to use the "at" command to set up a reminder. When I try to put anything in there though, i get something like the following:

```

mike@dell:~$ at "now +1 minute"
warning: commands will be executed using /bin/sh
at> jps > ~/test.log           
at> <EOT>
Cannot give away file: Operation not permitted

```

I also tried running the previous with root privileges, but got the same result. I suspected that it might have something to do with permissions in /var/spool/cron. My permissions in there are set to:

```

mike@dell:~$ ls -alD /var/spool/cron/
  total 5
  drwxr-xr-x 5 bin  bin     1024 2007-06-21 10:10 .
  drwxr-xr-x 6 root root    1024 2007-08-01 20:06 ..
  drwxrwx--T 2 bin  bin     1024 2007-10-30 16:12 atjobs
  drwxrwx--T 2 bin  bin     1024 2007-06-21 10:10 atspool
  drwx-wx--T 2 root crontab 1024 2007-06-21 10:10 crontabs

```

I'm not sure exactly what else to look for in the permissions though - I saw elsewhere people had the owner set to daemon, but chown-ing the files to daemon still did not fix anything, so i changed it back. I've also found some posts via google about this problem occurring when the spools are mounted from NFS filesystems. That's not the case for me though; it's all a local filesystem, so I don't know if that issue really applies here.
Any idea where I should go from here to figure out what's wrong with it?

Thanks in advance!

---

### Post by dcstar on 2007-10-31
> **turbotron said:**
> Hey everyone.

I'm running Feisty, and haven't fiddled with the installation much. But today I tried to use the "at" command to set up a reminder. When I try to put anything in there though, i get something like the following:

```

mike@dell:~$ at "now +1 minute"
warning: commands will be executed using /bin/sh
at> jps > ~/test.log           
at> <EOT>
Cannot give away file: Operation not permitted

```
............
Any idea where I should go from here to figure out what's wrong with it?

Thanks in advance!

Do not assume that where you run things in a terminal will work with CRON or AT - they are run in their own environments.

Put absolute file paths in for everything - especially any output.

---

### Post by turbotron on 2007-10-31
Good point, but it looks like the issue doesn't depend on the commands themselves. Anything, even a simple echo "hello world" results in the same thing. In fact, it even happens when I don't put any commands in there at all.

---

### Post by Cracauer on 2007-11-01
Has nothing to do with what the original poster is doing, this is broken in the OS as updated on my machine.

$ echo foo | at now + 1 min
warning: commands will be executed using /bin/sh
Cannot give away file: Operation not permitted

A trace shows that this is an actual EPERM.
fchmod(5, 0700)                         = -1 EPERM (Operation not permitted)

So the first bug is that the stupid at(1) command doesn't display errno or errstr.

The file descriptor 5 in this case is a copy of 4, which was 
open on /var/spool/cron/atjobs/a0000f012fa2ae

What seems to happen is that at changes userid to increase security, having opened the file while being root, but having switched away from root credentials to uid 2 (daemon) before doing the fchmod.

/var/spool/cron/atjobs/ is owned by "daemon", so far so good, but the file created in there was created as root. Since it was created as root, doing the fchmod as daemon doesn't work.

Somebody committed a broken at command here.

---

### Post by Cracauer on 2007-11-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/launchpad-report-tool/+bug/138743](https://bugs.launchpad.net/launchpad-report-tool/+bug/138743) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Also note a bug has been filed.

[https://bugs.launchpad.net/launchpad-report-tool/+bug/138743](https://bugs.launchpad.net/launchpad-report-tool/+bug/138743)

I don't have an account there, so if somebody could reference this thread over there that would be most welcome.

---

