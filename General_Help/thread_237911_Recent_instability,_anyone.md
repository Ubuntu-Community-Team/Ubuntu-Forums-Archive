---
title: "Recent instability, anyone?"
date: 2006-08-16
forum: General Help
---

### Post by Donshyoku on 2006-08-16
Perhaps this issue is only affecting me, but I have had tons of problems with instability recently.  It applies to a few "third party" (not sure if that is the right word) programs like Xine, MPlayer, Banshee, and NetworkManager, but it is really starting to irk me.

Banshee crashes upon exit.  Not really a problem since I was exiting, but a bit unprofessional nonetheless.

Totem/Xine has had tons of problems.  I have been having trouble finding the perfect media player, and this so far is one of the best solutions... at least for DVD.  Yet, it crashes upon me several times while watching a DVD, even causing me to have to do a cold shutdown by removing the battery from my laptop while watching a movie last night.

MPlayer has problems staying open.  It will crash a lot of times with the Mozilla plugin, but more often, it plays the video off center.  My window shows a portion of the video, but the content goes out of my view.  I have to Fullscreen and then exit to get it to center itself. 

Lastly, NetworkManager has been incredibly unreliable lately.  When I log on, I enter my keyring password for my WPA Personal network.  It won't connect, so it asks me for the password manually... it won't connect.  Then, I will have to deny access and create a new connection before it connects to the network it just failed at twice.  Again on the instability, the applet has simply closed itself on me a few times, causing me to logout/login to return it to my panel.

All of these programs have specific problems, which may not even be related to the distribution, but the random program crashes and the multiple force quits each time I get on the computer to surf the net is getting really annoying.  If there are individual solutions, I am ready to work on it... but is anyone else this crashy lately or is it just me?

Dapper is up to date as of 7 this evening and the problems persist.  I am going to download straight Debian later and get it burnt and see if I have the same problems.  I am not jumping the Ubuntu ship, but I am wanting to troubleshoot and see if this is really just bad programs, my system, or the distribution itself.

Thanks in advance for the help/listening to the rant!

---

### Post by orb9220 on 2006-08-16
Are you using 686-smp or 64bit kernels? I have read many that had stability issues when using them and were solved by going back to the 386 kernel.

The other things of this nature that I noticed was people tweaking thier video settings and or installing xgl/compwiz then trying to uninstall and still having issues.

Those are the only things I can think of.
The other is running the memtest at the grub select to check ram.

Sorry I couldn't be more helpful.

---

### Post by Donshyoku on 2006-08-17
I am running the standard kernel that installs with Ubuntu x86 version.  Should I change the kernel package, will it help at all?

Also, I don't have Compiz/XGL/AIGLX installed and haven't on this installation, so I don't think I have any remains from that.  The only things that I have been installing/uninstalling a lot are media player trying to find one that I really like (for both audio and video... can't decide!).  But I have been doing it all through the Terminal using aptitude so I wouldn't think that I have many left-over, conflicting packages.

---

### Post by nix4me on 2006-08-17
I have occasional problems with nautilus and firefox.  Sometimes they crash.  Some times i click something in nautilus and firefox crashes, which is weird.

nix4me

---

### Post by snaga on 2006-08-21
I am recently having trouble with Firefox, and sometimes konqueror crashing or hanging. It seems to happen on certain web pages, not sure why. I think it might have happened when I changed to the 686smp kernel. I will try switching back and see if that helps.

---

### Post by Craig Caldwell on 2006-08-21
I'm running the k7 kernel and banshee is suffering from some serious instability. After uninstalling it I've had all sorts of trouble reinstalling from source as well as from synaptic. Now my Ipod won't sync. I had been running with the k7 and banshee 10.11.0 for a long time with out any problems  now mplayer and banshee are crashing all the time.

---

### Post by compwiz18 on 2006-08-21
I'm running k7 and gaim won't stay open more then 5 minutes without crashing without warning.

---

### Post by ProjectGod on 2006-08-22
my breezy hasnt crashed at all over the months. :)

---

### Post by Donshyoku on 2006-08-23
Hm... at least I am not the only one.  The programs don't bother me as much, but the OS died twice on my yesterday.  It plain froze twice and I had to pull out the power before it would turn off. ](*,)

---

### Post by CassioBunana on 2006-08-25
Hi everyone! I'm experiencethe same problems you are talking about...xine (or gxine..) crash almost every time I try to see every kind of movies...what else? network manager doesn't display at startup my wifi connection nevertless it works perfectly....
My ALSA is almost hang up without reasons I could undestand..

Yeah, actually I can't feel improvements but just more confusion...

Quite boring, isn't it?

---

