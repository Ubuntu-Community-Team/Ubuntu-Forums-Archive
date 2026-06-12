---
title: "Multiple Bugs. These are CRITICAL!"
date: 2007-10-17
forum: General Help
---

### Post by Shoot3r101 on 2007-10-17
Hi guys I am having lots of bugs on ubuntu right now and they need to be fixed or I will probably (yes) *have* to install windows xp again :(. Heres a list of the bugs.

#1. When I am watching a youtube video in firefox and it gets halfway through the video and then I click a link firefox gets completely unactive and stays that way forever so I have to "Force Quit"

#2. When I installed wicd through synaptic package manager it told me to uninstall network-manager and network-manager-gnome so I went ahaid and did. I then made it so wicd would start up using sessions manager and then I pressed ALT+CTRL+BACKSPACE and everything restarted fine then after I logged in I saw no wicd in the tray so i manually opened it. I then un-installed wicd and re-installed network-manager, network-manager-gnome and also installed network-manager-dev for some odd reason don't know why. Then when it said "Configuring Network-Manager" everything just locked up and I had to reboot but somehow it got installed, odd.

#3. When I click on applications and hover something and a new window pops out and there are lines that flicker (these aren't perfect lines) on the side of the window. This somehow goes away when I start beryl-manager.

#4. I cannot watch videos in totem player for some reason, it either just appears black(and if I move the window I can see a bit of the video like a screenshot of it) or just crashes when opening a video. It appears black for music too.

#5. Sometimes when I use my internet cord that I use for my computer for my xbox and then switch back to my computer I can't see my connection information it just says "blah blah blah The glaid file!"

PLEASE FIX THESE BUGS!
I will update this when I can remember the rest of the bugs I have been having.

---

### Post by bodhi.zazen on 2007-10-17
I am not sure those bugs will be considered critical, but the way you fix them, as an end user, is to file a bug report :

[http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

### Post by syxbit on 2007-10-17
it doesn't matter if they're critical or not, Gutsy will be released anyway, as they follow a time based release

---

### Post by Shoot3r101 on 2007-10-17
So no one can help me with these bugs as of now?

---

### Post by d_iane1954 on 2007-10-17
> **syxbit said:**
> it doesn't matter if they're critical or not, Gutsy will be released anyway, as they follow a time based release

sounds so silly lets move to a new version with more bugs rather than fix the existing one first then move on!!!!!!!!!!!!

---

### Post by bodhi.zazen on 2007-10-17
> **Shoot3r101 said:**
> So no one can help me with these bugs as of now?

Did you file a bug report ?

> **d_iane1954 said:**
> sounds so silly lets move to a new version with more bugs rather than fix the existing one first then move on!!!!!!!!!!!!

---

### Post by anthonyJC on 2007-10-18
freezing in firefox is the flash player- remove flash and use gnash instead or remove flash completely or wait for new version of flash to come out beta

---

### Post by syxbit on 2007-10-18
i agree with you, it sucks, but there's nothing we can do about it.
it's either that, or having continuous delays.
can't keep everyone happy

---

### Post by gaussian on 2007-10-18
> **Shoot3r101 said:**
> Hi guys I am having lots of bugs on ubuntu right now and they need to be fixed or I will probably (yes) *have* to install windows xp again :(. Heres a list of the bugs.

#1. When I am watching a youtube video in firefox and it gets halfway through the video and then I click a link firefox gets completely unactive and stays that way forever so I have to "Force Quit"

#2. When I installed wicd through synaptic package manager it told me to uninstall network-manager and network-manager-gnome so I went ahaid and did. I then made it so wicd would start up using sessions manager and then I pressed ALT+CTRL+BACKSPACE and everything restarted fine then after I logged in I saw no wicd in the tray so i manually opened it. I then un-installed wicd and re-installed network-manager, network-manager-gnome and also installed network-manager-dev for some odd reason don't know why. Then when it said "Configuring Network-Manager" everything just locked up and I had to reboot but somehow it got installed, odd.

#3. When I click on applications and hover something and a new window pops out and there are lines that flicker (these aren't perfect lines) on the side of the window. This somehow goes away when I start beryl-manager.

#4. I cannot watch videos in totem player for some reason, it either just appears black(and if I move the window I can see a bit of the video like a screenshot of it) or just crashes when opening a video. It appears black for music too.

#5. Sometimes when I use my internet cord that I use for my computer for my xbox and then switch back to my computer I can't see my connection information it just says "blah blah blah The glaid file!"

PLEASE FIX THESE BUGS!
I will update this when I can remember the rest of the bugs I have been having.

One point:
You are running Beryl, I guess. Beryl is beta software. Not a finished and stable product (actually, it is obseleted by Compiz-Fusion, but that is still in beta). Not everything works in beta software and it is not suppose to even work. 

I cannot help you with problem 1,2 and 5. Except for 5 you could consider spending money on a router/switcher so you don't need to unplug your network cord. But for three and four I have simple solutions: stop using Beryl. Switch back to Metacity. I am seeing both of these too and 3 is hardly a critical bug by any reasonable standard.

You can actually get around 4 while still using Beryl. I don't use Totem  (I use VLC), but I am pretty sure you can do this in Totem too. Beryl (and CompizFusion) have upstream bugs that prevent multimedia playback using Xv (and other advanced output options) using certain video cards. If you switch the video output option to X11 (you will loose some picture quality) you should be able to see your videos in Beryl. Or, you could switch back to Metacity and keep your output option as Xv.

---

