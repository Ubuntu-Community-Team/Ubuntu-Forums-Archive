---
title: "Fine tuning performance of Ubuntu (Wine?) tips, tricks and info"
date: 2012-12-28
forum: General Help
---

### Post by Nikolai D. on 2012-12-28
Hi there, guys and girls,

I have just upgraded 10.04 to 12.04 on my MacMini 2.1. The spec are: 4gb ram, c2d cpu, ssd disk and intel GMA945 gfx. And i play D2 on it via PlayOnLinux.

The spec are not the super latest and fastest. But it should be quite ok for 12.04 imho right? I already had Lion, Win8 and some 11.xx Ubuntu and i saw that Win8 was kinda laggy so i downgraded the whole setup to: Snow Leopard, XP and 10.04. But that would not mean that Ubuntu is even laggy as Win7 right? Basically the look and feel and the overall working seems quite ok to me. This is just Wine that is kinda more laggy with 12.04 then with 10.04. I can even startup an XP virtual machine in VirtualBox and start D2 there and play it wothout any lag. So its not like theres not enough resources.

I have already learned that its not always best idea to run the latest and greatest software versions. Sometimes the hardware and the software are not quite compatible anymore. And you should better run somewhat earlier version of the software. So if theres nothing to do about it. Ill just reinstall 10.04 again. Or try some Fuduntu or something. :)

But what i was wondering. If there is any fine tuning that is possible. To the whole Ubuntu installation and/or Wine related fine tuning. That could speedup working of Wine somehow. Or is maybe crossover performing any better? So im willing to learn quite a bit more about system working and Fine tuning of it. If you have any resources to read on about it. Just tell me. Links / suggestions are appreciated. 

I have already found some tips. And have installed the preload thing. And changed the swappiness to 10. Is there any other interesting tweaks / lectures on this topic? Why i think i can be kind of more related to Wine itself. Is because i have already installed Xfce, Lxde, etc. And yes the GUI is somewhat snappier if i use them. But D2 in Wine stays still somewhat alggier. Same way as it is with Unity. So its not the Unity issue. Or is thee something with the v3 kernel which is to fat for my 4mb cpu cache?

p.s. I am actually pretty willing to learn more about the working / fine tuning of the system. Even to the point of learning to create my own fine tuned distro eventually.

Thanks in advance,
Waiting for the suggestions, tips, etc,

Nikolai

---

### Post by Pjotr123 on 2012-12-28
You might optimize your SSD like this:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

General speed tips:
[https://sites.google.com/site/easylinuxtipsproject/speed](https://sites.google.com/site/easylinuxtipsproject/speed)

Good luck! :)

---

### Post by Nikolai D. on 2012-12-28
thank you for fast response,
i have tried quite a view of the tips from the links,
like changing swappiness. Installing BFS kernel and preload.
Nothing helpes. Ubuntu 12.04 on itself works ok.
Only Wine stays sluggish. Any suggestions on tuning/fixing Wine? 
Also posted here:
[http://forum.winehq.org/viewforum.php?f=8](http://forum.winehq.org/viewforum.php?f=8)
thanks in advance,
Nikolai

---

### Post by Mark Phelps on 2012-12-29
You can always check the Wine support forums at the WineHQ site -- but I suspect there will be little or nothing you can do.  Wine is a kludge at best, and the fact that it even works, is nothing short of amazing.

If you're trying to use Wine to run games, it could be that your video card and/or drivers aren't up to the demands needed by the games.  If that is true, apart from replacing the card, there is nothing you could do to improve performance.

---

