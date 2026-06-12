---
title: "Not able to select Ubuntu on boot"
date: 2008-02-24
forum: General Help
---

### Post by jackdelamare on 2008-02-24
Hi,

I just installed Ubuntu using Wubi and it seemed to work fine. When it restarted the boot screen flashed but then Vista began to load.

I tried restarting again and the same thing happened, I cannot select which system to boot with, Vista just loads. I tried pressing F8, F11, F5, F1 and really of the F's... but it didn't give me the choice.

I hope someone can help, Ubuntu looks really cool.

Thanks,

Jack

---

### Post by Rocket2DMn on 2008-02-24
Sounds like either you didn't actually install, or GRUB didnt' install.  Check out this link: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
You will need to reinstall GRUB (overwrite the windows MBR - it's ok).
You can also check out the Super GRUB Disk - [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by jackdelamare on 2008-02-24
Ok thanks, I'm going to install the EasyBCD one as I have Windows Vista and hopefully that'll work. I might end up doing it tomorrow since LOST is on in a minute and I have school tomorrow :(.

EDIT: I'm in EasyBCD right now... what do I do? This is confusing.

---

### Post by Rocket2DMn on 2008-02-24
I don't know anything about EasyBCD, I suggest using the LiveCD to install GRUB, it's a time-tested and proven way to setup a multiboot system.  If you're set on using EasyBCD, you may have to look up some documentation on it.  
Your linux install has an ext3 file system, so that is how you can recognize it ("Linux native").  If it lets you select GRUB as the bootloader, that is what you should do.

---

### Post by jackdelamare on 2008-02-25
Err... sorry, I'm new to this. What is the LiveCD?

---

### Post by housam on 2008-02-25
> **jackdelamare said:**
> Err... sorry, I'm new to this. What is the LiveCD?

The live cd is what we are usually use to install ubuntu. You can get it by ordering from ship it or downloading and burn it to a blank cd. look at [[COLOR="Red"]_this guide_[/COLOR]]("http://www.ubuntu.com/getubuntu/releasenotes")

---

### Post by stoodleysnow on 2008-02-25
You probably have the LiveCD if you managed to do Wubi.

---

### Post by jackdelamare on 2008-02-26
I did use Wubi, but I torrented Ubuntu with the version that works with the current Wubi. Does anybody know how I can use EasyBCD to allow me to select Ubuntu on start up. In that program it does say Ubuntu is there.

---

### Post by jackdelamare on 2008-02-27
I think I might try making Ubuntu the default OS loader... but when I want to use Vista would I have to download the EasyBCD for Ubuntu and do the same?
Is there any easier way? Please help, it does say Ubuntu was installed.

---

### Post by Rocket2DMn on 2008-02-27
I think you need to go ahead and follow the guides we have already listed.    The LiveCD is here - [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and the directions to reinstall GRUB are here - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-9f28b5a7f41d3659b2ae759665f8bc89ed5b351d](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-9f28b5a7f41d3659b2ae759665f8bc89ed5b351d)
Forget the whole EasyBCD stuff, just use the LiveCD

---

### Post by jackdelamare on 2008-03-04
So you're telling me I have to download the whole Ubuntu package AGAIN just to sort this problem out? It takes hours to download, and for the version I have installed now I used Wubi to install. Wow this is hard. Does anybody else know anything about EasyBCD or maybe an easier way to get this working? I'm sorry, but this is way to hard.

---

### Post by Rocket2DMn on 2008-03-04
Wubi is a little different than doing a regular install, and is not an officially supported method.  I'm told wubi is still in beta and I don't know how good it's compatibility with Vista is, but the best way to use Ubuntu is to do a regular install from the LiveCD.  You might just want to go uninstall Ubuntu from Wubi and start fresh.   (I think) Wubi doesn't even set up different partitions like a regular install does, so using any method other than wubi's to boot into it won't work.
If you downloaded the LiveCD .iso file, you don't need to download it again, just burn it to a CD as an image.  Otherwise, just redownload it, I'm sure you can find something else to do while it downloads.  Alternatively, you can order an Ubuntu CD from canonical, but it takes 6+ weeks to deliver - [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) .  If you take that path, I would wait until Hardy is released in April.

My final suggestion: relax a little bit :) we're here to help you out with any problems, and Ubuntu is a lot of fun.   Post back with what you're going to do.

---

### Post by jackdelamare on 2008-03-04
Ok thanks man. I do still have a copy of Ubuntu ISO that I put onto a CD so where are the guides to guide me through the install :)?

I do not want to ruin Vista on my laptop though, you might know that you don't get an install disk for it so if it goes on my laptop then I won't have it unless I pay way too much money.

Anyway... I am now uninstalling Ubuntu from my laptop.

---

### Post by Rocket2DMn on 2008-03-04
Guide: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
By the way, are you really using Ubuntu 5.04?  That is really old, you should be using 7.10 "Gutsy Gibbon".  5.04 is not supported anymore.

---

### Post by jackdelamare on 2008-03-06
No, the version I downloaded onto a blank CD is 7.10... 5.04 is what I had to have to install it using Wubi.
I am now going to follow the instructions and install Ubuntu onto my laptop. The guide says about partitioning... I really hope I don't loose my Vista.

EDIT: I am now on the live CD and am going through the "GParted" program to make my drive smaller so I can install Ubuntu. There is a problem though. I make the free space 10GB and click apply and it says "An error occured while applying the operations". So I cannot make the drive smaller? Weird, because it is 143GB.

---

### Post by Rocket2DMn on 2008-03-06
You should always backup your system before fiddling with partitions.  Although it is rare for something to go technically wrong and ruin your system, it is possible for YOU to make a mistake with the partitioning and overwrite your own data.

---

### Post by Arthur Archnix on 2008-03-06
You should try and jump in here:

[http://ubuntuforums.org/showthread.php?t=715710](http://ubuntuforums.org/showthread.php?t=715710)

---

### Post by jackdelamare on 2008-03-06
Ok I will back my system up but the thing is now, I cannot actually make another partition... what should I do?

---

### Post by Rocket2DMn on 2008-03-06
What do you mean you can't make another partition.  From GParted on the LiveCD (System->Administration->Partition Editor) or using the GParted LiveCD you will need to resize the current windows partition to make room for Ubuntu.  In order to do this, you need to defragment your windows drive first so it will push everything toward the front of the drive, clearing room the resize the partition.  Otherwise it may not let you resize the drive.

---

### Post by jackdelamare on 2008-03-06
I did do a defrag, the same thing happens. "An error occured while applying the operations". Err...?

---

### Post by Rocket2DMn on 2008-03-06
Can you post a screenshot for me (or take a picture of the screen)?  How much space are you trying to give Ubuntu, and how full is your windows drive?  Although it's a pain in the butt, you can try defragging again, some people even suggest up front that you defrag twice, esp. if your drive had moderate to heavy use before you decided to try linux.
Are you using the GParted LiveCD or the Ubuntu LiveCD?

---

### Post by jackdelamare on 2008-03-06
[IMG]http://i89.photobucket.com/albums/k219/jackdelamare/UbuntuPartitionError.jpg[/IMG]

I am giving Ubuntu 10GB on the GParted program, although earlier I tried 20 GB. I am currently on the LiveCD, trying to do the partition thing.

---

### Post by Rocket2DMn on 2008-03-06
I can see in the background of that picture that there are 5 separate partitioned areas, some unallocated (?).  You may be running into problems because it is trying to work with logical partitions as well as physical ones (max physical = 4, I believe).
you can try merging all the unallocated space with the existing partitions so you have 2 ntfs partitions only.  Then you can try to resize your windows one to open up room for Ubuntu (wihch uses 2 partitions minimum = root and swap).  If it doesn't let you, it's probably because the data is too spread out on the disk, and since defragging didn't seem to help, you may not be able to install Ubuntu without starting your dual boot from scratch (or investing in a second hard drive).

---

### Post by jackdelamare on 2008-03-06
No, there is only 5 there because of what I tried to do. When I go onto GParted now, it only shows 2... my main 143GB drive and my other drive which is 5GB... I do not know what it is for though (I think it's hidden and unavailable).

---

### Post by Rocket2DMn on 2008-03-06
OK, well it seems like your drive just doesn't like you very much (this does happen sometimes)
You can try using the GParted LiveCD instead of the Ubuntu LiveCD (or vice versa), but if that doesn't work, you're gonna have to do one of the following:
1) setup a dual boot from scratch by wiping the drive, reinstalling windows, then installing Ubuntu
2) buy a second hard drive to install Ubuntu on for your dual boot
or
3) don't install Ubuntu at this time :(

Let me know which option you want and I can help you through it if you want/need it.  Sorry we haven't been able to get the drive to repartition.

---

### Post by jackdelamare on 2008-03-06
What is GParted LiveCD... would it make a difference. I think we should try this. I have a spare external 20GB hard drive if needed but we'll try GParted first.

---

### Post by Rocket2DMn on 2008-03-06
Yeah, here's the link - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
I've never used it myself, but I hear it's really intuitive and easy to use.  I think it might have a newer version of GParted than the Gutsy LiveCD.

---

### Post by jackdelamare on 2008-03-08
Ok, I booted from the LiveCD of GParted and it began to partition the drive (takes ages, right?). It got about 70% through and I heard a beeping... I realised that my laptop charger was not turned on! I turned it on, heard another beep and then looked over at the cable, realised it wasn't properly plugged into the laptop... managed to get it in and the laptop shut off! I am so angry... among trying to sort out things for my filming which was meant to be tomorrow, I now only have a 5GB drive aswell as a 133GB drive. So it took away 10GB from my 143GB drive and only made a 5GB drive... Ubuntu can run on 6GB and up, so I am so screwed!
Please help, can I deleted the 5GB and make another 10GB (I want to get my 143GB back first) or what?

EDIT: I found that I can grow the 133GB back to 143GB, but it'll take another few hours, so I guess I'll do that whenever I have time.

---

### Post by Arthur Archnix on 2008-03-08
5 GB is lots for me. I usually use around 2.5, but I keep data on a separate partition.

---

### Post by jackdelamare on 2008-03-08
So I can run Ubuntu fully on 5GB?

---

### Post by Arthur Archnix on 2008-03-08
I can run it on less than three, but I only install what I need, and keep my important data on a separate partition. We're talking a default ubuntu install that I then strip down. 

So yes, you can. But if you start installing kubuntu-desktop, and storing things in home, and three word-editors, and compiling from source... you may begin to wish you had 7GB.

Update: I just checked, because I was curious. I'm currently using 2.34 GB, with 985 packages installed.

---

### Post by Rocket2DMn on 2008-03-08
If the partitioning didn't finish, go back and try again, the space is still there, just not accessible until it's formatted properly.  If it broke in the middle of partitioning, you may not even be able to use the drive until it completes (you will have to start the formatting on that partition over again I think).

---

### Post by jackdelamare on 2008-03-08
Thanks for the help guys. What I'll need to do is make the 133GB, 143GB, it gave me the option to increase but it would have taken hours... then I'll make another 10GB one for Ubuntu, then I'll install Ubuntu.

---

### Post by jackdelamare on 2008-03-11
He he, I just received my Ubuntu in the post... nice stickers :).

Listen guys, I don't really have the time to partition anymore drives (it got through once then went through again, 4 hours for the first a 4 for the second, but it was late at night so I had to stop it).

So, is 5GB enough to run the whole of Ubuntu?

---

### Post by Rocket2DMn on 2008-03-11
Yes, you might be a little tight for space if you start adding onto it though.  If you don't mind downloading more stuff, I hear the Ubuntu Minimal install is very nice since it only installs what you need (it downloads almost everything during the install, the cd is just the installer itself) - [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
All in all, it just makes for a smaller installation.  I haven't tried myself, but I plan on it when Hardy is released.

---

### Post by jackdelamare on 2008-03-11
So really, you're saying that I should increase the size? I'll try increasing it to 10GB although it takes AGES!

---

### Post by Rocket2DMn on 2008-03-11
I suppose I should say yes to resizing.  I believe 10GB is what is suggested (though you could make do with less).  Using the minimal CD will give you more breathing room though.
Since it takes so long to resize, let it resize overnight or during the day when you're not there.
As always, have backups of all your data before screwing with partitions!

---

### Post by jackdelamare on 2008-03-14
Ok. I have finally created the spare 10GB but now, again I am stuck and in the risk of loosing my other hard drive, I thought I'd ask again here. Now I have 10GB space on the far right, listed as "Unallocated". Do I right click and create 'New'? If so, please help me with what to put down as that window seems difficult. If "unallocated" is fine as it is, then should I go straight to the Ubuntu LiveCD and begin installing that? I know there is some difficulty on what to select for where you want to install it.

EDIT: I now have 10GB spare which is not "unallocated". I began the Ubuntu setup and selected "Manual". This took me to a "prepare partitions" menu and I clicked on the 10GB one. It now tells me "No root file system is defined... Please correct this from the partitioning menu." What should I do?

EDIT EDIT: Ubuntu installation worked! Yay, everything is working ok now (seems to be). I'm posting from Firefox on Ubuntu, which shows the internet working :).
Thanks for all the help, I really appreciate it!
Now, how would I go about using the desktop graphics? It doesn't let me select them.

EDIT EDIT EDIT: It seems that when I select Windows Vista, it brings up Rescue and Recovery. Please help, how do I run Vista? Vista has not gone, because it is there for selection and it does actually load (green load bar) and this program was actually with it, so what should I do?

---

### Post by Rocket2DMn on 2008-03-14
> **jackdelamare said:**
> EDIT EDIT: Ubuntu installation worked! Yay, everything is working ok now (seems to be). I'm posting from Firefox on Ubuntu, which shows the internet working :).
Thanks for all the help, I really appreciate it!
Now, how would I go about using the desktop graphics? It doesn't let me select them.

EDIT EDIT EDIT: It seems that when I select Windows Vista, it brings up Rescue and Recovery. Please help, how do I run Vista? Vista has not gone, because it is there for selection and it does actually load (green load bar) and this program was actually with it, so what should I do?

I think it's time to start new threads for those problems.  Start a new thread for each topic and people with expertise and experience in those areas will help you out.  Good luck.

---

### Post by jackdelamare on 2008-03-14
Ok, thanks for all of your help! I "thanked" you for all of your work ;).

---

