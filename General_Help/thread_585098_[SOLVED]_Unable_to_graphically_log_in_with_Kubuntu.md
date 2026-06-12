---
title: "[SOLVED] Unable to graphically log in with Kubuntu 7.10"
date: 2007-10-21
forum: General Help
---

### Post by WebDrake on 2007-10-21
Hello all,

I've been using Kubuntu 7.10 since beta.  Just today I've found myself unable to log in except via a console window.  If I type username and password into KDM, it appears to start to load before the screen turns on and off a few times and then returns me to the KDM login screen.

I'm baffled by this as I was able to log in without trouble last night and have not installed/updated any software since then.

Can anyone advise on what could be wrong and how to get Kubuntu loading again?

Many thanks,

     -- Joe

*EDIT:* My system is a Lenovo ThinkPad R61.  I'm also having trouble with the more recent kernels---2.6.22-13 and -14 boot only rarely (they hang with COMRESET errors) so I have to use 2.6.22-12 to guarantee a boot.  I don't believe this can be the problem, though, for the reasons cited above---I have not installed or upgraded anything since successfully logging on last night.

---

### Post by WebDrake on 2007-10-21
Hmm!  I did not believe this could be the (known) issue of login failure when the disk is full.  Shows what I know; it turns out that the ~/.strigi directory was eating up almost 6GB for reasons I do not understand, presumably something to do with the strigidaemon going nuts all the time.

---

