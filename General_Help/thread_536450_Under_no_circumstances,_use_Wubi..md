---
title: "Under no circumstances, use Wubi."
date: 2007-08-27
forum: General Help
---

### Post by izanbardprince on 2007-08-27
I thought I'd use Wubi to get an easy Ubuntu install on my XP Pro x64 system, but I was wrong.

1. Disk access is SLOW, the Wubi site said "slightly" slower than a native ext3 partition, it was like half as fast as accessing an ext3 partition.

2. Using the Software Update program, which has an update for the HAL Daemon, whacks the customized HAL Daemon that Wubi installs, and then HAL can't initialize when you reboot, took me a while to figure out what happened.

Needless to say, I felt bad uninstalling Ubuntu from Windows XP's Add/Remove Software applet, but I feel for all those poor newbies that this tool is aimed at who will think Ubuntu is a slow, broken pile of crap because of Wubi.

---

### Post by Polygon on 2007-08-27
wait, inst wubi a windows program that aids in resizing/installing ubuntu on windows users computers? or... am i wrong

---

### Post by picpak on 2007-08-27
> **izanbardprince said:**
> 1. Disk access is SLOW, the Wubi site said "slightly" slower than a native ext3 partition, it was like half as fast as accessing an ext3 partition.[

Their [FAQ](http://wubi-installer.org/faq.php) says to install [LVPM](http://lubi.sourceforge.net/lvpm.html) to speed it up. Have you tried that?

---

### Post by leo_rockway on 2007-08-27
i don't get it... what's the supposed benefit of using wubi when there are live cds?

live cds are slow too... but if you're willing to do smth like install ubuntu on windoze it means you only want to test it not keep it like that. so i don't see why use anything else than a live cd to test ubuntu.

---

### Post by Fbot1 on 2007-08-27
This is better:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by robconscient on 2007-08-27
hmm. Wubi works fine for me. I have a work laptop that I use Wubi on, and it functions properly. Only time I ever had a problem was Windows related. You have to keep your Windows installation defragged and you have to regularly run chkdsk. As long as I do that, I can regularly experience the sweet gooey goodness that is free software.

I imagine the Wubi developers would like to hear any constructive criticism, [in the appropriate forum]("http://ubuntuforums.org/forumdisplay.php?f=234") ?

YMMV

---

### Post by Depressed Man on 2007-08-27
> **leo_rockway said:**
> i don't get it... what's the supposed benefit of using wubi when there are live cds?

live cds are slow too... but if you're willing to do smth like install ubuntu on windoze it means you only want to test it not keep it like that. so i don't see why use anything else than a live cd to test ubuntu.

Wubi lets you install Ubuntu easily (well for those who are afraid of partitioning, shrinking Windows, etc..). 

Wubi got me into Ubuntu (and only after when I realized I really liked Ubuntu I seeked help for a walkthrough for partioning and resizing my Windows to get a real Ubuntu install).

---

### Post by Richardky on 2007-08-27
Wubi is a great things esp for newcomers ... i use it on my Laptop for a simple quick no fuss (safe duel boot) install works great .. common tweaks will bring the speed right back up to snuff fast as standard install ...

heres a good list of tweaks

[http://www.xlntsolution.com/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/]("http://www.xlntsolution.com/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/")

---

### Post by leo_rockway on 2007-09-11
> **Depressed Man said:**
> Wubi lets you install Ubuntu easily (well for those who are afraid of partitioning, shrinking Windows, etc..). 

Wubi got me into Ubuntu (and only after when I realized I really liked Ubuntu I seeked help for a walkthrough for partioning and resizing my Windows to get a real Ubuntu install).

ok, i understand it worked for you and that's great. but i still don't see the benefit over a live cd. you don't need to partition with a live cd and you don't even touch your hd. it is completely safe to use it, even more than wubi i suppose, since with wubi you actually have to make an installation.

i'm not saying wubi is bad either cuz i never tried it myself, but a live cd sounds more appealing imho.

---

### Post by K.Mandla on 2007-09-11
Moved to the Wubi forum.

---

### Post by n3tfury on 2007-09-11
> **Richardky said:**
> Wubi is a great things esp for newcomers ... i use it on my Laptop for a simple quick no fuss (safe duel boot) install works great .. common tweaks will bring the speed right back up to snuff fast as standard install ...

heres a good list of tweaks

[http://www.xlntsolution.com/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/]("http://www.xlntsolution.com/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/")

i'm sorry, but those tweaks aren't for newcomers, and they're certainly not "common" to those folks.

---

### Post by ago on 2007-09-11
> **izanbardprince said:**
> 1. Disk access is SLOW, the Wubi site said "slightly" slower than a native ext3 partition, it was like half as fast as accessing an ext3 partition.
Hmm it should be almost same speed in most case. If you can profile we might be able to find the issue

> 2. Using the Software Update program, which has an update for the HAL Daemon, whacks the customized HAL Daemon that Wubi installs, and then HAL can't initialize when you reboot, took me a while to figure out what happened.
That's a known issue, but at the moment we (the developers) have not been able to reprdocue it (and hence fix it), again, if some user could send detailed reports that could be addressed. A quick fix is to downgrade HAL reinstalling the previous version, look in this forum for details.

---

### Post by jryprt on 2007-09-13
> **leo_rockway said:**
> ok, i understand it worked for you and that's great. but i still don't see the benefit over a live cd. you don't need to partition with a live cd and you don't even touch your hd. it is completely safe to use it, even more than wubi i suppose, since with wubi you actually have to make an installation.

i'm not saying wubi is bad either cuz i never tried it myself, but a live cd sounds more appealing imho.
You can save settings , bookmarks ,Apps. I do not think you can do that on live cd .

---

### Post by Fred Doolie on 2007-09-13
> **leo_rockway said:**
>  live cd sounds more appealing imho.

Here's my take on it (if I may).
When you first hear of this "Ubuntu Linux" thing you try the live CD just to see what it iis. It looks pretty cool but you can't save anything and it's SLOOOOOOOOOOOOOOW.  You can't seriously try Ubuntu. The Live CD is a "Toy Ubuntu" so to speak.

You think "This looks pretty cool". So you use Wubi for a few days/weeks to give a "real" Ubuntu install a trial.

Then you either:
A) Say "Forget it" and easily uninstall Ubuntu from your system. No harm done.
or
B) Repartition and install a dual-boot real Ubuntu system or toss Winblows altogether.


The purpose that I see for Wubi is to safely install a "real" Ubuntu system and give it a real good hard test run or installing Ubuntu without smegging up your hard drive with partitions and strange stuff.

My personal reason for using Wubi (for the time being) is that I *CAN NOT* get my graphic card working (32Meg On-Board NVidia GeForce 4-MX) In Ubuntu. I'm going to Wubi it and try everything and anything in the Wubi install. I don't care if I smeg it all up. I'll have backup copies of the virtual partitions and can recreate them easily. Another plus for a Wubi install I'd say. Make backups of the virtual partitons and you can go back in time if you mess something up.
 
 



... Two cents deposited.

---

### Post by Mavtech on 2007-09-18
How can someone seriously compare Wubi to the Live CD?  Wubi is a real install of Ubuntu.  In the Live CD, the menus hesitate and it's slow to open an app.  I have Wubi on my desktop.  I have a regular install of Ubuntu on my laptop.  I definitely do not notice a difference in speed.  I even have Compiz Fusion working well on it.

---

### Post by BernardB on 2007-09-18
> **ago said:**
> That's a known issue, but at the moment we (the developers) have not been able to reprdocue it (and hence fix it), again, if some user could send detailed reports that could be addressed. A quick fix is to downgrade HAL reinstalling the previous version, look in this forum for details.
I tried upgrading from Feisty to Gutsy and can't boot either because of HAL; what kind of "detailed" reports do you want?

Apart from this issue I think Wubi is awesome.

---

### Post by carolinason on 2008-07-15
Thanks Fbot1. Oh, how do I thank you..?

---

### Post by ago on 2008-07-15
> **BernardB said:**
> I tried upgrading from Feisty to Gutsy and can't boot either because of HAL; what kind of "detailed" reports do you want?

Unfortunately dist-upgrades are supported only from 8.04 onward. This is explained in the FAQ on this forum as well as in the [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide).

---

### Post by BigDXLT on 2008-07-23
Wubi (with Kubuntu and KDE 4.1) is running great for me so far.  There is absolutely *no comparison* to a live cd for me.  

[SIZE="1"]Then again, I built this computer to run vista so it should be able to handle a nice efficient operating system![/SIZE]

Nonetheless, I bet Wubi reels in more users for Ubuntu than it loses anyway.  I bet Ubuntu *itself* scares off more people than the odd problem that comes up due to Wubi.

---

### Post by dmanuel on 2009-10-24
> **leo_rockway said:**
> i don't get it... what's the supposed benefit of using wubi when there are live cds?

live cds are slow too... but if you're willing to do smth like install ubuntu on windoze it means you only want to test it not keep it like that. so i don't see why use anything else than a live cd to test ubuntu.


Leo, the reason one should use Wubi rather than a Live CD to try Ubuntu is because Live CDs don't allow you to install packages or, say, save your work or your modified settings. And they are SIGNIFICANTLY slower than Ubuntu installed via Wubi, in my experience.

---

### Post by Uncle Spellbinder on 2009-10-25
> **dmanuel said:**
> Leo, the reason one should use Wubi rather than a Live CD to try Ubuntu is because Live CDs don't allow you to install packages or, say, save your work or your modified settings. And they are SIGNIFICANTLY slower than Ubuntu installed via Wubi, in my experience.
Nothing like resurrecting a 1 1/2 year old thread. 

:shock:

---

