---
title: "sshd auto logout"
date: 2006-12-13
forum: General Help
---

### Post by bobmct on 2006-12-13
:confused: 
Our shop runs a number of Ubuntu 6.06.1 servers.  They all real quite well so kudos to the ubuntu team!!!

One inconvenience we have is when staff ssh's into a remote server to do something then forgets about it and moves on to another task.  Often they leave the ssh session open.  Could be for hours, days, even weeks!

We have been searching for a mechanism whereas if the ssh user has NO activity for a defined period of time the session will be automatically disconnected and/or logged out.

There are a number of similar questions AND responses on these forums and usenet but in actuality, none of them work!  All that came from these forums were deemed invalid by this versions sshd program which refused to start.  Others allowed starting but were ignored.

So, someone, somewhere, especially those in "the know" on these forums, MUST have a solution for this seemingly common dilemma.

Anyone?

TIA:-k

---

### Post by pandu.rs on 2006-12-13
Please refer man sshd_config

The following options seems to be helpful for you.
ClientAliveInterval
ClientAliveCountMax
TCPKeepAlive

---

### Post by bobmct on 2006-12-13
:( Thanks, Pandu.rs

I already tried those and restarted ssh with /etc/init.d/ssh restart then ssh'd into the server and logged on.  I then let the shell prompt sit in a window for a couple of hours and nothing happened.  I used 30 minutes for my interval and my max count was 1 so it should have triggered.  But it didn't.

Any other ideas???

---

