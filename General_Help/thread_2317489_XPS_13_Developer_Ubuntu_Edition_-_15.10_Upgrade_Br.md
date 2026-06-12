---
title: "XPS 13 Developer Ubuntu Edition - 15.10 Upgrade Broke WiFi and Xorg"
date: 2016-03-16
forum: General Help
---

### Post by Jaydamis on 2016-03-16
Howdy,

I'll start this by saying I'm an ubuntu novice. I know the basics of linux use, installing packages, where to find config files, etc.  I bought the (now older) Dell XPS 13 Developer Edition in order to have a machine that *shouldn't* be as problematic as any random laptop.  I knew going into this that it wasn't going to be perfect and probably end up being an insightful hobby - being forced to fix my machine vs just spinning up a new VM when things break.

All that being said - I had a couple minor issues out of the box. (I'm just giving some background to the current issues... skim down a bit if you want to get straight into my current problem)

On initial setup, I tried to make a recovery USB, (prompted during the installer). It crashed the whole installer and left me in a graphical session of a user called OEM... hoping everything was fine, I just restarted the machine and I was able to log in with my newly created user. No big deal, stuff happens.

Second, the trackpad acted strangely. Areas of the pad would become a deadzone, or act like they were always clicked. In chrome, two finger scrolling did a double click if I released my fingers too fast. This was usually fixed by disabling the touchpad and re enabling it, but often I had to restart. I tried a few thing, but since I was mostly using the terminal, its something I could live with. I tried installing different drivers on dell's site, but the .deb installer said i had a newer version.  I did read that the issue was resolved in 15.10.

(I'm running 14.04 LTS at this point)

**--actual problem below--**

Ok cool, I'll go to 15.10!

I made sure all my software was up to date - sudo apt-update / upgrade.

Then i did the distribution upgrade...

It downloaded what it needed... asked me if i wanted to continue... did its thing for awhile. Then there was notice that there were too many errors to continue. Wha?  Tried doing sudo apt-update / upgrade and it complained about packages not being able to be installed from unmet dependencies. I shut the machine off for the night, and decide to look at it a bit when I get to work.

On turn the machine back on, I'm greeted with a login shell.  I try startx.  It doesn't load and takes me back.  I try updating again... same issue as yesterday. When i tack -f on the end (apt-get install -f), as stated by the error output and some other posts, it wants to update, but can't get any internet because my wifi no longer works. (ifconfig yields just the loopback).

Any tips on what to do on this? I was under the impression moving a version up was relatively safe?  I'm pretty disappointed, but also excited to use this to learn a bit.

Thanks for any help :D

(I'm going to get some screenshots)

---

### Post by Geoffrey_Arndt on 2016-03-17
Sometimes online upgrades not nearly as reliable as full installs from scratch.   (often folks forget to disable all PPA's for example).    Since 16.04 due out in a month, might look at downloading latest beta and upgrading via normal system updates process.

---

### Post by Bucky Ball on 2016-03-17
You didn't move a version up, you moved two, and one of those is EOL. 15.04 comes in between but for some reason there is an upgrade path from 14.04 directly to 15.10 (a new 'innovation') which I haven't seen work for anyone here at least. Avoid.

I also wouldn't encourage you to install a development version unless it is on another partition. Wouldn't be using that as your day to day OS.

Thing is, with your upgrade problem from 14.04 to 15.10, you started off with a broken system in the first place by the sounds. An upgrade may have fixed one, or maybe more, problems, but upgrading a broken system is usually going to give you ... a broken system. Best to research how to fix your problems before upgrading or going for a clean install of another release if you can't fix them. 

Good luck.

PS: [These come with 14.04 pre-installed]("http://www.dell.com/us/business/p/xps-13-9350-laptop-ubuntu/pd") so odd you're having so many issues with that release ... perhaps Dell tweak the default Ubuntu for their machines, but generally Ubuntu works well on Dell.

---

### Post by vasa1 on 2016-03-17
> **Bucky Ball said:**
> ... **perhaps Dell tweak the default Ubuntu for their machines**, but generally Ubuntu works well on Dell.
That's the impression I have as well from stray comments on the internet.

---

### Post by mastablasta on 2016-03-17
> **Jaydamis said:**
> 
Any tips on what to do on this? I was under the impression moving a version up was relatively safe?  I'm pretty disappointed, but also excited to use this to learn a bit.



1. download 15.10
2. backup imporant data
3. install 15.10, but do not format the partition during install.

hopefully this will install 15.10 and leave many things that you use working or repairable. 

if not you have a backup, nuke the previous install (format) and go with a fresh install. later upgrade to 16.04 which is supported for 5 years.

---

