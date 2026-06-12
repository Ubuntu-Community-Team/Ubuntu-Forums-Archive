---
title: "Problem with Rosegarden"
date: 2007-01-26
forum: General Help
---

### Post by Scooter7 on 2007-01-26
Hey, I just downloaded and installed Rosegarden, and as soon as I started it up I got this message:

[IMG]http://i49.photobucket.com/albums/f281/Scooter7/Random%20Image%20Storage/Screenshot-1.png[/IMG]

Now, normally I'd go to the Rosegarden people for help, but since the message told me to contact my distributer, I decided to post here.

Any suggestions?

---

### Post by Unknowndeepness on 2007-01-26
How about "Try lmms instead"? (:

---

### Post by Magnes on 2007-01-26
1. You can ignore that message.
2. [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67568](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67568) - read this and if you find some information more about it report to this bug
3. I believe you will need to ignore the problem or use some other kerne or wait for Ubuntu 7.04l.

---

### Post by Scooter7 on 2007-01-26
Alright, thanks for your help, guys. :) 

I'll wait for 7.04, and try it then - until then, I'll check out LMMS.

---

### Post by tonymoloney on 2007-11-15
I'm resurrecting this thread because I've updated to 7.10 and I get exactly the same messages.
I've had a look at lmms, but it doesn't give me the functions that I'm looking for.
Tony

---

### Post by edm1 on 2007-11-15
You are getting this message because the default ubuntu kernel does not have low-latency audio input support. You should still be able to use rosegarden to some extent however if you are trying to record through a midi input try installing ubuntu studio which is included in the gusty repositories.

---

