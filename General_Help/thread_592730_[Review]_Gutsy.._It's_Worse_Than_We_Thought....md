---
title: "[Review] Gutsy.. It's Worse Than We Thought..."
date: 2007-10-26
forum: General Help
---

### Post by #Reistlehr- on 2007-10-26
Ok.. So Gutsy Problems, Where To Begin. over the past week i've been keeping an eye on problems with laptops, and most notably HP laptops running the AMD64 kernel. Feisty, was pretty Feisty to get working, but it was worth it. But Gutsy.. I think it was a Gutsy move to release it as soon as they did, which personally, i feel was a mistake. Problems that were once fixed in Feisty, are now overshadow by defeat once again, for example, bluetooth. 

For some reason even when you dont have bluetooth, and you stop the bluetooth modules, it still loads bluetooth, wtf? Whether it is disabling the service in the service window, and blacklisting the bluetooth modules, something seems to keep loading it. 

Also, the nice lag between GDM Login, and your desktop, has dramatically taken a turn for the worst. It takes atleast 45 seconds for some users' desktops to load after the crednetials have been authenticated. Atleast in Feisty you could plug in USB devices, and they automounted. In Gutsy, for me and a large group of others, lsusb fails to recognize the devices, even when updating them.  This is a diar problem.

Next, the whole suspend/hibernate fiasco. Still fails to work. Didn't work in feisty, and it doesn't work in gutsy still. Now people say this is an ATI problem, and people say this is an nVidia problem, but i think both are in denial. But, people also need to remember there is more to it than just your video card. This is a bummer. Windows, as frustrating and disorganized as it is, atleast had the whole suspend/hibernate problem worked out. 

Fourthly, SLUB vs SLAB. I can't debate this, because personally, i don't know that much about it. But as one user put it.

Moreover, there has been an addition of AppArmor (Atleast i think it's the name.) This has rendered some users printing privliges useless. As a bug was discovered and milestoned too late for the initial release, everytime i wish to print, i need to run a command, "sudo aa-complain cupsd" just so i can print, if Gutsy even picks up the USB printer.

Ontop of that, when i disable my wireless, using the switch on the front of the laptop, Gutsy fails to load. I end up receiving an Internal Error the X failed to start. That's just fine and dandy. So the whole hour i get on the laptop out of my battery (Compared to the 3 hours in Windows), is cut even shorter when utilizing another piece of hardware that is not needed.

And one last thing is, my wireless card, is identified as a whole other device as in feisty. In feisty i was told it was a Broadcom 4310. In Gutsy it reports it's a 4312. What is going on?!

Don''t get me wrong i love Ubuntu. I've been on the band wagon since Breezy. It runs almost perfect on my Mac Book Pro (For the record i'm using rEFIt, to tri boot mac/feisty/win). I just think that there are a lot of repeated problems that were never addressed. I mean, everytime i check the forums, i'm tired of seeing the same problem reposted in a thousand threads. I don't think it's possible to count the number of threads that had the subject about hibernation/suspend not working. And if you can count them, go ask a girl on a date. :)

But with all the bad, there is some good. I do love the shift to compiz. Even though you need to manually install the ccsm (compizconfig-settings-manager) you will be awed. Gutsy does run smoother and cleaner when it works. You can really feel the ooph when multitasking. But i must say my wireless worked without any hitch. It was pretty simple to get going, unlike feisty where i had to slave for hours trying to even get the device to recognize any wireless networks (And no, the SSID's were not hidden lol). I like how i can completley turn off the backlight, which is a temporary substitute for suspend as it seems to save some battery life untill i can plug it back into the wall. Also, all the fuction keys worked pefect. The one anooying thing i did find is, When you click leftmouse and right mouse, it pasts the clip board.. Why? lol. 

But all in all, I am impressed, but dissatisfied at the same time. With everyone reporting problems, the same problems for that matter, and not that many problem solvers, I think the Gutsy world will be in limbo for a few more week, but that is expected. HOpefully this can help somebody at some point. If you have feisty, don't upgrade for a while. If you are on Gutsy, i join you, and i'll be trying to help be a problem solver, that is, if i don't get banned from launchpad bug reporting for entering so much info. :) 

Happy ubuntuing everybody!!!

And thanks to everyone who makes this community what it is (And to the dev's who make it more possible).

---

### Post by ogwilson on 2007-10-26
agreed. well i think upgrading for me personally did way more bad than good. it just takes alot of manually-made settings you had, resets them, and makes it even harder to get working again. I had Wireless on my laptop set up within 5 minutes on FF, on GG, i struggle to get even the WIRED network to function correclty. Also, on my desktop, my display is very bad. like there are color bleeds everywhere and it hurts my eyes, and i cant use my preferred resolution of 1600x1200 @ 85 hz refresh rate because even if i change all the necessary settings in xorg-xserver or whatever, i get an error saying it couldnt do what i asked and has to boot back up into low graphics mode, where the loop begins all over again.

I love ubuntu, i really do, but i think upgrading so quickly was a mistake.

And it doesnt help that NOONE will answer any questions I have (check my profile for topics made by me) so its even harder to get it up and running. is there a way to downgrade within the system?

---

