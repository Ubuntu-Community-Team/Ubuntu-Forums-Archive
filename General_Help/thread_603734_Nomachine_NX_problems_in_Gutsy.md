---
title: "Nomachine NX problems in Gutsy"
date: 2007-11-05
forum: General Help
---

### Post by volksman on 2007-11-05
Hey all!

Hopefully someone here can help with this issue:

I run Nomachines Free NX server to remotely connect to my machine.  This ran fine under Feisty regardless of whether I had Beryl running or not (ran beryl for a time under Feisty).  I recently upgraded to Gutsy and again had no problems with the install or connections when I ran with the open source fglrx driver, with desktop effects running (IE Compiz).

This weekend I decided to try the new ATI driver and loaded it up.  Got Compiz working using the AIGLX and Composite extensions.

Today I tried to remotely log into my machine and I kept seeing my desktop for a second then it would disappear and I would get a "network" error.  Did  some digging into the NX logs and saw something about composite and thought this may help.  Long story short I had to disable the "Render" feature in NX to be able to get a desktop up and running remotely.

So I have it working but it looks like crap and is quite a bit slower than it should be.

Any ideas on what I can do to make this work?  I'm thinking I need to revert to the OSS ati driver but I don't particularily want to do that.

---

### Post by volksman on 2007-11-05
Hrm...I just reverted my system back to the OSS driver but I still get the same problem.  This sucks.  NX was such a slick way to access the machine remotely and I used it daily.

The speed has definitely been helped by reverting the driver but the display still looks like crap with the Render extension disabled.

---

### Post by volksman on 2007-11-05
Ok...So this is definately a problem with NoMachine NX and Compiz (updates that were released on Friday or Saturday seem to be the culprit as the issue didn't appear before the updates).

Basically all I did was disable compiz and my remote sessions work again without having to disable Rendering.

Before the updates to Compiz I had my machine at home logged into a session with Compiz enabled and remotes worked fine with the same user account.  This is not the case now.

I hope someone from the Compiz or NX teams reads this.  I'm more than willing to send log files and I can easily reproduce the problem.

Please update this thread if you know more info about this issue.  I'd love to be able to leave compiz enabled on the base system and still be able to remote without having to disable Rending.  It looks awful without rendering.

---

### Post by senecaso on 2007-12-04
I am seeing a very similar problem, except that I have no compiz processes running at all.  If I use NX (nomachine) to connect from A to B, everything is fine.  I can open the session and use it as expected.  However, if I connect from B to A, as soon as I see my desktop, I get a "The connection with the remote server was shut down" error.  Along with that message, I get a core file and a bunch of stuff in my ~/.nx/F-C-stuff/clients file.

I think the "kdeinit: Fatal IO error: client killed" is the root of the problem, but I have no idea what the IO error was.

Has anyone else seen this?  Found a way to fix it?

I have attached my clients file in case that helps.

---

