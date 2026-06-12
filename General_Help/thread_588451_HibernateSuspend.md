---
title: "Hibernate/Suspend"
date: 2007-10-23
forum: General Help
---

### Post by anotherdisciple on 2007-10-23
I realize that this type of problem has been posted a million times, but I can't find any real working answers! I am running gutsy on a dell inspiron e1505 with an ATI mobility radeon x1400. I have a 2.4 Gig swap partition and every time I click suspend or hibernate... the screen goes black (still lit and on.. just black... not like the screen is turned off) and I am unable to wake it!

I love Ubuntu... and I"m a complete newbie. Any help would be much appreciated... Even if it's some wierd work-around.

---

### Post by #Reistlehr- on 2007-10-23
99% of the time, from tests i have done, it had to do with my wireless card. When i disabled the card, and ndiswrapper wasnt loaded as a module, suspend/hibernate worked better.

But, i still have not discovered or read a 100% working fix for this, but it's the only thing i need to get my HP dv9000z working 100% perfectly.

---

### Post by groovomata on 2007-10-23
> **anotherdisciple said:**
> I realize that this type of problem has been posted a million times, but I can't find any real working answers! I am running gutsy on a dell inspiron e1505 with an ATI mobility radeon x1400. I have a 2.4 Gig swap partition and every time I click suspend or hibernate... the screen goes black (still lit and on.. just black... not like the screen is turned off) and I am unable to wake it!

I love Ubuntu... and I"m a complete newbie. Any help would be much appreciated... Even if it's some wierd work-around.
Hmmm I have a Dell Inspiron 1505 as well, though with an nvidia graphics card and I have no problem with hibernate, suspend though is a different matter as I can't seem to wake it up again. I'm going to check the Dell site and see if there's anything on that and post back.
Erik.

---

### Post by groovomata on 2007-10-23
> **anotherdisciple said:**
> I realize that this type of problem has been posted a million times, but I can't find any real working answers! I am running gutsy on a dell inspiron e1505 with an ATI mobility radeon x1400. I have a 2.4 Gig swap partition and every time I click suspend or hibernate... the screen goes black (still lit and on.. just black... not like the screen is turned off) and I am unable to wake it!

I love Ubuntu... and I"m a complete newbie. Any help would be much appreciated... Even if it's some wierd work-around.

Hey, check out your laptop on this page and see if there's anything there for you:
[https://wiki.ubuntu.com/LaptopTestingTeam/Dell](https://wiki.ubuntu.com/LaptopTestingTeam/Dell)

Good luck,
Erik.

---

### Post by anotherdisciple on 2007-10-24
I'll try the wireless thing tonight. What is ndsiwrapper and how can I fix it? I've heard a number of people talk about fixing problems with it, but I don't know how to get to it or work with it!?!? 

By the way... I've been running linux for about a month now and I've only used windows once on my computer in that time period. I'm pretty sure that I'm getting rid of windows soon... haha! All I need is this dang suspend/hibernate thing to work! GNU/Linux does everything that windows does... plus some better stuff. I'm trying to stick to as much open-source stuff as possible too. There are some things that you just can't seem to avoid though... like 3d graphics don't do so good with the open source drivers. Bummer... I'm hoping it gets better in the future so I can switch to an open-source. 

I'm loving Ubuntu... I am going to read up on how to do more technical stuff though... do you suggest any books that teach all the important stuff? Mostly how to create deb packages, how to be more familiar with doing things in the terminal, how to create scripts, etc.

---

### Post by groovomata on 2007-10-27
Try going to System > Administration > Restricted Drivers Management, when you are plugged in to your internet by cable. You probably need to enable ubuntu to fetch some firmware to be able to use your wireless card. Give it a try and post back.
Erik.

---

### Post by anotherdisciple on 2007-10-27
I have the restricted driver turned on. I heard that sometimes it has to do with the wireless card though. If I hit Fn+F2 it turns off my wireless card... I tried that before I hit suspend.. and it didn't help... bummer. I have an Intel PRO/Wireless 3945 if that helps.

---

### Post by anotherdisciple on 2007-11-30
Anyone else know about this?

---

