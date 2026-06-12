---
title: "uninstall 8.0.4, reason: hd failure; please help"
date: 2008-05-13
forum: General Help
---

### Post by MadCutter on 2008-05-13
Hello everyone,

Hopefully someone can help me out with an issue I'm having:

Situation: I installed ubuntu on my xp machine, on a 2nd, internal, harddisk. Dual boot XP/Heron. Ubuntu runs like a dream.  ( Windows, well, let's not go into that right now, ok?)

Problem: This 2nd harddisk has a hardware defect or something. It manages to mess up all the workings of my system, both when booting in XP and in Ubuntu.

Need: I have to remove  ubuntu completely, because when the 2nd hd (ubuntu disk) is connected, both XP and Ubuntu are very very slow. Somehow, the disk error consumes a lot of resources.

When I unplug the disk, trying to simply boot XP, grub gets stuck, obviously, because the MBR has been altered by installing Ubuntu.

Question: How can I remove Ubuntu? 

Confusion: the ubuntu website claims boldly that Hardy Heron comes with a convenient uninstaller, but, eh, how does that work? Where can I find this uninstaller?

I'd appreciate all and any help! 


MadCutter

---

### Post by cyberbill on 2008-05-13
Wow, two of these in a row. Just replied to one very similar.

Check here for more info:
[http://ubuntuforums.org/archive/index.php/t-209105.html](http://ubuntuforums.org/archive/index.php/t-209105.html)

-cb

---

### Post by MadCutter on 2008-05-13
Heh, cool, an immediate reply! TX!

Thing is: that thread is old, is from before Heron included the uninstaller. (Which I can't find, grrrr)
I have an Ubuntu issue, meaning I need to uninstall it. The thread you sent me is a windows-issue thing. I have had so much trouble with windows, I really hoped Ubuntu could save my life, but it didn't. Once I replace this hardisk and also my ISP contract (modem that ubuntu doesn't support, unless I get into terminal which means learning a lot and spending much time, which I can't because I need the machine to set up my tailoring company) I can try again to use Ubuntu and I certainly will. Just right now I need to get my XP working normally again, to get my work done. Terminal jobs etc is just much more that I can handle, being a noob and having a company to build.... disaster, as you can understand.....

Would you, hopefully, be able to help me out with the uninstaller thingy? Anyone else, perhaps? I need this machine for my work and the sluggishness that disk 2 causes is unbearable. When I unplug it, box won't start... 

Pleading...

---

### Post by cyberbill on 2008-05-13
I believe the uninstaller is only usable if you installed using wubi. Which if you boot into windows, use wubi to uninstall. I wish I had some better news for you. Otherwise, I found a more up-to-date thread for you.

[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

-cb

---

### Post by cyberbill on 2008-05-13
In the future when you're ready to try again, there's a ton of people here who can walk you through it. I am surprised by your modem not being recognized, that's been a mute issue for a long time. Though, I guess the question is, what type of modem are we talking about. :)

-cb

---

### Post by MadCutter on 2008-05-13
Oh dear, that means I'm f****ed. 

I have to say, for all the good Ubuntu does and is trying to do, anouncing that "we now have an uninstaller" when that only refers to a shelled install (inside windows), is kind of false. And suckers like me will get confused, loose time, and what is really a bummer: they will  loose faith in Ubuntu. It's a nice slogan, but quite unfit to what they actually mean. But hey, that's just my marketing mind talking.

On to the problem, in the last link you posted, there is an xp solution that seems straightforward enough even for me to use. I'll give it a go, and tell you the results here.

---

### Post by MadCutter on 2008-05-13
What exactly would you suggest I would be walked through, I'm confused here. Installing ubuntu is easy enough, i love it. Love the way the os runs too. (mac user by default)  The thing is just that I installed it on a hd that causes my system to nearly stall.

As for the modem, it's a huawei e220 hsdpa umts thingy. Nice, but there is only one package I have been able to find for driving it, and that won't work on my ubuntu, possibly because of the hd failure. And terminal commands etc... Like I said, I have a business to build, I need my tools (i.e. comp) to work. I just haven't got the time to learn how to get the tools to work. (ye, mac user by default. I'm terribly spoilt.)

---

### Post by cyberbill on 2008-05-13
Was referring to this:

> **MadCutter said:**
> (modem that ubuntu doesn't support, unless I get into terminal which means learning a lot and spending much time, which I can't because I need the machine to set up my tailoring company) 

But let's see what happens when you get that hd replaced.
That's a tiny modem! :) No wonder it had trouble finding it! ;)

>  (ye, mac user by default. I'm terribly spoilt.) 

I understand. Got my new MBP in February. :)

-cb

---

### Post by Wandering on 2008-05-13
Just a few thoughts.

You don't need to uninstall Ubuntu, just use XP Disk Manager to delete the partition it's installed on. It's gone then.

It sounds like a jumper problem on the second disk. If it's a SATA, you probably don't need a jumper, but if it's a PATA you need to set as a slave. Maybe you have already done that.

The uninstaller is, as someone above told you, only used in Windows if you installed Ubuntu in Windows as a program there. Then you use Windows add/remove programs in control panel to remove it. If you didn't install in Windows, then you don't need an uninstaller, just use the Ubuntu partition for something else, and format it accordingly - all in Windows.

If you turned the first disk mbr over to grub, then you'll need to reinstall the Windows mbr on that disk. Check out the help files for methods to do that.

Good luck.

---

### Post by jimv on 2008-05-13
> **MadCutter said:**
> Oh dear, that means I'm f****ed. 

I have to say, for all the good Ubuntu does and is trying to do, anouncing that "we now have an uninstaller" when that only refers to a shelled install (inside windows), is kind of false. And suckers like me will get confused, loose time, and what is really a bummer: they will  loose faith in Ubuntu. It's a nice slogan, but quite unfit to what they actually mean. But hey, that's just my marketing mind talking.

On to the problem, in the last link you posted, there is an xp solution that seems straightforward enough even for me to use. I'll give it a go, and tell you the results here.

I saw that today and thought to myself that they should qualify that as being the Wubi uninstaller.

And you're not f***ed.  Running FixMBR from the Windows XP repair console will fix it.
[http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)

---

### Post by MadCutter on 2008-05-14
Hey, thanks a lot everyone. Getting there, I think...

@wanderer: deleting the partition will be ok, (although -eek- partition magic won't start)
This is because I thougth I was being clever, i figured:

Well, if I install ubuntu again, on a c: partition, then the mbr will be corrected, and grub will load without looking for the d: disk. I was right. However, it didn't work. d: disk is out and the platters are currently being being delicately hammered into very artistic coasters. It wasn't the jumpers, because it (sata) was set for slave. But on starting partitionmagic, it would start by telling me about an error on that disk, and do I want to fix it. Also, the boot screen (f10 for menu, f1 for startup) tells me of an imminent failure, also after a full format followed by writing to the disk. disk is dead.

So, am I not happy now? The disk is gone, but I get a dual, nay triple, boot menu: ubuntu on a c: partition (which partitionmagic can't see), xp on a c: partition, and ubuntu on d: disk (gone). I'm guessing the mbr is still a big mess, because starting up now takes a long long time. And Ubuntu won't work, although xp does. Fortunately.

I can't use fixmbr, because when I bought the pc (second hand) (in a country 3000 km from here, so no return policy) it had xp installed, it had a shine xp license sticker on the box, so I thought I was legal. But no, the os was hacked, i found out much later. I.e. no install disks.

Anyone know of an alternative to fixmbr, that automates the process for me?

---

### Post by MadCutter on 2008-05-14
> **jimv said:**
> I saw that today and thought to myself that they should qualify that as being the Wubi uninstaller.

And you're not f***ed.  Running FixMBR from the Windows XP repair console will fix it.
[http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)

Yes, it is a very confusing way to anounce a supergood function. Misleading but probably not at all intentional. In fact, if it would be stated as something like: test drive or something more clear, something that will explain to would-be users that it's a safe uninstallable program (can that be said in one single slogan) I think many many more people would give it a try. After all, installing an os, or a dual boot, is just far too much for most people. But hey, everyone can install and uninstall a program, right?

---

### Post by MadCutter on 2008-05-14
Well, I was saved by a sort of angel. I guess. My neighbour, brainy and geeky and XP wizz, dropped by. He wanted to install a version of Vista for me, so I clubbed him. Then he very kindly helped me by modifying the partitions with the use of an XP installer disk. After that, it was a jiffy to simply copy my cloned XP to the primary partition with Norton Ghost. So I'm back online and all.

Thanks for all you help. I'll surely be back in a few weeks when I'm ready to start tinkering with Ubuntu again. (yes, wubi install, of course.)

Cheers

MC

---

### Post by jimv on 2008-05-14
Thank God for geek neighbors.

---

