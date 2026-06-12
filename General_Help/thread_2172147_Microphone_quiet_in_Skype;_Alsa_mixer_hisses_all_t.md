---
title: "Microphone quiet in Skype; Alsa mixer hisses all the time"
date: 2013-09-03
forum: General Help
---

### Post by Andy3142 on 2013-09-03
Since I re-installed Lubuntu (up to date version) on my Samsung N220 netbook recently, the  microphone volume on Skye is very, very low. In a test call I can hardly  hear my own voice. This is true whether or not I set Skype to "let  Skype control mixer." The speaker volume is OK, I can hear the other person fine, but they can't hear me at all.

All sound devices inside Skype are set to "default".  The  Skype drop-down offers 10 or 12 microphone options, all different names for the one and only onboard mic, far too many to test them all. 

So, I tried to install a mixer. I tried pavucontrol and xfce4-mixer. These do not run at all, they fail on startup.

Alsamixer  appears to install OK. Two of the mic settings were set to zero and I  corrected this, but still no sound in Skype, if anything it is worse.  And, there is now a constant hiss from the speaker, apparently due to  the mic having a constant "presence". So, several questions:

(1) How do I get control of the microphone volume in Skype?

(2) What is the best mixer to use?

(3) If alsamixer is the best mixer, how do I stop the background hiss?

Many thanks

Andy

---

### Post by nativehound on 2013-09-03
The hiss is usually too much mic boost. Have you turned up the capture setting via [F4] or [F5] in alsamixer?
Also recheck the all the settings in alsamixer [MM] means mute. 

gl

---

### Post by Andy3142 on 2013-09-13
Thank your for this reply - the problem fixed itself!  I'm not sure how, the hiss is indeed the boost. But why the Skype came back I have no idea.  I'd thought I'd explored everything I could in Alsamixer before posting, maybe there was something I hit on later, or maybe it was to do with re-booting the system after installing Alsamixer, which I hadn't done at post time.  On of life's mysteries.

Cheers

Andy

---

