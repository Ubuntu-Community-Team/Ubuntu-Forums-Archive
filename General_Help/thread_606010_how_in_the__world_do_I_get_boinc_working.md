---
title: "how in the  world do I get boinc working?"
date: 2007-11-07
forum: General Help
---

### Post by boostedtsi on 2007-11-07
as the title says...
I am once again attempting to use linux... and once again ************************.  .

Why the hell can't linux develop a program installer that will install the program and get it working without continuous hassle?

It will not connect to local host is the current issue.

If this is going to take an inordinate amount of work I will simply uninstall linux and go with windows yet again. This not running of simplistic programs is really getting on my nerves.

---

### Post by boostedtsi on 2007-11-07
actually don't even bother.
I am burning a copy of xp as I write this and will then be destroying my worthless linux disks and it will never be installed on any of my systems again.

---

### Post by Tyke91 on 2007-11-07
Go to applications > Add/Remove programs > boinc manager


this will download and install it for you with no hassle.

OR you could enter this code into the terminal application (applications > accessories > terminal)

```
sudo apt-get install boinc-manager
```It is clear that you did little to no looking around at all when you tried to install this program. please don't troll the forums if you are too lazy to spend a minute looking for something (i see you waited a total of 7 minutes before you gave up on your post)

---

### Post by boostedtsi on 2007-11-07
> **Tyke91 said:**
> Go to applications > Add/Remove programs > boinc manager


this will download and install it for you with no hassle.

OR you could enter this code into the terminal application (applications > accessories > terminal)

```
sudo apt-get install boinc-manager
```It is clear that you did little to no looking around at all when you tried to install this program. please don't troll the forums if you are too lazy to spend a minute looking for something (i see you waited a total of 7 minutes before you gave up on your post)
Actually...if you would have bothered to read my post...
I got it to download and install fine.
But it still would not work correctly.
IE the program would not run.
You know, the entire reason to have a program installed is to have it run, at least that is what I thought...
Not for it to sit there and continuously error and not do what it is supposed to be doing... Worth while calculations for research and humanity...

---

### Post by macbeth66 on 2007-11-07
> **boostedtsi said:**
> Actually...if you would have bothered to read my post...
I got it to download and install fine


Ah, your orignal post.  I see nothing in your original post to suggest that you "got it to download and install fine".  Do us all a favor and make good on your promise ( threat ) of never installing linux again.

---

### Post by boostedtsi on 2007-11-07
> **macbeth66 said:**
> Ah, your orignal post.  I see nothing in your original post to suggest that you "got it to download and install fine".  Do us all a favor and make good on your promise ( threat ) of never installing linux again.

They don't have a turd emoticon, but here is a nice one for you; :!:
Oh so very funny...

> **boostedtsi said:**
> 
It will not connect to local host is the current issue.

If you knew anything about the actual program I am attempting to get linux to run (you know after I used add/remove programs to get it installed), you would realize that this statement says that the program is installed. But that error says that the program will not communicate with the client program. The computer it was actually installed on. 

But hell what can I say, I installed XP, installed Boinc client and what do you know...
IT WORKS... first try. As it should.

I guess that is still why Linux is still not as popular as Windows, it is not nearly as friendly. 

I have given Linux more than a few shots, but you know what...
Windows still works better than Linux, because you install a program, start said program and that program actually WORKS like it is supposed to.

---

### Post by smartalecks on 2007-11-07
thats really an overreaching generalization :/ almost all apps work flawlessly and install very easily, and I don't have to worry about restarting, viruses, etc... dependencies are satisfied automatically and there is usually alot of support online if something does go wrong.

to your problem:
boinc is known to be fairly unstable at the moment :/. From what you are describing, it sounds like the daemon hasn't started, or there is a blocked port... if you start the manager from your terminal, what errors come up? Also check to see if the daemon is running. You should be able to do this with the system monitor (right click on one of the desktop panels/bar thingies, add to panel, and find 'system monitor' under 'System & Hardware'), though I'm not too familiar with boinc.

---

### Post by ShirishAg75 on 2007-11-10
Perhaps you could try [https://wiki.ubuntu.com/BOINC](https://wiki.ubuntu.com/BOINC) maybe that's what you need :)

---

### Post by Skip Da Shu on 2007-11-12
> **ShirishAg75 said:**
> Perhaps you could try [https://wiki.ubuntu.com/BOINC](https://wiki.ubuntu.com/BOINC) maybe that's what you need :)

but the 1st command in that should now be

```
sudo apt-get install boinc-client boinc-**manager**

```

Other than this small tweak I followed your wiki and had 64bit boinc up and running in little time and my Boinc Manager connects to the Boinc-Client just fine.

Also set it up as a daemon/service and all is good.

Thanx, Skip

---

### Post by Skip Da Shu on 2007-11-12
> **boostedtsi said:**
> Oh so very funny...


If you knew anything about the actual program I am attempting to get linux to run (you know after I used add/remove programs to get it installed), you would realize that this statement says that the program is installed. But that error says that the program will not communicate with the client program. The computer it was actually installed on. 

But hell what can I say, I installed XP, installed Boinc client and what do you know...
IT WORKS... first try. As it should.

I guess that is still why Linux is still not as popular as Windows, it is not nearly as friendly. 

I have given Linux more than a few shots, but you know what...
Windows still works better than Linux, because you install a program, start said program and that program actually WORKS like it is supposed to.

Besides you probably need to spend your extra time fixin' that Talon, not wasting it on 'puters.

---

