---
title: "Eclipse Problems"
date: 2007-02-01
forum: General Help
---

### Post by BIGtrouble77 on 2007-02-01
I'm running Eclipse 3.2 from the eclipse project site, not the repos.  I'm also running the Sun java jdk 1.5.0.06 from sun.com, not the repos.  Problem is that when I shut down eclipse there's still an eclipse process and an eclipse java process running.  It happens with all my workspaces.  

I have to go in and kill the processes manually.  This seems to be relatively new behavior- I've been using this eclipse install for a long time now.  I just installed RadRails so that may be part of the problem (but I have some non-rails projects that have the same issue).  Anyway, hoping someone might have some ideas I could try out.

(oh, i'm running 64bit Dapper)

Thanks,
-BT

---

### Post by phossal on 2007-02-01
Are you running beryl? That affects the JVM.

Shutting down eclipse, in fact, does not *immediately* kill the threads it may have spawned. I've experienced bizarre problems where shutting down eclipse left me with java processes, similar to what you're describing. It was a result of unfinished rmi transacations to a database server. Bizarre. 

lol Upgrade to Java 6 and get a new eclipse?

---

### Post by BIGtrouble77 on 2007-02-01
> **phossal said:**
> Are you running beryl? That affects the JVM.

Shutting down eclipse, in fact, does not *immediately* kill the threads it may have spawned. I've experienced bizarre problems where shutting down eclipse left me with java processes, similar to what you're describing. It was a result of unfinished rmi transacations to a database server. Bizarre. 

lol Upgrade to Java 6 and get a new eclipse?

Thanks for the response.  No, I'm not running Beryl, XGL or anything like that.  I have to keep my laptop as stable as possible as it's my primary development machine.  I guess now is as good a time to upgrade Eclipse and Java as ever.  At least I'm not the only one having problems like this- I wish there was a way to set eclipse to kill all of its threads on exit.  I just hate messing with a setup that otherwise works really well- I use a bunch of eclipse plugins so I'm sure they'll give me a few headaches when I upgrade.  I read that Java 6 is much faster so it might be worth just trying that out first and see what happens.

Anyway, thanks.

---

