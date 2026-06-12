---
title: "Trying to get my mother to use Linux"
date: 2007-09-03
forum: General Help
---

### Post by PmDematagoda on 2007-09-03
As you can say from my Thread title I'm trying to get my mother to use Linux, but I'm hindered by the fact that two programs she needs as an engineer, STAAD.Pro and Prokon don't work. Does anyone know how to make these programs work or any alternatives to them?

---

### Post by aitorcalero on 2007-09-03
You can use a windows virtual machine with QEMU, VMWare or VirtualBox, and install those programs there.
Also you can try to make it run through WINE

---

### Post by mckryptyk on 2007-09-03
I don't know what your mother's computer specs are but it might be possible to run these programs in a virtual machine for her. 
If done correctly, it should be "near seamless" for her to use them. 
Post back if you would like, as I would like to help with this.

Cheers.

Edit: Drat! beaten to the post. (I spend too much time formatting my posts :) )

---

### Post by PmDematagoda on 2007-09-03
> mckryptyk:-

Edit: Drat! beaten to the post. (I spend too much time formatting my posts  )

Don't worry I read and acknowledge everyone who helps me.:)

Anyway my mother has a Compaq laptop with the following specs:-

1.6 Ghz Intel Core 2Duo T2050 
128 integrated Intel VGA card(Not sure about model)
512Mb DDR2 RAM
80 GB(Don't know if SATA or PATA)

Is this enough to run a virtual machine properly?

P.S. STAAD.Pro uses up a lot of power when it's analysing a drawing which my mother does a lot.

---

### Post by mckryptyk on 2007-09-03
Honestly, I think due to the lack of ram and the fact that you say the program uses a lot of ram, I don't think it will run "smoothly". 

Is it possible to run the program from a lesser Windows version ? 
Perhaps a Windows version less than XP ?

I'm not very familiar with her ( your mom's)  particular programs, but I think if the minimum requirements for the programs she uses were posted, we could figure out what options were available.

Right now, My best bet is on a virtual machine because I do not know how well wine would work with her programs. (Perhaps you could investigate further with this ?)

Cheers.

---

### Post by anaconda on 2007-09-03
Well. I am running XP virtual machine with vmware in my machine, which has just 512Mb of ram, and it works very well. 

If the program you want to run in VM is heavy in CPU it is not a problem. on the other hand great usage of RAM might be a problem.  and if it needs lots from the graphics card that can also be a problem. 

Try it and you will be wiser.

---

### Post by PmDematagoda on 2007-09-03
Well according to specs STAAD.Pro requires about 256Mb RAM, the program is not heavy graphic wise because it uses mathematics and calculations for the analysis. Prokon won't have much of a problem but it's STAAD.Pro that concerns me since she uses it a lot.

---

### Post by mckryptyk on 2007-09-03
You most definitely could be able to run programs within a virtual machine, if you were able to upgrade her RAM. (It should be cheap if you shop around)

The most performance friendly way to run them would be through wine, however I think the programmers may have attempted shortcuts while coding in order to improve realtime performance.

This has always been a problem for wine, as they are only implementing API's according to clean-room spec, this makes it very difficult to make everything work, all the time.

I would like to hear that wine works for the programs, though I doubt it due to their complexity.

Try the virtual machines (I recommend Vmware and Virtual box, in no particular order) anyways and let me know, performance-wise how it went.

Just make sure, you do not lose any of her saved data, as this is the most important thing to Windows users. (next to usability)

Cheers.

---

### Post by insane_alien on 2007-09-03
i think in this situation a wondows partition should be retained. the engineering apps i use do not function very well under a virtual machine no matter how much RAM i throw at it. it doesn't need to be big, just enough to cover the OS, programs and probably large data files she'll be working with.

---

### Post by mckryptyk on 2007-09-03
It is possible to use a "cut-down" version of a Windows distribution. (Nlite, etc.)

For example, there is a version of XP available that takes 50 - 75 MB of RAM fully loaded.

This is not counting any installed programs or drivers.

People are using it as a gaming version due to the increased performance they see from it since it uses less RAM.

Cheers.

---

### Post by Spam Banjo on 2007-09-03
Hahaha! My mother has been using Ubuntu on a daily basis longer than I have!!!

She was given an old sucky machine with Windows ME installed. It ran like crap... she used it for a few weeks and lost her temper with it too many times to count. I tried Ubuntu to give the old beast some new life... It worked like a charm!!

She now has my old Pentuim 4 Dell Optiplex, all Ubuntu'd up with Beryl & Emerald running and she loves it.

My mom is nearly 60!!!

---

### Post by PmDematagoda on 2007-09-05
Thanks everyone for your help, sorry for the absence I had a lot of school work to do these past 2 days. I will give Nlite a try and tell you how it went, the thing is it will have to be done this weekend when my mother is doing the least amount of work. And you are right my mother is very concerned about the data she has.:):) 

Sorry I kept you guys waiting.

---

### Post by PmDematagoda on 2007-09-14
Sorry for the late reply, I've had some problems with my own Ubuntu. About my mother, I think it might take some time for her to get warmed up to it atleast until Linux gets some good engineering software like TAAD.Pro and Prokon. The thing is my mother was really impressed by the GUI of Linux and the fact that it's free, but the fact that her necessary programs weren't available made her forget about Linux.

The fact is my mother is really busy with her work and she doesn't have time to configure and operate Linux. 

Really sorry about that. But not to worry, I'll keep at it and maybe someday my mother will switch to Linux.:)

---

### Post by Spam Banjo on 2007-09-14
I forgot to mention my mom only uses the machine for Email, MSN, Web, Music... she's a typical home user. I think providing you are only a home user, and you have means of hard wiring into your router, then there will be no problems at all.

It's a shame to hear about your mom missing the opportunity this time.

Did you try running her apps under wine? I have Dreamweaver and Flash running better under Ubuntu than they ever did under windows XP

---

### Post by PmDematagoda on 2007-09-14
No problem Spam Banjo, the thing is my mother would have definitely loved Ubuntu if she only used it to do basic stuff, but the thing is that my mother uses her laptop for more things than just basic stuff.

The thing about wine, I didn't install Ubuntu in my mothers laptop because there is only one hard drive on it an 80 Gb, but it's used almost to full capacity with stuff my mom needs for her work, so she doesn't want to risk losing her valuable data. Of course she could get another hard drive but once again my mother doesn't have the time to do that. 

I most probably would have installed Ubuntu over XP if I knew that Prokon and STAAD.Pro could be run as well either through wine or as a Linux version. Most probably I'll check them out on my own system, but as I'm going to install the 64bit version of Feisty, would wine be able to emulate 32bit apps that well?

---

