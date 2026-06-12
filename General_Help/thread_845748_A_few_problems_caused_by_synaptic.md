---
title: "A few problems caused by synaptic?"
date: 2008-06-30
forum: General Help
---

### Post by ferdose on 2008-06-30
Hello

After installing a few packages through synaptic (the ones I can recall included GLib and bison), I noticed that any time I tried to run anything from the command line (e.g. pidgin, gedit, or deluge), they would not launch. This was a while ago, so I cannot recall the error messages returned, but they said something like 'cannot find symbol' or similar to that.

I then tried to open them from the Application bar on the desktop (I think that is what it called, it is the ubuntu equivalent of the window's 'Start'). Any program I tried to run would not run, but the ones which where already running worked perfectly fine. 

After all this, I restarted my computer this way:
$ shutdown now

When the system loaded, the login screen would not load. However, using the full text terminal, I could login. I could not use lynx, for viewing files or accessing the web. iwconfig returns that I am connected to the network, but all pings return 'Network is unreachable'. But I could run the game angband. I tried fsck, and it returned clean.

I am using Gutsy and am on a Vaio laptop. I have been using linux for about 10 months now. Nothing in my file system is backed up(anymore) considering my external hard drive stopped functioning a few days ago, but I am not concerned with that right now :]

Any help would be appreciated, though I am sorry my post is so vague.

---

### Post by soccerboy on 2008-06-30
> **ferdose said:**
> Hello

After installing a few packages through synaptic (the ones I can recall included GLib and bison), I noticed that any time I tried to run anything from the command line (e.g. pidgin, gedit, or deluge), they would not launch. This was a while ago, so I cannot recall the error messages returned, but they said something like 'cannot find symbol' or similar to that.

I then tried to open them from the Application bar on the desktop (I think that is what it called, it is the ubuntu equivalent of the window's 'Start'). Any program I tried to run would not run, but the ones which where already running worked perfectly fine. 

After all this, I restarted my computer this way:
$ shutdown now

When the system loaded, the login screen would not load. However, using the full text terminal, I could login. I could not use lynx, for viewing files or accessing the web. iwconfig returns that I am connected to the network, but all pings return 'Network is unreachable'. But I could run the game angband. I tried fsck, and it returned clean.

I am using Gutsy and am on a Vaio laptop. I have been using linux for about 10 months now. Nothing in my file system is backed up(anymore) considering my external hard drive stopped functioning a few days ago, but I am not concerned with that right now :]

Any help would be appreciated, though I am sorry my post is so vague.

Can you post your path environment variable?

---

### Post by ferdose on 2008-06-30
'printenv PATH' returns this:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

