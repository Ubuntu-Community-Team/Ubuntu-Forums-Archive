---
title: "To root or not root? (Question)"
date: 2007-05-18
forum: General Help
---

### Post by loathsome on 2007-05-18
Hi there.

All the problems I'm having with my wifi card([[link]](http://ubuntuforums.org/showthread.php?t=445593)) dissapears when I put myself in the "root" group.

Why is this bad? It's either that, or living with a buggy notebnook.

Thanks,
loathsome:KS

---

### Post by aysiu on 2007-05-18
It's bad because you've just taken out an extra layer of security *and* you're thinking only of the present. Putting yourself in the *root* group could have worse repercussions down the road and leave you with an even buggier notebook.

It seems like a workaround to me. You should find out the real problem and the real solution.

---

### Post by loathsome on 2007-05-18
What's the main things I should to be concerned about when putting myself in the root group? If I can't solve the problem, I'll just do it - In my eyes, a workaround is better than an unsolved problem.

---

### Post by aysiu on 2007-05-18
Well, could you report back if you do experience a problem? I'd be interested to see if any problems do crop up.

---

### Post by darkjedi664 on 2007-05-18
Now I may be new to Linux/Ubuntu, but if you're confident with computers (as I am), what would logging in as root hurt?  I understand the "extra layer of security", but why would you want to use a "limited account".  I know I might get flammed for this, but it seems an awful lot like Vista's UAC (which I know sudo came first, only made the comparison as I'm coming from Vista).  I'd rather have full control over everything, then make worry over everything I do.

---

### Post by earobinson on 2007-05-18
sudo can do everything that root can, there is no reason for needing root. + as aysiu said you lose a layer of security.

---

### Post by merlinus on 2007-05-18
Agreed about sudo, but what about folders and files that are owned by root and root group, and others (users) have only ro privileges?

Would it not be a royal pita to have to change the permissions for each one, which would also have to be done as root?

I have found it much easier to add myself to the root group.

-merlin

---

### Post by darkjedi664 on 2007-05-18
I understand that sudo can do everything, but having to do that on every command, then typing in your password every 15 minutes, is just a little tedious.  Now is the extra layer of security just in case you fudge something up?  I'm confident in my computer skills (still learning Linux), but I know enough not to destroy my install with something I shouldn't have done (well...technically I was being a little over-zealous and decided to "upgrade" to Gutsy, and that broke quite a few things).  UAC on Vista is an annoyance and that was quickly gotten rid of.  So I'm thinking the same thing here.

---

### Post by ricrac on 2007-05-18
What are you doing that you need to sudo every 15 minutes?

No standard desktop apps require sudo during normal use. (openoffice, gimp, firefox, xmms, mplayer, k3b, etc.)

Advanced categories that don't require sudo.
audio editing
video editing
hotplugging cameras
external harddrives
burning cd's and dvd's
web site development
compiling
debugging
database administration
3d modeling
CNC milling, lathing and routing
building virtual machines and deploying to physical machines

The only issue with "too much" sudo is during install and configuration, which you should only need to do once per release.  Save your settings to a kickstart file and you won't have to use the installer.  If you learn a merge source control tool and you can easily save your config and re-apply to a new system build.   
What else are you doing that requires sudo?  Just wondering.

---

### Post by darkjedi664 on 2007-05-18
Compiling apps, drivers, etc...Copying files to other folders.  There's lots of things I have to use sudo for.  I'm constantly doing things to my system, and since I'm still new to Linux, it's taking me awhile to do things.  My recent attempt at X11VNC isn't going too well, so it's a guess and test sorta thing.  Same thing with compiling apps, if it doesn't compile correctly, I have to try something different, then try again.  Maybe I'm doing something wrong in the compile process, but as I said, I'm still learning, so if I forget to type sudo before ./configure, I get all kinds of permission denied errors.  I understand what sudo is, and what sudo does, I'm just saying it's annoying.  So to get back what I was asking previously, is the only issue with logging in as root, that you have a bigger chance to screw things up?

---

### Post by freakavoid on 2007-05-18
I just read another post about how some fellow ubuntu user messed up his/her system by trying to delete the empty directories. Imagine using complicated commands like the -exec option of gnu find or parsing arguments with xargs... One can never be sure that nothing will go wrong; e.g. one can accidentally use a wrong directory tree (/ instead of ~ for example) or things might turn out nasty for other not so obvious reasons. So, I don't want to check every command eight times just because typing sudo for the ten minutes I spend a day for administrative purposes seems too much work.

---

### Post by ricrac on 2007-05-19
You don't need root (sudo) to compile apps (or even install and run them)
You only "need" to use sudo for the "make install" step.

When using a shared system for development, no one has root access and we compile X, apache, mysql, our own code, run it, test it, package it up, before anyone ever starts a virtual machine to test using root access.

You should never get "permission denied" from a .configure.  What is the app, that's a bug and should be submitted.  You do not need permissions to configure, compile, or run an app, only to install into system directories (make install). 

Yes you have a bigger chance of screwing up as root.
If you are root, accidentally start a browser as root, and go to the wrong website....say goodnight.
If you are root and create the right file with bad permissions, someone could escalate privileges...say goodnight.

---

