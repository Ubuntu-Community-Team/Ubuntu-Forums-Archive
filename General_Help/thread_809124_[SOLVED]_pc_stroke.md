---
title: "[SOLVED] pc stroke"
date: 2008-05-27
forum: General Help
---

### Post by KaliVoid on 2008-05-27
Hi

Two days ago while i was watching a movie clip the pc froze and the keyboard lights started blinking, after restart everything was normal.

Yesterday every time i opened firefox it was immediately closed and the terminal window froze (only those windows were opened).
since i didnt have a web browser to search for the problem i did a restart
,the pc didnt boot and started to show all kind of messages.

all this didnt work :
ubuntu safe mode
the live CDs (7.10 & 8.04)
switched HD with windows on it
new install of ubuntu
(i wanted to plug the ubuntu HD to another pc but idont have one... ;))

so i decide it was a hardware problem and dismantle all the parts cleaning & examine theme .
all the parts seemed ok except for a lot of dust, assembled all the parts back boot the pc and... back in business , all working fine.

the question is what was the problem ?

i attached pictures of some of the error messages taken with a camera.

tnx.

---

### Post by Kevbert on 2008-05-27
It might be worth running the memory test which you get with the grub screen  for a hour or so to see if you get any errors.  Also you say that the PC was full of dust (which can be slightly conductive).  It's worth carefully cleaning this out with Mr Vacuum Cleaner once in a while.  Dust can also clog up your fans and cause overheating.
Hopefully you've cured this with your Spring clean!

---

### Post by KaliVoid on 2008-05-27
oh.. i forgot abut it , i did ran the mem test it gave some errors (in red lines) i only remember that each error line started with "8".

all the dust was removed with an old tooth brush, paint brush & air blow. its shining :)

---

### Post by Kevbert on 2008-05-27
You have a memory problem by the look of it.  With the PC turned off, try refitting the SIM memory chips with care in their motherboard socket (they may be badly fitting).  When you do this make sure that you're touching the metal case to reduce static to a minimum.  The chips are damaged by static.
Now run the memory test again.  If you still get errors, try removing all but one of the memory chips and repeat the test.  That way you'll find the faulty memory by elimination.  Once you've found out which chip it is try fitting it in a different socket (just in case its the socket).
Did you have the PC case earthed when you used the brushes ?  If not you could easily damage other components (by building up a static charge on the brushes.  I [COLOR="Red"]would not[/COLOR] recommend using brushes on computer PCBs.

---

### Post by KaliVoid on 2008-05-28
yes , the pc was earthed and i did put back the mem cards in different slots i guess thats why its working again.

i ran a second mem test for 5 and a half hours, it didnt finish but there was no errors .

i think its safe to say that it really was a memory (hardware) problem.

thanks for all the advices (if you have anything to add feel free :)).

---

