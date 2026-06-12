---
title: "Old desktop EMachines ET1331G, AMD Athlon(tm) II X2 250u help"
date: 2020-02-09
forum: General Help
---

### Post by frank18 on 2020-02-09
Hi guys i have an old desktop EMachines ET1331G, AMD Athlon(tm) II X2 250u Processor. came with XP  and i want to install a Linux distro that runs good,i tried Xubuntu 18.04 64bit with chromium but on the web pages it enters page fast but when in the pages it takes to long to load next page and when i right text it stalls takes too long to show text ,is this due video card issues or software issues,or is there a better distro i can try on this old PC? thanks

---

### Post by Bashing-om on 2020-02-09
frank18; Hey --

Maybe a matter of ram.
How much ram is installed ?
Be aware i too run xubuntu on old old hardware here; dual core Athlon system and I have no such issues. xubuntu performs admirably with chromium ( though I recently went to slimjet).

[INDENT]my bit to try and help
[/INDENT]

---

### Post by NM5TF on 2020-02-09
@frank18....

we need a little more information....

can you open a terminal and type....post the output in code tags to make it more readable... 

```
inxi -F
```

this will tell us a lot about your machine.....

also...have you looked at Lubuntu which is I believe, a light weight distro based on Ubuntu...

and like Bashing OM, I am using an older machine running a dual core Athlon with less than 4 GB of ram...

I am using Arch Linux mostly these days and have no problems running multiple apps....but I use Firefox
for my browser rather than Chrome....

tommy

---

### Post by mastablasta on 2020-02-10
is this the one?: [https://www.newegg.com/emachines-et1331g-07w-student-home-office/p/N82E16883114092](https://www.newegg.com/emachines-et1331g-07w-student-home-office/p/N82E16883114092)

this PC seems to have enough ram but an on board nvidia chip. luckily it has pcie expansion socket, so you could add a new card. for example GT 1030 will make it run a lot faster and you will also be able to play some games. 

i have an old single core AMD Athlon 64, 4 GB ram and have added GT730 (which is similar card to 1030 but older generation). anyway it can run plenty of windows games up to about 2013. depending on how heavy the graphics are. CS: GO, team fortress 2 work well for the most part, Call of duty 4, Far cry 2, oblivion are only a few old games i played. i have no issues at all surfing the web, doing work, light picture editing etc. later if you decide to upgrade the desktop PC, you can use the same card, as long as it is still supported by their drivers. 

you can also go for equivalent AMD card (not sure but i could be that is radeon 540 or similar). AMD opened it's drivers, so the card will be supported longer by correct drivers.

i went with nvidia, because AMD at the time and for some strange reason didn't work on my PC.

---

### Post by kc1di on 2020-02-10
[QUOTE=NM5TF;13931117]@frank18....

we need a little more information....

can you open a terminal and type....post the output in code tags to make it more readable... 

```
inxi -F
```

He won't be able to run the inxi command unless he installs it first , it is not installed by default. 

Anyway xubuntu should run on that machine if you have a strong enough video card and enough ram.

---

### Post by frank18 on 2020-02-10
[TABLE="class: tborder, width: 100%, align: center"]
[TR]
[/TR]
[TR]
[TD="class: alt2"]Thanks guys ; i had an extra HDD and i did a fresh install of Xubuntu 18.04 and used Firefox  instead of chromium now  it's  OK also disabled Java and it got even better,thanks[/TD]
[/TR]
[TR]
[TD="class: alt2"][IMG]https://www.linuxquestions.org/questions/images/icons/useragent/icon_linuxubuntu.gif[/IMG] [IMG]https://www.linuxquestions.org/questions/images/statusicon/forum_new.gif[/IMG]  [/TD]
[/TR]
[/TABLE]

---

### Post by Bashing-om on 2020-02-10
frank18; Outstanding :)

As this matter is now concluded -
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]it''s 'buntu
[INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT]

---

