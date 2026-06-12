---
title: "SDL_init failure: window creation error."
date: 2020-01-23
forum: General Help
---

### Post by jrcj38 on 2020-01-23
New here. Don't know where this belongs, if elsewhere I'll be happy to move/repost, just tell me which forum please.

I was running Ubuntu 19.10. I run the second life viewer Firestorm. I had, until a week or so ago, been capable of running 19-20 Firestorms in --multiple mode very comfortably. My system has a geforce GTX 1080ti, 6x2 processors, 64GB RAM, it's good sized as such things go. Running all this and BOINC projects in background, everything used 29.4GB RAM. Nowhere hear maxing anything out. One of the updates a week or so ago broke all this. My system now struggles to get 15 viwers up and running. When I try more viewers I get SDL_init failures. Never happened before. Coincidentally, I also lost all sound on web apps like Youtube.  Ubuntu 19 is still a development/test system. I figured ok go back and try  18.10 so I did, Now running 18.10 with all recent updates. No joy. I have my sound back but that's all.  Still struggles to get up to 15 viewers, didn't before last week. Still getting SDL_init failure errors, didn't last week. AFAIK or have found, this error is from Gnome and is claiming a hardware issue. Please correct me if I'm wrong. I downloaded the Heaven benchmark tool and ran it (with BOINC chugging in the background) for a couples hours with maximum tesselation and everything else I could check. Flawless if running a wee bit warm but nothing beyond the usual. Hardware looks sound.

Something in a recent update would seem to be responsible for my now drastically curtailed capabilities on this system. Has anyone seen this?  Is there a solution? All resources are unlimited for each process. After and upgrade last week my system won't do what it was very happily doing. 

Any help greatly appreciated. Thank you.

---

### Post by coffeecat on 2020-01-23
Welcome to the forum. I've moved this to General Help, where you will be more likely to get help than the near-abandoned backwater of "Ubuntu Application Development" that you found! If subsequent discussion reveals that this is better in another sub-forum, we can move it again for you. 

By the way, Ubuntu 18.10 is well past end of life. Support ended in July 2019, and the repositories were then closed. You shouldn't have been able to get updates. You would be best advised to install a supported release to trouble-shoot your problem, either 19.10 again which is an interim release due to be end of life in July, or the LTS (long term support) 18.04 which has 5 years of support from its release in April 2018.

---

### Post by jrcj38 on 2020-01-26
Sorry for the delay. Have ubuntu 18.04 in. Had to install stuff just to get Firestorm to run but no general updates. To wit:

dpkg --add-architecture i386

apt -y install libidn11:i386 zlib1g:i386
apt -y install libstdc++6:i386 libcurl4-gnutls-dev:i386 
apt -y install libuuid1:i386

apt -y install libgtk2.0-0 gconf2

Took a while to remember I had to torn off the noveau driver.

I can get 16 of my previous 19 firestorms running. Graphics response is acceptable. Terminal response is abysmal. Wasn't before. Can't run anything else either, could before. Not seeing any SDL_INIT failures. The remaining three try to start. Again, this use to consistently work and I was going to try 20 of these things because there sure seemed to be plenty of resources left.

When I started this time I didn't have my BOINC projects running. I've seen schedulers doing really odd things under load, like be more effecient than under light load. I install BOINC and ran my 2 projects. Didn't help. Didn't seem to hurt either.

Again, this use to work under 19.10 until that upgrade a week and a half ago.

Still looking for suggestions. In the mean time I'm going to run general updates and see if it kills my Youtube sound again.

---

### Post by jrcj38 on 2020-02-03
More info. I notice that when I run as few as 15 of the second life viewer Firestorm (use to be able to run 19 or 20) response time for other processes is abysmal. For the very first time ever on Ubuntu (18.04 now) a job not responding window popped up for my terminal session. I've never seen this before on Ubuntu although I recognized it. At this point even getting a click event to elicit a response took a minute in some cases. I took 5-8 seconds to get the job not responding window to respond to a mouse-over event. This never happened before that update about two weeks ago. II don't know what that update did but it wasn't at all good for event response or scheduling.

---

### Post by CelticWarrior on 2020-02-03
18.10 is one year out of support. Please upgrade to a supported release ASAP.

---

### Post by jrcj38 on 2020-02-03
20200203 15:40, none of the resent updates  have corrected the problem.

---

### Post by jrcj38 on 2020-02-03
20200203 16:04 Confused. Ubuntu site says 18.04 support ends April 2023 as reported earlier by coffeecat.

---

### Post by CelticWarrior on 2020-02-03
18.04 yes.

> I figured ok go back and try  18.10 so I did, Now running 18.10
18.10 is out of support.

---

### Post by jrcj38 on 2020-02-16
Back to 18.04. I noticed the nVidia drivers were installed but noveau wasn't blacklisted, fixed that. There was a barely noticeable improvement. I  can run 18 firestorm second life viewers.Now I can clear them without having to reboot.  However, it takes 30-60 seconds for a mouse click to respond, 15-30 seconds for a mouse over to be recognized and terminal  window response per character typed is still glacially slow. Again, before those updates in the last two weeks on January I had no trouble with this at all.

---

