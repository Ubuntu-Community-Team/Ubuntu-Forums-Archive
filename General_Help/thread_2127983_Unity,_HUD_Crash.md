---
title: "Unity, HUD Crash"
date: 2013-03-21
forum: General Help
---

### Post by timfinley on 2013-03-21
So I left Ubuntu after the switch to Unity but came back when I heard it got a little quicker. Still a little boggy, but to the issue:

I am using Ubuntu 12.04 on an old gateway with an Intel dual processor. I have only a few windows open, but this has also happened with nothing at all opened. 

I press super to get to the lens, type anything. The system is a little slow catching up with what I am typing but I see what I want to go to. I click or press enter and the Unity menu disappears as well as the top bar and the borders around the windows. 

Everything is still running fine, like chrome and a terminal window, and I can still right click on the desktop. I can't, however, press ctrl+alt+T to open a new terminal to reset or log out. The only wat to do any of this is to hit the power button. 

That works and I tell it to restart, restart happens and all is back to normal. What gives?

It's real annoying to have to stop working and wait for a reset over some little thing like this.
 
But hey, it is still better than using other OS that I have found to be much more frustrating.

---

### Post by ManamiVixen on 2013-03-21
What are your computer specs? Anyways, from what it sounds like, compiz is crashing either from the computer not being powerfull enough to run it, or from a possible memory leak in compiz that is noted on 12.04.

---

### Post by timfinley on 2013-03-21
Any other specs you need? 

Ubuntu 12.04 LTS
Memory: 1gb
Intel® Core&#8482; Duo CPU T2450 @ 2.00GHz × 2 

I'd be willing to bet that it's compiz crashing because of this computer not being able to handle it. Sad about Ubuntu. Used to be my goto for old hardware. Now it's about mint, which I'm not a fan of.

---

### Post by ManamiVixen on 2013-03-21
Yeah, the CPU details on Intel's ARK page looks to weak to run Unity 3D as well as the ram running at 533MHz as well as it being 1GB. Though we can try to fix it! 

Do this:
sudo gedit /etc/sysctl.conf
 
Now at the very bottom of the text, beneath the pound sign at the very bottom paste these two lines as they appear:
# Decrease swap usage to a workable level
vm.swappiness=10

Now save it and close. Then reboot. Swappiness is the tendency of linux to use swap over system ram. It works well for servers, but on a desktop it is unnecessary. By default, Ubuntu set 60, which means when 60% of the ram is used, swap is initiated for use and unimportant stuff starts to store there slowing down the PC. By setting 10, Swap won't be used until the ram is almost full.

---

### Post by deadflowr on 2013-03-21
Slowdowns on Unity tend to be more graphics card related over anything to do with CPU, or RAM.

Do you know the graphics card on the system?

---

### Post by timfinley on 2013-03-24
manamivixen: not good advice. This slowed my computer to a near halt. Undid that, back to normal. deadflowr: Graphics is stock whatever came with this laptop. I'll just use XFCE. Fine for me but others less inclined to linux don't get it. Six years of using Linux and it has damn near the same problems....

---

### Post by ManamiVixen on 2013-03-24
Really? That is odd... Usually swap slows a PC, what I gave differed from swap allowing for faster use. Could of been too much of a load on the ram, but I doubt it.

---

