---
title: "terrible sound in dapper"
date: 2006-07-18
forum: General Help
---

### Post by orpheusblotto on 2006-07-18
hello all. 
i am having severe problems with sound applications. the first and most annoying thing is that dapper will only play one sound app. at a time; for example, if i am playing a song then no system sounds will play, and if i am using any program that has sound i can't play any songs.

another, posibly unrelated issue is that flash player sound is not working correctly either.

i'd be willing to bet this is a simple problem, but i am new and don't know where to begin. 

any ideas are greatly appreciated.

thanx

---

### Post by skale on 2006-07-18
Same problem here. It's very annoying to have to turn off the music player and restart firefox every time I have to hear something.

---

### Post by quedigg on 2006-07-20
The same here !!

---

### Post by foolsh on 2006-07-21
i agree but even breezy and hoary were like that, why cant the sounds be threaded somehow and mixed at output?

---

### Post by skymt on 2006-07-21
First, the fix. Go to System > Preferences > Sound, and (really!) uncheck Enable software sound mixing (ESD). This will disable system sounds (the various "desktop noises") but it's necessary.

Next, the explanation. Linux sound is a mess right now. There are several different sound systems, and they usually conflict. The most popular is ALSA. It has hardware mixing, so if your sound card is supported well enough, you'll be able to have sound from several ALSA-enabled programs at once. 

Another one is OSS. It was what came before ALSA. It conflicts with everything else. Flash Player uses it. Therefore, you can't use Flash Player if anything else tries to use sound. This will be fixed when Adobe releases Flash Player 9 for Linux, which will also be when Apple sells DRM-free music on iTunes, and Duke Nukem Forever is released.

ESD is the GNOME default sound solution. It also conflicts with things. Plus, it's a daemon, so it's always running. It seems like (from observation) OSS applications can't run alongside ESD, and ALSA ones don't run as well.

There's also ARTS, but since you're not using KDE, it doesn't matter.

There are several projects that aim to solve the Linux sound problem. The most likely winner is jackd. Of course, all our software will need to be changed to use it, once it's out of beta. Flash Player will probably start using it at version 19.

---

### Post by Avian00 on 2006-07-24
Am I the only one who didn't have any success with that "fix?"  First of all, it didn't even fix the problem.  Secondly, I don't see how that can be considered a fix.  I have Dapper installed on both my laptop and my desktop.  My laptop does not have this problem.  If it works on one computer but not on another, why would disabling ESD make any difference?

Does anybody have a better solution?

---

