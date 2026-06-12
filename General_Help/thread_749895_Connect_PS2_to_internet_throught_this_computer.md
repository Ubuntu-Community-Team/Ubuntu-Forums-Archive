---
title: "Connect PS2 to internet throught this computer"
date: 2008-04-08
forum: General Help
---

### Post by doorknob60 on 2008-04-08
Well, I'm considering buying a network adapter for my PS2 (Burnout onlinne :D), but my PS2 is nowhere near my router. But, it's right next to my computer, currently running Hardy, connected wirelessly, and has an unused ethernet port. What I want to know is would it be possible to connect the PS2 online through my wireless connection on here, would I need any extra equipment besides a regular ethernet cable, and how would I go about setting up Ubuntu to handle this? Also, would this slow down my computer at all? If it matters, my wireless is ath0 and my ethernet port is eth0. If this is in the wrong board, please move it, thanks!

---

### Post by doorknob60 on 2008-04-09
Bumpity bump! Well, I know it's possible, but how would I go about it?

---

### Post by louistan3 on 2008-04-09
im not sure as ive never done what your describing before.. but i think one way would be to make a dhcp server off of your desktop then your computer should act like a router and would just relay packets through..

but maybe someone else here has a better a idea.. maybe an easier one.. hehe

hope that helps.

---

### Post by doorknob60 on 2008-04-09
Sounds like it might work, but I have no clue how to do it, can any one tell me how or show me a guide on how to or something?

EDIT: Getting off for tonight, I'll check back tomorrow.

---

### Post by MrFSL on 2008-04-09
First off you will need a crossover ethernet cable not a (regular straight through ethernet cable) to connect the PS to the Computer. Next you would setup static internet settings on the computer and the ps2.

Finally install firestarter (Linux frontend for firewall)
```
sudo apt-get install firestarter
```

And use the ICS settings to share the connection.

---

### Post by doorknob60 on 2008-04-28
Thanks, I'll look into that when I have the money to buy the network adapter :)

---

