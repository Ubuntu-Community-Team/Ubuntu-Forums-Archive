---
title: "Grub loading error 17"
date: 2006-12-08
forum: General Help
---

### Post by boostedtsi on 2006-12-08
Well this was just a matter of time I suppose.
I installed this a few months ago to try it out, and while it is ok, I do a fair amount of gaming so linux just is not for me.
I have tried the emulators, and they are 'ok' single player, but online, forget it, the FPS hits the floor.

So, this led to me barely ever booting into ubuntu on purpose, mainly it went because it chose itself as the default :evil: to load.

So I go to reboot after a game patch install, and lo and behold it is now doing this. I cannot boot the computer period.
So how can I get rid of this so I can have my box back?

---

### Post by boostedtsi on 2006-12-08
Ok I know what started it, and did not think about it when I did it. 
I recently got pissed at my comp for several reasons, so I decided to start anew and format the extra 2 partitions. 300 giger, 3 9X gig partitions.
I have my main drive which has W2K, Ubuntu and then open storage. I also have a second pure storage drive, but it was never installed there. Even if it were, it was formatted as well.

So I probly wiped out Ubuntu, so how do I go about and getting rid of this grub loader?

---

### Post by iamhugeinjapan on 2006-12-08
If you want to be rid of Ubuntu/Grub, a quick and easy way is to boot your Windows install cd (you have one of those right?) and load the Recovery Console. Login to your installation and put in the command to rebuild the master boot record:

```

fixmbr

```

Agree to any warnings and you should be booting Windows in no time.

If you want to recover Grub and still use Windows and Ubuntu, there's guides on the forum.

---

### Post by boostedtsi on 2006-12-08
woo back to gates I go.
For most stuff linux is fine. 
It really has come a long way. For the average person it is all they really need. But for gamers, and heavy video/audio it still has a ways to go.

---

