---
title: "New to (x)ubuntu questions :) (already read many posts)"
date: 2016-03-31
forum: General Help
---

### Post by max141 on 2016-03-31
Hello community !  :)

[TellingMyLife]
I am a windows user very curious about linux, open-source, privacy worlds, also a gamer and student.

I have already been in touch with ubuntu about 3 or 4 years ago, but i only tested it on live session.

Because at that time, i really needed Microsoft Office for my studies and it seemed to me that gaming was difficult on Linux.

But now, i am about getting graduated and saw that steam is on linux with some games ported to linux.

I have 2 laptops, one fairly new MSI GT60 with W10 and the previous one, an Acer ASPIRE 5750G.

So, to make the transition easy, for now, i want to keep W10 on the MSI and get a linux OS on the Acer.

I already chose what will be my first linux distribution: Xubuntu :)

I installed it and tried some stuff, i think i messed up the system so i am about to create a fresh new installation.

But during this first experience with Xubuntu 14.04 LTS i faced some issues... :-?


So (finally), here are my questions :

 1.

The Acer ASPIRE 5750G has an Nvidia GT540m graphic card with the optimus technology.

By default, Xubuntu is using the Nouveau open-source driver. This one makes a good job for all the stuffs i am doing on my computer.

BUT i tested CounterStrike Global Offensive on it, and it's unplayable in game. On menus and spectator mode, i have good fps but in game it's really bad, about 10 fps...

So i read many posts and tried many Nvidia proprietary drivers but it's still the same.

I learned about the issue of Optimus technology on linux. And found out about Bumbleblee/Prime.

In every tuto i found, they all say, the graphic card driver depends on the computer you are using.

But i don't know... Which one should i use ?

On the official nvidia site, they say that the proper driver for the GT540m on linux is the 361.42.

On Xubuntu 14.04 LTS, on additional drivers, the latest one is the 352.XX (tested).

With all the posts i read, some say dont get your driver on the nvidia site use the ones in additional drivers, some say get your driver on nvidia site, and bumbleblee related posts dont help about which driver to use...

And i switched to the 352.XX to give it a try but when i rebooted, blackscreen after the xubuntu splash :/

-
[FONT=comic sans ms]
[/FONT]2.

On a fresh installation of Xubuntu 14.04 LTS, there are many programs which i dont use...

I removed some. But for some, when i tried to remove them, a pop-up told me that it needs to delete some other program/additional libraries to remove it. So i didnt.

What are the programs i can remove without causing any trouble on a fresh Xubuntu 14.04 LTS installation ?

-

I am sorry for my bad english, english isnt my first language.

And thanks to people who had the courage to read this novel xD

---

### Post by grahammechanical on 2016-03-31
Nvidia 361 is just about the latest Linux Nvidia driver (very latest is 364) and I do not think that either is available in Ubuntu 14.04 unless we have gone to System Settings>Software & Updates>Updates tab and ticked the box Proprietary drivers for devices (Restricted). I do not think that repository is enabled by default. If that box is ticked you may get an updated Nvidia driver. Maybe 361 but only maybe. Maybe not.

Alternatively, you should upgrade to Ubuntu 16.04 when it is released at the end of April. Ubuntu 16.04 will come with the Nvidia 361 driver. The reason why we get new versions of Ubuntu every six months is to get newer Linux kernels and hardware driver modules and newer proprietary drivers to keep up to date with newer hardware.

Another thing that you need to know. Nvidia does not produce a Linux driver that automatically switches between the Intel graphic adapter and the Nvidia adapter in the way that the Nvidia drivers do on Windows. You have to make the switch in the Nvidia settings utility. Sorry, but that is life.

Regards.

---

### Post by max141 on 2016-03-31
Thanks for your answer Grahammechanical ! :D

I will tick that box in proprietary drivers for devices and see if i get an update !

Yes i know that the switch isnt avaible by default between Intel graphics and Nvidia... Yeah that's life, unlucky/sad life ahah :p[[COLOR=#000000][/COLOR][COLOR=#000000][/COLOR]]("http://fdsg")[FONT=comic sans ms][/FONT]

---

