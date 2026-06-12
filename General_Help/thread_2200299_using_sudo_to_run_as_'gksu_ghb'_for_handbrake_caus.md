---
title: "using sudo to run as 'gksu ghb' for handbrake cause cant read write files"
date: 2014-01-18
forum: General Help
---

### Post by sdowney717 on 2014-01-18
I have to run as 'gksu ghb' for handbrake cause cant read write files on another partition.
It is a permissions problem.
So how can this be fixed to let handbrake do this without using sudo?

At least it is working with sudo, otherwise I would have to a lot of huge file copying back to home and then back again to the other partition.

---

### Post by TheFu on 2014-01-18
How is the other drive connected?
How is the other partition mounted?
What file system does it use?
What are the permissions?

Using sudo for any GUI program is asking for permission problems. Setting files will be created with root as the owner, so that will be something to be corrected later beyond fixing the access to the source files.

File permissions are central to UNIX/Linux security. There are lots of good tutorials on the web and youtube videos that do a good job explaining permissions too. If you can, take 30 minutes and work through a tutorial - don't just read or watch. Create a temporary directory and try out things to get an understanding.

---

