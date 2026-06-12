---
title: "User upstart jobs: Ubuntu 12.04"
date: 2014-07-18
forum: General Help
---

### Post by DEMLS on 2014-07-18
I am attempting to set up some upstart jobs that will be run by a user. Specifically, a job that will run a browser and monitor it in case it is killed (accidentally or intentionally), then respawn it. My first attempt at this was in 14.04 and it worked perfectly -- job set in ~/.config/upstart/job.conf and it ran no issues.

However, I've been tasked with getting this set up on a pre-existing 12.04 box for the same purpose. When I attempt to run it, I get the usual errors of 'rejected send message'.

Note that this **cannot** run via sudo or su. This is in an extremely locked-down environment, and while I know sudo is quite safe, this box will be open to physical attack by a lot of actors and thus the main user on this system should have NO admin privileges of any kind.

I've attempted to modify the /etc/dbus-1/system.d/Upstart.conf file with no success. Does anyone have a working config or some ideas to present to me?

---

### Post by DEMLS on 2014-07-21
No suggestions? This is about to have me write off 12.04 completely. Without this being successful, this project cannot move forward.

---

