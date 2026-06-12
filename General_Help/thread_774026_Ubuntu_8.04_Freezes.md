---
title: "Ubuntu 8.04 Freezes"
date: 2008-04-29
forum: General Help
---

### Post by henrywm on 2008-04-29
My copy of Ubuntu 8.04 keeps freezing, and I am forced to do a hard shutdown. No other version of Ubuntu that I have tried has frozen this often. Even my Windows computers do not freeze this often. Any advice?

---

### Post by hermes0710 on 2008-04-29
Seems to be a graphics card problem but you must provide more info. What is the model? 
Try killing the gdm before it starts and log in to the console in order to see the log of the X (/var/log/Xorg.0.log). Post its contents here

---

### Post by milind4 on 2008-04-29
I also get this problem. I've installed Hardy Heron with wubi inside Windows Vista. I've got an AMD Athlon 64 X2 Dual Core 4200+ processor, 1 GB ram, and a Nvidia GeForce 6150 le graphics card.

What happens is that sometimes, Uuntu will just freeze. It has always happened within one minute of the dektop coming up. The first time it happened, the keyboard seemed to lose power. Pressing keys would not give any response. The mouse would not move, but the red light was still shining on its backside.

The next few times, the mouse was the same as before, and the keyboard would not respond. However, the keyboard's caps lock and scroll lock indication lights would blink (one second on, one second off). They would blink together.

Please help me fix this problem! Also, this has not occurred  every single time I boot Ubuntu, but when it does the only was to turn it off is to press the power button. As the OS has been installed with Wubi, and it says that hard restarting might corrupt the hard drive, I'm cautious of even booting up Ubuntu now..

---

### Post by Nunu on 2008-04-29
> **milind4 said:**
> I also get this problem. I've installed Hardy Heron with wubi inside Windows Vista. I've got an AMD Athlon 64 X2 Dual Core 4200+ processor, 1 GB ram, and a Nvidia GeForce 6150 le graphics card.

What happens is that sometimes, Uuntu will just freeze. It has always happened within one minute of the dektop coming up. The first time it happened, the keyboard seemed to lose power. Pressing keys would not give any response. The mouse would not move, but the red light was still shining on its backside.

The next few times, the mouse was the same as before, and the keyboard would not respond. However, the keyboard's caps lock and scroll lock indication lights would blink (one second on, one second off). They would blink together.

Please help me fix this problem! Also, this has not occurred  every single time I boot Ubuntu, but when it does the only was to turn it off is to press the power button. As the OS has been installed with Wubi, and it says that hard restarting might corrupt the hard drive, I'm cautious of even booting up Ubuntu now..

Is this the first time you using Ubuntu, I am just curious because a few people have complained about 8.04 freezing up. Apparently this has something to do with the kernel, I also have an Nvidia card and my machine is working perfectly. I have had no issues what so ever since upgrading to 8.04

---

### Post by hermes0710 on 2008-04-29
Guys is this an AGP or PCI Express card?

---

### Post by milind4 on 2008-04-29
yes, this is my first time actually installing ubuntu. is it a problem with the graphics card then?

---

### Post by Nunu on 2008-04-29
> **hermes0710 said:**
> Guys is this an AGP or PCI Express card?

I have AGP and like i said no problems, Good question though is there any one suffering with this issue using AGP, or is it isolated to PCI Express?

---

### Post by hermes0710 on 2008-04-29
> **Nunu said:**
> I have AGP and like i said no problems, Good question though is there any one suffering with this issue using AGP, or is it isolated to PCI Express?

When i had an AGP nvidia card i had similar problems but that was due to faulty configuration of xorg.conf (the NvAGP option i think was not set) but with the right configuration everything went smooth. Check your drivers details and options

---

### Post by Tatty on 2008-04-29
I am also having freezes on a laptop with a Nvidia Go 6100 card on a PCI Express bus.  

Not sure if this is the same bug though as mine freezes only if left inactive for a while.  The cursor moves but nothing else appears to, however pressing the power button does bring up the shutdown dialog, and if i press cancel i get control back.

Sometimes however my display has gone black (i assume it has gone to sleep due to inactivity) and then there is no way out other than hard reset.  
Cant switch to another tty console either, all i get is a blank screen, Although this seems to be a separate issue as i still cant get a tty console now as i type this.

---

### Post by brethren on 2008-04-29
i've been suffering from the random hangs in hardy. mine was a fresh installation yet within ten minutes of booting into ubuntu the whole system would crash, the cursor would be locked and nothing except a hard reboot would get my system back up and running:( after 3 fresh installs of 8.04 i had given up on it

anyway i ended up using the vista recovery dvd that came with my laptop but this morning i got the urge to try hardy just one more time, this time using the wubi install and guess what? NOT A SINGLE CRASH ALL DAY

i'd rather not have 2 os's on my hdd but just being able to use ubuntu again is worth it!

btw i can't find the original thread i posted in so i've posted here. maybe it'll help someone

---

