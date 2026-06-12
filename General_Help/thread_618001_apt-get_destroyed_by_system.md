---
title: "apt-get destroyed by system"
date: 2007-11-19
forum: General Help
---

### Post by caen1944 on 2007-11-19
Hi Folks,

Well, I just tried running the "add/remove" software and it complained about something and asked me to run some apt-get commands. I don't remember which ones but I think it was apt-get update and apt-get install -f or some such thing. 

Anyway, after running that, pretty much nothing survived. It pretty much removed all my software. I don't even have the synaptic package manager. Half my menu items are missing. My file browser is gone. And the list goes on and on. After rebooting, I can't even log back in.

Is their any hope to fix this or am I screwed. After the autoupdater destroyed my installation of 7.04 when updating to 7.10, this would be my second reinstall from scratch. I am no linux expert, but I would have thought it would have been safe to perform the tasks that the "add/remove software" recommended.

I hope there is a simple fix, because I don't think I am going to bother with another reinstall of ubuntu. 

Thanks

---

### Post by Nano Geek on 2007-11-20
Try running this:```
sudo apt-get install ubuntu-desktop
```
It's odd though that it deleted your programs though.

---

### Post by caen1944 on 2007-11-20
Thanks, I'll give that a try when I get home. Last night I couldn't even log in, but I did try to log in at the gnome screen. I'll try dropping to a terminal from the login screen instead.

I really wish I could remember what error message the add/remove programs popped up that enticed me to do this. All I know is that I followed these "instructions" and now the system is dead.

No matter what, the standard GUI should never recommend doing something that will destroy the system. It seems to me to that this is a serious flaw. So far my experience with 7.10 has not been a happy one.

---

### Post by malfist on 2007-11-20
It usually give that error when you installed something, then canceled the install when apt or aptitude was installing the program. apt-install -f or some such thing just causes apt to look though your installed software and uninstalled software and fix inconsitancies.

If the apt-get doesn't work, try aptitude install ubuntu-desktop (or xubuntu/kubuntu)

---

### Post by Nano Geek on 2007-11-20
> **caen1944 said:**
> Thanks, I'll give that a try when I get home. Last night I couldn't even log in, but I did try to log in at the gnome screen. I'll try dropping to a terminal from the login screen instead.

I really wish I could remember what error message the add/remove programs popped up that enticed me to do this. All I know is that I followed these "instructions" and now the system is dead.

No matter what, the standard GUI should never recommend doing something that will destroy the system. It seems to me to that this is a serious flaw. So far my experience with 7.10 has not been a happy one.Though I've run that command several times on my system and it has never caused a problem. I think that this just might have been a freak accident.

---

### Post by caen1944 on 2007-11-20
Well, dropping to a console and running "apt-get install ubuntu-desktop" restored the system to a working state. I am still missing a bunch of stuff I that also got uninstalled in the accident, like eclipse, but I can reinstall all that when I realize what I am missing. Some stuff that I had installed manually, like vmware is still intact (which was fortunate, as it took a while to get that working)

Thanks for the help everyone.

I hope this thread helps anyone else who has the same unfortunate experience.

---

### Post by Nano Geek on 2007-11-20
I'm glad that fixed it for you. And you're right. That command just installs the default Ubuntu desktop, but at least it got you back where you can reinstall the programs you want.

---

