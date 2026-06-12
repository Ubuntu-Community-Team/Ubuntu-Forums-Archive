---
title: "Ubuntu 6.10 dragging slow"
date: 2007-03-17
forum: General Help
---

### Post by stchman on 2007-03-17
Hello all, I have noticed that in the last few day ALL my Ubuntu installations are moving real slow.  I have 6.10 installed on my laptop and two desktops.  They all exhibit the same slowness.

During logon the Ubuntu logo stays for a long long time and applications seem to open and close very slowly.  Has anyone else had these effects?  Has any of the patches that have been installed could cause this?

Thanks.

---

### Post by Kateikyoushi on 2007-03-17
No it is running fine for me, nothing slower than before, what video cards do you use ?

---

### Post by stchman on 2007-03-17
> **Kateikyoushi said:**
> No it is running fine for me, nothing slower than before, what video cards do you use ?

My laptop has a Radeon 200 Xpress and the desktops both have nvidia cards (7600GT and 5700 Ultra)

They were running real nice up until a few days ago.  They all just started acting slow.

---

### Post by stchman on 2007-03-17
anyone?

---

### Post by stchman on 2007-03-18
Ok, here are some symptoms.  When I have either a wired or wireless ethernet card enabled the system drags down.  Are there some settings that can be edited?

---

### Post by peabody on 2007-03-18
Have you tried using a system monitor to see what processes might be slowing down your system?

---

### Post by stchman on 2007-03-18
> **peabody said:**
> Have you tried using a system monitor to see what processes might be slowing down your system?

It is only when I enable the ethernet.  I was reading about IPV6, does this have anything to do with it?

---

### Post by Albert E. on 2007-03-18
It is slow:

I installed 6.10 a few weeks ago and was still coping with all the problems a noob encounters when everything became sloooow! 
The only things I had done (since installation) was to install 2 packages of codecs for media players and 2-3 programs. I was working on a ppt presentation,had mozilla and skype running. The first thing i noticed was that skype had problems maximizing/minimizing.Then the Internet became slow - like,2mins to select the url bar!
I restarted and everything was back to normal - internet just fine. Opened the presentation again and in a couple of mins all was slow again....
Today i tried to scan a picture with XSane and ..well it was close to impossible.
As of now,i have normal internet,but dare not open any other applications.

It looks to me that my ubuntu is showing some rather random behavior,but yet there´s no such thing..so how does one run a system check or something else??

Please help,i installed linux in an attempt to run alway from all windows's randomness and  lack of reliability... 


:confused: :confused: :confused: :confused:

---

### Post by dncrash on 2007-03-18
I have ubuntu 6.10 too and it gets very very slow sometimes. In my case i think it's azureus or totem that's making him crazy. 
And when the slowdown happens i don't see anything on my windows partition unless i wait 1 minute or so. 

The problem is preety strange and i can only guess that it can be caused by azureus, totem or ntfs-3g. It appears randomly ....the system can work fine for hours at a time and then suddenly it's all in slow motion.

I think we shoud try a system monitor like peabody said but don't really know which one.

---

### Post by Albert E. on 2007-03-18
Well ..i don't know. If you think that this problem can be fixed, then i'm willing to try all possible solutions. Otherwise i will simply install some other distro while i still have time -i find it really disturbing when my laptop freezes in the middle of my exam session :(

---

### Post by Khaos on 2007-03-18
I'm a completely new user to Linux (about 6 hours into it :p) and I was experiencing your problem as well. Try this, it might help because it fixed my problem :)

Run sudo gedit /etc/hosts in the terminal and just add your hostname in the line 
127.0.0.1 localhost <hostname>. The one below it will have your hostname on it (if im not mistaken).

---

### Post by peabody on 2007-03-18
might want to troubleshoot drive access times

sudo hdparm -t /dev/partitionnamewithubuntu

Anything less than 25 should be alarming.

---

