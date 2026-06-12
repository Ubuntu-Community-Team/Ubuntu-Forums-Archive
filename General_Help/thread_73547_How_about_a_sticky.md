---
title: "How about a sticky"
date: 2005-10-09
forum: General Help
---

### Post by BLTicklemonster on 2005-10-09
How about a sticky in here that tells us new people the right way to install stuff we download?

A. Is there a specific place we need to put the files we download? (if so, don't say yes and submit new reply. tell us. I've seen people do stuff like that before, you have to wonder if they actually know, or are trying to act like they know. I personally think that 90 percent of the people who make replies like that don't know.)

B. Once a package/file/thing is downloaded, what steps are used? (I'm trying like the dickens to install something I can listen to streaming audio with, and none of them will install.) Do we sudo? Sh? Chmod? Curse? Sacrifice burnt offerings?

C. And so on and so forth...

---

### Post by zigg on 2005-10-09
Being new myself I often find what you say above all to common place in linux based forums, I hope this one will be different :D I think I may have a solution for you too;) 
open up a terminal and type ```
sudo apt-get install xmms
``` that will install xmms which is like winamp. it will play streaming media out of the box ( at least it did for me). I normaly use it to listen to shoutcast streaming stuff with. sometimes firefox won't foward the download to xmms right, if thats the case then just save it to the HD and open it in xmms, it will then proceed to stream :D

I hope this help, Z|gg

---

### Post by Zelut on 2005-10-09
Best solution for the new users is checking out the [www.ubuntuguide.org](www.ubuntuguide.org).  It'll tell you how to get/install programs for all types of stuff.  Just take a look, follow the steps & you should have everything you need in no time!

If you get stuck, just ask

---

### Post by BLTicklemonster on 2005-10-09
[QUOTE=kuyaedz]Best solution for the new users is checking out the [www.ubuntuguide.org](www.ubuntuguide.org).  It'll tell you how to get/install programs for all types of stuff.  Just take a look, follow the steps & you should have everything you need in no time!

If you get stuck, just ask[/QUOTE]

Thanks, but I've been there, and there's no "before you get started, let me beat you with this fish brain and see if it helps" anywhere.

Basics, pure simple every day basics. Since posting this, I've already gotten xmms working and listened to some tunes while getting my surround speakers to actually surround me with sound (something I never got in xp no matter what sound blaster drivers I used), and I learned how to make ctrl+alt+del work like it does in windows, I installed UT, but it still doesn't work right, Got my microphone working, tried several ways of getting my nvidia drivers installed, but nothing worked, and now I'm locked out of the x server at the command prompt. But the tunes were cool. Restarting the machine just brings me back to the command line. So I turned off the box, hooked the hd with xp on it back up, and the hd witn ubuntu is sitting there waiting for me to rescue it. 

Big lmao on me.


But still, some primer would be nice for those of us who were clueless.

Seems like it doesn't matter where you put stuff, but /home/yourname seems a nice place. and if it's a tar baby, shoot, I have no idea. But normally, cd /home/yourname/nameoffolderyoudownloaded and you'll be in the folder with your download and can sudo or chmod or sh or lmnop for all I care, at that point. I think. 

See, it doesn't say that anywhere. I never found a simple 1 2 3 on downloading and installing packages. A thread on such a thing, several actually, yes, but it was all over my head to begin with. Got this far, though, I'm a quick study once I grasp what's going on. Then I totally destroy what I'm doing, lol.

---

### Post by floyd27 on 2005-10-09
when in the command promt start..

dpkg-reconfigure xserver-xorg
that will get you going on ubuntu again..

---

### Post by BLTicklemonster on 2005-11-18
Thanks floyd!

---

