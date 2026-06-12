---
title: "Problems: hotkeys, beryl, tv-out switch"
date: 2007-05-31
forum: General Help
---

### Post by wheezart on 2007-05-31
Hello everybody! I'm using Kubuntu 7.04 and i've stumbled upon two somewhat frustrating problems
[LIST=1]I've set up hotkeys in KDE - in my case mirroring some of the Windows default hotkeys i'm so used to at work. For example Win+F opens up search, Win+D shows desktop, Win+R opens Run dialog and Win+T to open xterm. They worked for a while, than after a reboot they suddenly stopped - the definitions in the Kmenu are still there but the commands just won't execute... that's bad in my list =( [*]I've configured a TV-out display for my nvidia mx 440 on KDE - now i have a seperate screen! Cool! =) But that seperate screen is in the living room and the box is in my own cozy and comfy room... Now if i'd want to start a movie with Mplayer on that screen i need to see what i'm doing on that screen right? How do i switch between Scrren 0 and Screen 1 on my Monitor? (And is there any way to do it in that matter?) 
[*] When i power on my PC and log into KDE beryl starts without window decorations (eg. no emerald frame) untill i select Reload Window Manager from beryl-manager. Does anyone know what is causing this?
[/LIST]

Thanks in advance you lot, and greetings from Bulgaria! =)

---

### Post by ihristov on 2007-07-19
> **wheezart said:**
> 
I've set up hotkeys in KDE - in my case mirroring some of the Windows default hotkeys i'm so used to at work. For example Win+F opens up search, Win+D shows desktop, Win+R opens Run dialog and Win+T to open xterm. They worked for a while, than after a reboot they suddenly stopped - the definitions in the Kmenu are still there but the commands just won't execute... that's bad in my list =

I suspect the problem is caused by beryl. Did they stop working after you installed beryl and then rebooted?

> **wheezart said:**
> I've configured a TV-out display for my nvidia mx 440 on KDE - now i have a seperate screen! Cool! =) But that seperate screen is in the living room and the box is in my own cozy and comfy room... Now if i'd want to start a movie with Mplayer on that screen i need to see what i'm doing on that screen right? 
How do i switch between Scrren 0 and Screen 1 on my Monitor? (And is there any way to do it in that matter?) 


As far as I know it is not possible. They are separate screens. The idea is a use of a dual-monitor for a bigger screen that is in front of you. For what you want, maybe you can use VNC - "vncviewer localhost:1" or something like that.


> **wheezart said:**
> When i power on my PC and log into KDE beryl starts without window decorations (eg. no emerald frame) untill i select Reload Window Manager from beryl-manager. Does anyone know what is causing this?

Beryl is known to have quite a few bugs, but having said that, are you loading beryl-manager with every session? I guess you are. Maybe it's a matter of load order? Try removing beryl-manager from autostarting with every session and then start it manually after you have logged in and see if it works then. Do you have setup a "fallback" decoration (window manager) in beryl-manager?

---

