---
title: "Disaster recovery"
date: 2007-07-21
forum: General Help
---

### Post by the lemming on 2007-07-21
The saying goes "If it ain't broken don't fix it".

Before I started my quest of messing around with Operating Systems I taught myself to use Ghost 2003 which didn't half get me out of a lot of sleepless nights I can tell you.  With my limited experience I have learnt that I can not do a dual boot of XP and Vista or XP and Linux because the boot up does not recognise the second OS.  At the moment I am also not experienced enough to mess around with the windows booter or the grub booter.  But I am willing to learn if anybody can advise me.

Learning how to make a clone of XP gave me a safety option of experimenting.  And now I have learnt that using Linux has a huge learning curve.  With this all in mind I would like some options on desaster recovery or an ability to restore my system to a safe working Linux configuration.  I know some of you may cry NOOOOOOOOOOOOooooooooooo but I still want to have a working XP configuration.  I am a realist and appreciate that the majority of the world use XP, which works fine for me and the majority of the plebs of the world but I refuse to install Vista.

In a nutshell I would appreciate any tips or advice on creating a safe and quick way of returning my computer to normal after some sort of disaster.

Cheers

---

### Post by lisati on 2007-07-21
I beg to differ on your comment that you can't dual boot XP & Ubuntu and have both. My Compaq desktop has both XP home and Ubuntu on it, with both accessible from the boot menu. This was achieved by using the standard installation on the Live CD

---

### Post by the lemming on 2007-07-22
> **lisati said:**
> I beg to differ on your comment that you can't dual boot XP & Ubuntu and have both. D

You are correct, you can dual boot XP and Ubuntu.  It is probably my initial post that has cause some confusion.  Sorry.

Before I learnt about the existance of Linux I bought a copy of Vista (Please don't laugh) and I was able to boot XP and Vista.  I was then able to make a clone of the master drive with both operating systems.  Everything worked fine until I ran the clone.  Once the computer booted up after this operation I would only be able to boot into one operating system.  The boot would not recognise that there was enough data on the Hard Drive for two operating systems.  In effect I had one operating system with all the data needed for the second operating system.  I had no way, and still have no way, of restoring the boot sequence to recognise the second operating system which has been sucessfully cloned.

I am hoping that somebody will teach me how to fix the boot sequence once I have made a clone of two operating systems (Which will be Linux and most definately NOT Vista).

I would like to explain that I did not dual boot with three OS's.  It was always XP / Vista or XP / Linux and never all three at the same time. 

I hope this helps explain a little more about what I am trying to achieve because I believe that Norton Ghost can still help me.  Norton Ghost will clone my Master drive faithfully, it is just that I do not know how to fix the boot records ,or what ever they are correctly called, to get my computer to realise that it can dual boot.

I do have a copy of Ultimate Boot CD but that thing is way over my head and there are far too many options for me to even begin to understand.

---

### Post by Daveth on 2007-07-22
this
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

is a well written and useful site to help you along a bit. I would also strongly suggest that you create a separate /home partition, where most of your personal data will be kept. Then, if you kill off ubuntu you can always just write back safe in the knowledge that most, but not all, of your important stuff will not be touched (you do not format the /home partirtion, of course!).

It might be worth you loading up Sbackup which you can get from Synaptic. Whilst not as slick as Norton, it will allow you to save and recover the files and folders you saved with it. If you use it with an external hard-drive, you can be a s reckless as you want- with a reasonable degree of impunity!:)

---

