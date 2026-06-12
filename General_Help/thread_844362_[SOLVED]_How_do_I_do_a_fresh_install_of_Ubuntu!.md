---
title: "[SOLVED] How do I do a fresh install of Ubuntu!"
date: 2008-06-29
forum: General Help
---

### Post by taminrob on 2008-06-29
Need some help here...I messed up something bad! 

I need to do a fresh install of Ubuntu 8.04. When I first downloaded it I went a bit crazy with installing some updates and extra apps, and in the process (I think) something in my system got changed and my computer stopped acting in the manner that I wanted. I couldnt get flashplayer 10 to stay loaded, my touchpad quit working, when I tried to Compiz FireFox wouldnt access the net, and a few other things.

So being the genious (roflmao!) that I am, i decided to just try to reinstall Ubuntu. Did some Google and Forum searching and after surprisingly little information on the subject found a post the basicly said that to get rid of Ubuntu, you need to delete its files, except to the boot file as that would cause the computer not to boot at all, even in Windows (running dual boot). So thats what I did, I went into a terminal and started clearing out files. 

Booted to Win XP and inserted the Ubuntu CD that I used to install it, and tried to do an install...as I'm sure you know, that doesnt work! 

What do I need to do? I dont have a Windows install CD because my machine was preloaded, so from what I think I know I cant even just reformat my D: drive because doing that will also get rid of the Grub boot that Ubuntu replaced the Windows boot information with.

I want Ubuntu, I just want to start over fresh with it and be a bit more cautious about installing and changing things that I dont know about.

---

### Post by ConMan318 on 2008-06-29
You could go into the Windows partition manager and delete your Ubuntu partition, turning it into free space.  Defrag Windows, too, well you are at it.  Then boot from the LiveCD for install, and when it asks how it's going to be installed select "use largest free continuous space".

---

### Post by taminrob on 2008-06-29
This and the above information did the trick.  All seems to be working well now! 

Re: Need a fresh start, Ubuntu wont load
there are two options here,

1- you try to solve whatever issues you had before

2 - reinstall ubuntu.

K, what you need to do is to boot from the live CD, not XP, you can set in your bios the boot order to boot from the CD. Ubuntu does not (as far as I know) load from within WinXP only wubi does.

SO what you need to do is boot your liveCD, and install ubuntu, at some point you should choose the manual install, then you can erase the ubuntu partition and install a fresh one. Just make sure you choose to install grub, the installer should then see your windows partition.

Aside from that you said that winXP came preloaded, do you not have a recovery partition by any chance, if you do you can perhaps make recovery disks. Also it may be a good idea to burn yourself a supergrub CD [google it], just as a precaution, it should allow you to boot whatever operating system you have in case things go south.

It should be fine as long as you don't delete your windows partition.

well good luck

---

