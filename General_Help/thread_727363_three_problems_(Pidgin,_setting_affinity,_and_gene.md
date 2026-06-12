---
title: "three problems (Pidgin, setting affinity, and general performance)"
date: 2008-03-17
forum: General Help
---

### Post by gamelord12 on 2008-03-17
I'm almost as nooby as it gets for a Linux-user.  I've never compiled anything for my distro before, but I can't find a binary for a particular plug in for Pidgin.  I'm trying to install music tracker.  It puts the song that I'm listening to in my AIM status.  I've tried a few different ways to install it, but if someone could give me a fool-proof set of instructions (the simpler, the better) for installing this plug in, that would be great.

My second problem is that I can't get Unreal Tournament to run correctly.  It's installed and it runs, but it's running at two times speed, so I need to set the affinity for it somehow.  I'd also like it to automatically launch on only one core every time I boot it up (is it possible to put those additional commands in the launcher?).  Also, the mouse leaves the window that the game's running in, which is bad because I need the mouse to aim my avatar's gun.  If I run it full-screened, the game gets confused by my laptop's widescreen resolution and the top and bottom of what I'm supposed to see is chopped off, making it next to impossible to use the game's menu system.

My third problem is that my network manager appears to keep crashing on me.  I'll lose my wireless connection, and then the rest of my system will sort of lock up shortly afterward.  I won't be able to switch workspaces, exit programs, or open new programs.  If there's an easy way to force quit programs, that would be nice, but I'd also like to fix whatever's making my system crash.

Any help anyone can offer would be great.

---

### Post by duncan.hawthorne on 2008-03-18
theres a panel applet called force quit, or you can run the program xkill. you can also kill programs in system> administration> system monitor > processes

if you are running the windows version in wine, its a known bug, sadly youve just got to wait for the fix. there is a native linux version too, which you might have, which might work better. (but maybe that is what you are already using)

i would guess its not the network manager causing things to crash but something else which is taking down the network manager, you should give more info. look in system monitor to see which programs are crashing. (they usually start using very high cpu). you can always press ctrl+alt+backspace as a very quick way to kill X, and get you back to your desktop after a crash.

you could try [http://www.getdeb.net/app/pidgin-musictracker](http://www.getdeb.net/app/pidgin-musictracker) , although generally try and look just in synaptic for most of the programs posted there as they will probably work better straight out of synaptic

---

### Post by prshah on 2008-03-18
> **gamelord12 said:**
> won't be able to switch workspaces, exit programs, or open new programs.  If there's an easy way to force quit programs, that would be nice, but I'd also like to fix whatever's making my system crash.

Any help anyone can offer would be great.

Ctrl+Alt+Shift+SysRq+"E" Terminate running processes or "B" instant reboot (not recommended).

---

### Post by duncan.hawthorne on 2008-03-18
>>>>>Ctrl+Alt+Shift+SysRq+"E" Terminate running processes or "B" instant reboot (not recommended). 

ok, thats a really bad suggestion

but magic keys can give you a safe restart. (not like mentioned above) but this is as a last resort (well second to last before pressing your computers reset button, or holding down the power button, or turning it off at the wall)

check out [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)
specifically the last section for a safe restart.

but this is way more than you need, if all you want to do is kill a crashed program. and is dangerous if you typing the mnemonic wrong

---

### Post by gamelord12 on 2008-03-19
The installer they had on getDeb crashes Pidgin, but thanks for your help; I can't find it in binaries anywhere else anyway.  If you know a way to uninstall that plug in now, that would be nice though.  I hate to have a plug in in the list that doesn't work.

As for my setting affinity problem, I'm running Unreal Tournament natively, and I know that there is a way to set affinity, but the pages I found were all way too advanced for me.  I figured maybe someone coded an easier way to do it by now.  Maybe there are a few easy commands that I could plug into a launcher somewhere that would make the program boot up like that every time?

Doesn't Ctrl+Alt+Backspace log me out and shut down every program I'm running?  That's not always an acceptable solution.  I'd like to have a surefire way to fix this if possible.

---

### Post by sdennie on 2008-03-19
> **gamelord12 said:**
> 
My third problem is that my network manager appears to keep crashing on me.  I'll lose my wireless connection, and then the rest of my system will sort of lock up shortly afterward.  I won't be able to switch workspaces, exit programs, or open new programs.  If there's an easy way to force quit programs, that would be nice, but I'd also like to fix whatever's making my system crash.


What network card are you using?  It sounds to me that it's more of a driver issue than a network manager problem.  If it hangs and you can still Ctl-Alt-F1 to get to a terminal, it might be useful to type "dmesg" and see what it has to say.

---

### Post by gamelord12 on 2008-03-19
I've got a Dell 1420N that came with Ubuntu re-installed, so I'm using that driver.

---

### Post by sdennie on 2008-03-19
> **gamelord12 said:**
> I've got a Dell 1420N that came with Ubuntu re-installed, so I'm using that driver.

I would follow these instructions from Dell to see if it fixes your network problem.  I had a similar problem with a Dell laptop but, this fixed it completely: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)

---

### Post by gamelord12 on 2008-03-23
Well, I solved my Pidgin problem.  I took out some time to learn how to compile it myself.  It really wasn't too bad.  My system hasn't done a complete crash in a while, but now I'm trying to get my processor affinity working.  It doesn't seem like there's any easy way to do it.  I looked at the man pages for taskset, and then I modified Unreal Tournament's launcher to run with this command:

taskset 0x00000001 <directory of UT>

The game still booted up, albeit after quite a delay, but then it continued to run on both cores as it always had.

---

