---
title: "Pan won't run tasks"
date: 2007-04-24
forum: General Help
---

### Post by riksweeney on 2007-04-24
Hi,

I upgraded to Feisty from a fresh install and reinstalled Pan. It prompted me to enter the server information, which I did, but none of the tasks actually run. If I check the tasks window, it says

Getting group list from "server-name"
Queued

Is there a way I can get it to actually run? Quitting and restarting has no effect. I've tried typing a garbage server name in to see if it fails, but this also queues up and never moves.

This is Pan 0.120

Any suggestions would be appreciated.

Thanks

Richard

---

### Post by zorkerz on 2007-04-25
Hi there I have just installed pan and am playing around with it. I must be honest i have never used a news reader before. I put in a bogus server as well and one that i thought might be a real one. The both stay queued all the time.

There might be other newsreaders you can use or have you chosen pan for a specific reason. 
You could visit the pan website if you don't get better help here. File a bug yourself or email one of the project members. Im sure they would be helpful and able to tell you what is going on.
good luck

---

### Post by dcstar on 2007-04-25
The Feisty Pan in the repositories is still the bug-filled Beta version, go to the Pan site and download the .deb of the older Released version (0.14.2.91).

When you install this older version, you then have to lock it using the Synaptic Package-Lock Version function.

When the proper version of Pan is finally released and put into the Ubuntu repositories, then remove the lock.

I gave up on the Feisty Pan after a week of frustration.

---

### Post by Compyx on 2007-04-25
Strange, I've been using Pan 1.20 from the repositories for quite some time now, and I've never had any problems with it, and I use it many times a day.

As for the tasks being queued, check File -> Work Online and make sure it's enabled.

---

### Post by zorkerz on 2007-04-25
Interesting you are not having problems. I guss that is a good sign for future stability of others. Although i do believe its version 0.120 not 1.2 because there does not seem to be a non beta release yet.
cheers

---

### Post by Compyx on 2007-04-25
You're right, it's version 0.120 ("Plate of Shrimp"). I remember compiling and running an older version (0.117) on Gentoo, that wasn't exactly stable either. Too bad, Pan is a really nice usenet-reader. Maybe I'll try to compile the latest version and see how stable that one is (with conservative CFLAGS. just to be sure).

---

### Post by cutterjohn on 2007-04-27
Yep, the new version of Pan in Feisty ATM is AWFUL.

I do appreciate that the Pan developers are trying to actually move Pan forward, but a bunch of features have gone missing for the moment, and I do NOT like the fact that there is NO way, apparently, to tell Pan to ONLY use this server or that server only ATM.  i.e. all you get is that it hits ALL of the servers as primary or just as fallbacks as they are set when added.

Pan 0.120 is just not ready for use, unless you are looking for that particular "feature".

Oh, if a task just stays queued check and make sure that you are in online mode and then if you are, check the log as if it cannot contact the server it will just remain queued IIRC.

---

