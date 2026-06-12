---
title: "Server does not exist error"
date: 2013-01-07
forum: General Help
---

### Post by Jarec01 on 2013-01-07
Hi all

hopefully someone can help as the Internet has failed to solve my problem.

A little background. We have 2 main servers, live (livehost2) and backup (livehost1), plus a Dev box that holds Subversion. The live servers are both running lucid (10.04.1 LTS). We run a backup, restart, rebuild on both the main servers every day. 

Up until Saturday our live was running fine, it restarted and rebuilt on Friday morning as usual. Nothing was changed on the system on Friday, no automatic updates are enabled and we had no system issues.

On Saturday morning the server failed to build. Giving the following error in the log: 

> Server 'livehost2' does not exist. Please specify one of: 
devhost
livehost1
Alternatively, you can create a new profile:

We've swapped over to the backup box and everything works as expected. I've checked the build scripts and they are identical and have not been changed. The logs all show no changes and they both use the same Subversion and Maven repositories. We've compared .profile files between the servers and they are the same. Even tried restarting the box in case there is an issue but can't see one.

I can supply other information as required.

Unfortunately we don't have a server expert in house, I do what I can but I'm primarily a developer.

Any help or ideas of where to look greatly appreciated.

---

### Post by Jarec01 on 2013-01-08
Problem solved

Script was using a variable, that was dynamically created using a dynamically created variable in another script file, that was using variables in yet other script files. Of course none of it is documented, so I only found it by sheer luck.

Unfortunately the system was written by a developer that has now left and took all the knowledge with him. Just worried what else is out there to find. :(

---

