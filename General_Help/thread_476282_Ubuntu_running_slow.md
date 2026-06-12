---
title: "Ubuntu running slow"
date: 2007-06-17
forum: General Help
---

### Post by penguinchrissy on 2007-06-17
My Ubuntu is running slow in general. An example; 

I go to delete a file out of /home/me/folder what happens is the windows blacks out (freezes) for a min or two then comes back and the file is then gone.

Another example

I go Places>Computer. Nothing happens or so it seems. I try another 5 times. Nothing. Get bored waiting for them to open so open up Swiftfox. BOOM. I have six of the Computer windows open up along with it. Same goes for /home and other folders.

Another one

When I Crtl+Alt+Backspace to restart GNOME I lose some icons in my panel liken whats mounted.

Also after Crtl+Alt+Backspace or an actual restart (reboot or shutdown) it takes forever for my desktop to load. The only panel I have is white for about 2mins and the splash screen is up for 2 to 3 mins. After about that time everything seems to load. 

I have tried a couple of speed up ubuntu forums and other suggestions but they haven't worked. I'm not sure if its a natiulas (the file system sorry for bad spelling) or something else. Even if it is that I'm not sure how to fix it. 

I'll try anything and post back on if it worked or not.

I'm running fesity 7.04 with beryl
Pentium M 3.02
Nvidia GeForce Go 6800 with latest drivers

Thanks for any help!!!

---

### Post by handydan918 on 2007-06-17
How much ram do you have? When your system displays this behavior, are you running multiple processes? Have you tried NOT running Beryl to see if the problem still exists?
If you have an adequate amount of ram installed, try running memtest at bootup time to see if you have some bad memory.

---

### Post by astrix on 2007-06-17
same problem... all was well and then one fine day everything is slo and persists to be so

---

### Post by penguinchrissy on 2007-06-18
I have a gig of ram and I ran memtest and it passed everything. I also tried turning off all start up process that doesn't do anything. 

When I reboot after turing off all the process its the same thing the splash screen stay there then the toolbar comes up white then everything loads

After ctrl+alt+backspace it loads the toolbar but the background it blue and if you try and click on anything the toolbar freezes. After a while everything loads.

I've been run into a problem in amarok.  It stays on the splash screen for about 30 seconds then nothing happens. After about 2 mins a space is formed in the notification area. Then after another couple of mights it will open but blacked and locked. Then if luck it will open. This is recent only a couple of nights ago it was working. I tried reinstalling but thats been it.

---

### Post by penguinchrissy on 2007-06-18
might using gnome-commander instead of nautilus fix the problem?

I found the problem I was running a session called Xclient script instead of GNOME why I don't know but it the problem is now fixed.

---

### Post by Brian96 on 2007-06-19
> **penguinchrissy said:**
> might using gnome-commander instead of nautilus fix the problem?

I found the problem I was running a session called Xclient script instead of GNOME why I don't know but it the problem is now fixed.

Can someone explain (or link to a thread/page that explains) what the Xclient script session is about? --Thanks.

---

