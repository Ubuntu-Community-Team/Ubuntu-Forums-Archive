---
title: "What is eating my CPU cycles?"
date: 2007-07-05
forum: General Help
---

### Post by edantes on 2007-07-05
I am running 7.04 on an older Dell Inspiron (8100/PIII 1MHz/512M).  Current  kernel is 2.6.20-16.

After a reboot, the system works fine for a while.  Then, after a period of heavy CPU use, everything slows to crawl.   Even moving the mouse around becomes CPU intensive, resulting in a long period of 100% use, wIth Firefox as the top resource hog.

I am monitoring the system from a terminal window using  "top".  Firefox and Xorg are using most of the system resources.  This same configuration has worked fine for a couple months and became a problem only in the past week.  

I suspected a hardware problem, but couldn't duplicate the behavior under Windows, nor running Ubuntu off the installation CD.

I have not added any Firefox extensions recently, restarting Firefox doesn't fix the slow down.  A reboot does, but only for a while.

Ideas?  Please!!!

---

### Post by orb9220 on 2007-07-05
More info needed.

1) Does this only happen when firefox is running?
2) What is your video chipset? And did you install the video drivers for it?

Things to try.

1) Determine what has been installed from the last week? Video drivers,jBeryl,compiz,java,flash,etc....

Usualy what I have seen about these issues can be traced back to one of these problems listed above.

Sorry couldn't be more help.

---

### Post by timcredible on 2007-07-05
updatedb runs every day by default.  that's what's taking all your cpu shortly after boot.  move the script to run monthly if you want:

sudo mv /etc/cron.daily/slocate /etc/cron.monthly

---

### Post by edantes on 2007-07-05
> **orb9220 said:**
> 
1) Does this only happen when firefox is running?
Yes, but the slow motion remains after firefox gets killed. I is like it  left something running in the background, but it doesn't show under top.

> **orb9220 said:**
> 
2) What is your video chipset? And did you install the video drivers for it?

Nvidia GeForce 2 GO (It is legacy chipset by now)  with NVIDIA Driver version 1.0-9631.  

Right now I am booted with the older kernel 2.6.20-15 and suprise, it has worked fine for a while.  Later I will give the newer kernel a try disabling this driver.  The puzzling part is that I had been using the new kernel before the problems started.

Thanks for your suggestions.

---

### Post by tigerstripedcat on 2007-07-08
Wild guess.  It might be flash.  Does cpu skyrocket after youtube or something like that?

---

### Post by euler_fan on 2007-07-08
Get and run Htop from (I believe) the Add/Remove programs lists. Otherwise your package manager. It works great.

It's also lightweight, so start it up next time you log on, have it set to sort by CPU and see what is hogging your cycles as things slow down. Please post your findings.

Depending on what it is it might just have not exited cleanly and needs to be manually killed. And it might not always be the same thing At least that's how mine is. ](*,)

Alternatively, also look at whether or not your swap and ram are getting filled and what is doing that. It might be a combination of the two. On mine, Thunderbird eats plenty of my ram as does Firefox with multiple processes. On that note, how much swap to do you have?

---

### Post by edantes on 2007-07-09
Oh well.  I reinstalled Ubuntu 7.04 from scratch and it looks like the slowdowns went away,   I wonder if there was a messed up configuration somewhere.

> **euler_fan said:**
> Get and run Htop from (I believe) the Add/Remove programs lists. Otherwise your package manager. It works great.
I am installing it as we speak,

> **euler_fan said:**
> 
have it set to sort by CPU and see what is hogging your cycles as things slow down. Please post your findings.

After killing Firefox,  top and ps did not show anything, but the system was certainly slow.

> **euler_fan said:**
> 
Alternatively, also look at whether or not your swap and ram are getting filled and what is doing that. It might be a combination of the two. On mine, Thunderbird eats plenty of my ram as does Firefox with multiple processes. On that note, how much swap to do you have?

I have 512M of memory and 1G Swap.   I am not sure of the swap usage at the time of the slowdowns, htop would have been informative then.

> **tigerstripedcat said:**
> Wild guess.  It might be flash.  Does cpu skyrocket after youtube or something like that?
You are right.  But everything was OK two weeks ago and it is back in shape after my reinstall.  Nothing obviously different in the configuration.

---

### Post by euler_fan on 2007-07-09
My only further advice is simply to keep Htop running as you do your normal work and occasionally check it so see what is going on.

You may find all kinds of interesting things. For instance, I've had the evince thumb nailer stick for some reason and hog LOTS of resources, that kind of thing.

Beyond that I must appeal to the others.

EDIT: Have you considered switching to Xubuntu? It is supposed to be lighter on resources than GNOME and may make things run a bit faster for you.

---

### Post by alphanuderek on 2007-07-09
I have the same problem.  Running a Dell XPS2 with 2gb of memory.  It slows down when some pages off of SU come up, so I'm thinking some "web 2.0" stuff.  

I had that written and then it froze again.  From looking at my logs it appears to be something in xml.  It also does it to me in gmail.  If the guru's need something from me let me know because I'd like to help get this resolved.

---

### Post by alphanuderek on 2007-07-09
> **alphanuderek said:**
> I have the same problem.  Running a Dell XPS2 with 2gb of memory.  It slows down when some pages off of SU come up, so I'm thinking some "web 2.0" stuff.  

I had that written and then it froze again.  From looking at my logs it appears to be something in xml.  It also does it to me in gmail.  If the guru's need something from me let me know because I'd like to help get this resolved.

Upon further investigation the culprit seems to be gconf, so it is because of automatic updating.  I'd still like to figure out why it's doing this with out having to do something as drastic as leave GNOME.

---

