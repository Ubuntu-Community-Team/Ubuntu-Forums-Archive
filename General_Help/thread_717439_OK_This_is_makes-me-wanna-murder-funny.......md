---
title: "OK This is makes-me-wanna-murder-funny......"
date: 2008-03-07
forum: General Help
---

### Post by jabeez on 2008-03-07
> I've had a MythTV backend up and running for the last few months (the latest one anyway), but outta the blue it started having all kinds of issues, so after quite a bit of fiddlin' around, I figure screw it, backed up all my recordings and go for a fresh install. I also thought I was smart and backed up my xorg.conf, which I finally got working for single 1920x1080 output to my TV, yet after re-installing both MythBuntu and Kubuntu, the best I can do is 720x480, even with the identical xorg.conf that was working @ 1920x1080 before it stopped. So WTF??????? I mean really, if you are forced to go edit a .conf file, at least make it work!!!!!! GRRRRRRR, sorry but yet again Linux is making me want to go break something (besides my working MythTV install)....................anyone have a helpful suggestion or wanna share your own make-you-crazy story??


So this is too inflammatory? Wow, I must be missing something.......

---

### Post by mozetti on 2008-03-07
Starting with Gutsy, Ubuntu included a failsafe mode for X so that an update wouldn't leave you with a blank screen/terminal login. So, if something in your backed up xorg.conf file caused X to fail, it would put you into failsafe mode. I'm not quite sure how you'd tell if you're using the failsafe mode, though. Hopefully it's a start in your troubleshooting.

---

### Post by jabeez on 2008-03-07
thanx for the reply! But at this point there are a few things working against me......The MythBox in question was before Gutsy, but anywho this xorg.conf worked before, and the version was no later than Feisty, so not sure what could've changed since then..................

---

