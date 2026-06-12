---
title: "How much swap space should i use? (UBUNTU 13.10)"
date: 2014-02-05
forum: General Help
---

### Post by feroz_akbar on 2014-02-05
Hello friends,

I am new to ubuntu, my problem is,

I have a intel dual core system with 2GB Ram and 500 GB harddisk.

And at the time of installing ubuntu 13.10(NOT A DUAL BOOT ONLY SINGLE BOOT) i have used swap space only 200mb (actually i dont know how much to put).

Now whenever i browse firefox with morethan 4 or 5 tabs and any 1 or 2 other applications running in background my computer completely freezes (not only one window), I am not able to do any thing(mouse,key board everything freezes).I have to restart system everytime.

So i want to know is this freezing of computer is because of low(i put only 200mb) Swap space or any other thing? And as i read the system requirements in ubuntu site it says that 


[LIST]
[*]700 MHz processor (about Intel Celeron or better) 
[*]512 MiB RAM (system memory) 
[*]5 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach) 
[*]VGA capable of 1024x768 screen resolution
[/LIST]

is enough for ubuntu.But if comparing my configuration with the above one then definitely my one is higher.So where is the problem? 

Please Help Me? Does increasing SWAP Space solve the freezing completely?

---

### Post by westie457 on 2014-02-05
Welcome to UF.

Your swap is too small. it should be about 2GiB or as much as 4Gib if you want to hibernate your system.

You might also get away with adjusting the 'swappiness. See here for a way to adjust. [http://askubuntu.com/questions/103915/how-do-i-configure-swappiness](http://askubuntu.com/questions/103915/how-do-i-configure-swappiness)

---

### Post by 3rdalbum on 2014-02-05
2 GB of RAM is well and truly enough memory. Even if it wasn't, your computer would not completely lock up; it would just get very, very very slow, but the mouse cursor would still move.

A complete system freeze is usually due to one of two things:

1. Faulty RAM chips
2. A buggy driver (and this is often a graphics card driver).

If you can access the RAM sticks in the computer, I recommend taking one of them out and seeing if that solves the problem. If it doesn't, put it back in and take the other one out. If the computer works fine with one RAM stick, then it's the other RAM stick that is faulty and should be replaced.

If you can't access the RAM sticks in the computer, try running the memory benchmarks in the Phoronix Test Suite. When I had a bad RAM problem I noticed that the memory benchmarks would consistently cause a crash, which was resolved when I replaced that RAM.

There's also the Memtest86+ tool that you can access through GRUB, but this sometimes passes memory that is actually faulty.

If you've exhausted all possibilities of bad RAM, then you might have a driver problem. If you're using a proprietary graphics driver, try using the open-source one. If you're using the open-source graphics driver, try using the proprietary one (if available for your graphics card). If you have loaded any other drivers, try removing or disabling them and see if you still get the problem.

---

### Post by 1clue on 2014-02-05
First, if you have room for it you should look at more memory.  Ideally, you should never hit swap because you ran out of memory.  In my experience 2g is marginal for a full-featured desktop.  Memory is cheap right now, and the best and easiest way to speed up a computer is add RAM when it doesn't have much.

The minimum specs is the smallest amount that the OS can possibly run in, not what makes a useful system.  Figure that you need as much memory as it would take for a modern Windows system and you'll be fine.  In my opinion, that 512m system is for Ubuntu Server, which doesn't even have a GUI.

Second, if you have your system configured to suspend to disk (save the login, power down completely and resume when you restart) then you need a swap partition which is as big as RAM or you'll crash.  You can have multiple partitions, but one of them has to be able to hold all of memory.  That's how the suspend logic works, it writes RAM to one of the swap partitions and then shuts down.  Realistically speaking, that's the biggest requirement of SWAP.

---

### Post by CeejRab on 2014-02-05
200mb of swap space is way way too low... the common forumla is to use twice the size of your installed RAM. so if you have 2gb of ram, (DDR2 i assume), you should use a 4GB swap space. as mentioned above you can adjust swappiness but thats slightly advanced if youre still new to linux, and it doesnt make a huge difference in some instances. you can use gparted to change your swap partition size quite easily...

you should have gparted already, but if you dont here is the apt-get terminal command:

sudo apt-get install gparted

all the best,

---

