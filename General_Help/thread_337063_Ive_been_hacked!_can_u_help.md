---
title: "Ive been hacked! can u help?"
date: 2007-01-12
forum: General Help
---

### Post by tom1979 on 2007-01-12
Ok to cut a long story short, my hotmail account was taken over, and the guy who did it has been using it to close other web based acounts.

ive noticed 2 days later that the mouse keys on my thinkpad werent working properly in xp. the bottom left key acted like the right key, and caused screen glitches, and the top set of keys were fine.

i was then unable to acces internet at all on the laptop. he was in contact with a contact of mine who hacks too, and my contact advised hes too good and they cant help.

now when i reboot into ubuntu i still cant go online at all, ive tried after destroying the windows partition too. also the bottom left mouse key still appears to not be working correctly. 

now i dont want anyone to hack the guy who hacked me, but i want to know if you can help find the problem in linux and rectify it. i started using linux as it was said to be more stable and less hackable, i now need this proving to me!

obviously the alternative is to reformat, which i will do tomorow if needbe.

ps please only respond here as i dont want email notifications going to the hacked msn account untill ive edited my profile! thnx a lot. 
(hacked off)tom

---

### Post by Iarwain ben-adar on 2007-01-12
Hiya,

When you reboot in ubuntu,
there is practically NO WAY he could still "control" your pc...

I just think your internet isn't correctly configured, and your mouse might have died.


Iarwain

---

### Post by tom1979 on 2007-01-12
yes my mistake im back online in ubuntu now... but the mouse key only plays up when the network cards in. so i dont think its a dodgy key.

---

### Post by ZylGadis on 2007-01-12
It is practically impossible that your Ubuntu partition has been hacked, except in the following cases:

1. You ran some binary or .deb someone gave you, and you provided your root/sudo password when it asked for it.
2. You are running Ubuntu on top of Windows in a virtual machine.
3. (Obvious) you have personally allowed somebody access to an account on your machine.

If none of that is true, your personal machine is fine. There may be other things he is trying to do to you - flood your network from the outside, for example - but your machine is completely fine. Don't panic :)

---

### Post by tom1979 on 2007-01-12
well thats very reassuring to know. i had been using xp more than i intended with the dual boot, but this time i think ill stick to ubuntu. im formating now and starting again with a fresh install. hopefully the mouse keys will go back to normal!

on this subject can u recomend a good firewall and antivirus (if there is any) for ubuntu just to be on the safe side?

---

### Post by tagra123 on 2007-01-12
iptables is firewalling your computer from the first login.  ITs part of the install.

If you want an easy to use interface to iptables -- try firestarter -- its in the universe repos.

sudo apt-get install firestarter  from a terminal.

I have a virus scanner on my linux machine just to protect the windows users I deal with.

I think there are only like 2 or 3 known linux viruses and you have to be very careless -- giving a "bad" program root privileges.


I think your friend is pulling your leg:)

---

