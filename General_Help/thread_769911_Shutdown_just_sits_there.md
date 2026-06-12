---
title: "Shutdown just sits there"
date: 2008-04-27
forum: General Help
---

### Post by Daniel15 on 2008-04-27
Hey everyone,
 I just upgraded to Ubuntu 8.04 (well, I reinstalled due to several problems I had after upgrading), and shutting down doesn't seem to work properly. I click "Shut Down", it closes all the programs I have open, and then just sits there at a blank desktop. I need to kill X with Ctrl+Alt+Backspace for the shutdown to complete.

Any ideas how to fix this?
Thanks :)

---

### Post by bobdog on 2008-04-27
I am having the same problem.  Running a dell inspiron e1505 with 1.6 duo core, 2 gigs ram and ATI Raedon Mobility 1400.  Kind of bugging me.

---

### Post by Daniel15 on 2008-04-27
Perhaps that's a clue... My system's nearly the same configuration (Dell Insprion 6400, 1.73GHz Core Duo, 2 GB RAM, ATI X1400). The Dell Inspiron E1505 was known as the 6400 here for some reason.

---

### Post by Onesimus on 2008-04-27
Yep, I have a DELL 6400 and I get a similar problem.

A couple of times it has reported something about the Network Manager.  

As we have similar machines, I am curious to know whether you have had difficulties with suspend and hibernate.  Suspend works and hibernate partially works - the only problem is that it is unable to re-connect to the network with hibernate.

That's why I wonder if the network manager is somehow causing the long delay in shutdown.

---

### Post by speckman on 2008-04-28
I have an old Pentium 4 and have had this problem since quite a while back after updating.  When I choose Shutdown, it takes up to a few minutes (? I've never really timed this) for the menu to come up.  Normally, I just type ```
shutdown -h now
``` in a terminal.

---

### Post by Joeb454 on 2008-04-28
You will need to run that as sudo :) and you can also use -P instead of -h (I've not yet found a difference).

As for sudo I mean like so (this is what I run): ```
sudo shutdown -P now
```

---

