---
title: "Canno't Boot into 7.10!"
date: 2007-10-21
forum: General Help
---

### Post by UltraM4n on 2007-10-21
Hello folks.
Just recently burned the new 7.10
As usual, Regular boot doesent work because of some X server error. So i try safe graphics
...and this fails.
After a while of my screen flashing on and off, i come to a screen that says it tried something with the monitor over 6 times and will try again. something wrong please wait 2 mins..
Does this over and over...

Anybody help?

---

### Post by UltraM4n on 2007-10-21
bump

---

### Post by UltraM4n on 2007-10-21
please help me

---

### Post by UltraM4n on 2007-10-21
Sorry for triple post, but i want some help! :confused:

---

### Post by jrharvey on 2007-10-21
does it give you an option to manually configure your xserver?? I got a black screen when i first tried to install but it doesnt sound like this is the same problem. Does it give you an error message??

---

### Post by jrharvey on 2007-10-21
Is this from the Live CD or after the install?????

---

### Post by UltraM4n on 2007-10-22
> **jrharvey said:**
> Is this from the Live CD or after the install?????

live cd.

BTW, i've always had problems doing a regular boot into ubuntu. I always have to do a safe gfx boot.
My GFX card is an ATi x1300.

---

### Post by jrharvey on 2007-10-22
Ok now that you have replied try this (its what helped me). Start to boot the cd and at the menu that ask you to (start ubuntu, start ubuntu in safe mode......etc......). Highlight the START UBUNTU and do not press enter. Press F6 and it will give you a line of text at the bottom. Erase "QUIET" and add "NO SPLASH" This worked for me. For some reason with the video card I have the live cd would always freeze when going through the booting process. I hope this works for you. There are many reasons why gutsy wont boot but this is what fixed my problem. Please tell me how it goes.

---

### Post by UltraM4n on 2007-10-22
> **jrharvey said:**
> Ok now that you have replied try this (its what helped me). Start to boot the cd and at the menu that ask you to (start ubuntu, start ubuntu in safe mode......etc......). Highlight the START UBUNTU and do not press enter. Press F6 and it will give you a line of text at the bottom. Erase "QUIET" and add "NO SPLASH" This worked for me. For some reason with the video card I have the live cd would always freeze when going through the booting process. I hope this works for you. There are many reasons why gutsy wont boot but this is what fixed my problem. Please tell me how it goes.

Thanks alot!
is NO SPLASH one word?

---

### Post by jrharvey on 2007-10-22
Oh yess!!!! you are right, sorry. NOSPLASH is what you should type

---

### Post by UltraM4n on 2007-10-22
> **jrharvey said:**
> Oh yess!!!! you are right, sorry. NOSPLASH is what you should type

Thanks!
Going to try it now..hope it works!

---

### Post by jrharvey on 2007-10-22
Ok good luck.

---

### Post by UltraM4n on 2007-10-22
> **jrharvey said:**
> Ok good luck.

AGH!
Still didnt work.
Got the same X server error.
It mentioned something about uh...error on line 41...um..
Also, when i do a safe gfx boot, it will stay at this one spot right after Running local scripts..
and the screen will flash for a bit.. then sometimes it will say too much work for irq7.

---

### Post by jrharvey on 2007-10-22
My roomate has an ATI card and we had to use the alternate cd. Try to download the ISO of the alternate cd. How much memmory do you have on your computer???

---

### Post by jrharvey on 2007-10-22
Ok just like my roomate, it seems that alot of people have the same problem with Gutsy and ATI cards. You have to install from the alternate CD and then configure your xserver from there. You will have to configure it after install but with gutsy it is alot easier than fiesty so you should not have a problem (hopefully)

---

### Post by UltraM4n on 2007-10-22
> **jrharvey said:**
> Ok just like my roomate, it seems that alot of people have the same problem with Gutsy and ATI cards. You have to install from the alternate CD and then configure your xserver from there. You will have to configure it after install but with gutsy it is alot easier than fiesty so you should not have a problem (hopefully)

Thing is, i really didn't want to install it : S
I just wanted to try out the livecd...
And i'm not very linux savvy...

Also i have 2 gigs of ram.

---

### Post by jrharvey on 2007-10-22
Ok well I can totally understand why you would want to use the live cd and try it out but for this post it may be beyond my knowledge. I really wish someone else that has more experience with ATI cards would jump in here. I truly think it would install fine and work fine with the alternate cd but I can understand your desicion. I can say that it is alot like fiesty but waaaaay better. Yes there are some bugs like the one you are having but once you get past those, Gutsy is overall a great OS.

---

### Post by UltraM4n on 2007-10-22
> **jrharvey said:**
> Ok well I can totally understand why you would want to use the live cd and try it out but for this post it may be beyond my knowledge. I really wish someone else that has more experience with ATI cards would jump in here. I truly think it would install fine and work fine with the alternate cd but I can understand your desicion. I can say that it is alot like fiesty but waaaaay better. Yes there are some bugs like the one you are having but once you get past those, Gutsy is overall a great OS.

Alright well i suppose i will take the plunge.
the iso is downloading as we speak, tell me what i need to do.
My current OS is Vista ultimate, and I have  an un-used corrupt xp partition... Its about 20 gigs... Gonna copy some stuff over to my external. So, what do i do?

---

### Post by jrharvey on 2007-10-22
I would just format over the 20Gig XP partition. The alternate CD will be in text mode instead of a pretty GUI but if you have ever installed XP then it is kinda like that. Just select the partition you want to overwrite. Make sure you do not select the option to use the whole disk as that would destroy your vista partition and this could be bad. Afterwards it will just ask you a crapload of questions and jsut follow the dirretions. If you know a little about computers then it should be farely straight forward. 

Before you do this check out WUBI 7.04. I havnt used this yet but appearantly it lets you use windows to install any ubuntu on your windows partition withought having to repartition the disk. I am testing it as we speak so if it works it could be an option for you if all you want to do is try it out. If you are searious about trying out ubuntu then just install the alternate CD. I have used both Windows and OS X and I would always choose ubuntu over both.

---

### Post by superyounan1 on 2007-10-22
if you just want to play with the live cd for now and your motherboard has on-board video, shutdown your computer and unplug yoru video card, use the onboard one.

Its far less drastic than install ubuntu, you might loose all your data

---

### Post by jrharvey on 2007-10-22
Oh yes I didnt even think about that, DUHHHH. You do not have to unplug it and I wouldnt recomend it. Just switch your primary card in your bios. That is if you have an onboard card. It may be that you are using a laptop or the ATI is stock on your machine. I dont know but if you have an onboard card then use it to test the cd.

---

### Post by superyounan1 on 2007-10-22
> **jrharvey said:**
> You do not have to unplug it and I wouldnt recomend it. Just switch your primary card in your bios.

with some motherboards the linux kernel tries to use the dedicated graphics despite disabling it in the bios, it happened to me and was a source for a lot of confusion.

But its a good place to start, change the video device in your bios, if it doesn't change anything with respect to the live cd's boot, then try physically unplugging it

---

### Post by jrharvey on 2007-10-22
Once again you have a very good point. I forgot that this happened to me in gutsy. Even if I had my onboard card seleted then Gutsy would still use my nvidia card. I would try the bios first and if that does not work then you could unplug it. I just hate messing with hardware all the time because if you brake it then it is broke for good.

---

