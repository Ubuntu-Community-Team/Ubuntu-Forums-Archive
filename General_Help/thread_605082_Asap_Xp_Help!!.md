---
title: "Asap Xp Help!!"
date: 2007-11-06
forum: General Help
---

### Post by Attila2452 on 2007-11-06
i installed ubuntu a coulpe of days ago and its been working fine but when i updated my system, there was some kind of error! when it told me to re boot, i did  and since i have XP as a primary OS it went th there because it first goes to the (select a OS then waits for 15 secs for a response and if nothing then it goes to XP and since i did nothing, i was doing homework and was buisy so i forgot about it for a bit and it went to load Windows Microsoft XP (loading page) then it stopped and rebooted by its self! im really scared because i have no back up CD's or anything! i still have my files wor windows on my ubuntu acer folder and i can assess the folder and the contense but i cant do anythign with it. i dont know what to do. i was thinking of uninstalling ubuntu ... but i was on it and cant get on XP and if i uninstall it then i will ave no COMPUTER so thats out of the question. my sister is gonna kill me (she bought the computer) i really need all the help i can get to get XP back! 

PLSEAS RELPY!

---

### Post by ohzopants on 2007-11-06
Your post is a bit unclear... panic I guess (been there, done that).

What kind of error caused this? Random reboot?
Can you boot into ubuntu?
If so, can you access your windows partition from ubuntu? (What's an "ubuntu acer folder"? and what do you mean you can't do anything with it?)

---

### Post by Attila2452 on 2007-11-07
ok it was from an ubutnu update and it told me to reboot.

i rebooted and then my comp automatically went  to XP and after trying to load XP ot rebooted by its self in the middle of loading! 

then i tried getting on XP a few more times but it just kelp re-booting.

acer is the computer xompany i use. and its a folder on my ubutnu its to acess all of my files on my XP its weird. i can acces the folser but i get on XP do you get what i mean?

and i can get onto ubutnu i just want my XP working because if not my sis is gonna KILL me!!!

please reeply .. again and if you have any more questions.


 - Attila Hajzer -

---

### Post by ohzopants on 2007-11-07
You should try rebooting windows into safe mode (you have to hit f8 while booting to get the menu from which you can select safe mode).

You could also try running fsck.vfat to check for errors on the drive (type man fsck.vfat for more info, I'm not an fsck pro).  You can check a mounted drive, but you cannot repair one.  If it finds errors you will need to unmount before repairing them.

---

