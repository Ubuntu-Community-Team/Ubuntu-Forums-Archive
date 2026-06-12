---
title: "I have two -major- problems"
date: 2014-02-21
forum: General Help
---

### Post by greglolarikos on 2014-02-21
Hello to the ubuntu community ):P

   I just installed lubuntu 13.10 in an old desktop, in hopes that it will run smoothly. Well, my expectations were met, but I've found soon that even though it is quite a fast OS, it created certain problems.  First, when I first boot up the PC, about 80% of the times that I click to run mozilla web browser, the screen turns gray and I've waited for a bit, but it doesn't change and pressing different keys didn't work. That's why I'm force-shutting down the computer all the times. Currently I'm using chromium, it hasn't shown this problem, so I'll be using it, but I'd prefer it if I could use mozilla again.  Second, out of the blue, it will give me a message that I have disconected from the WiFi network ( unfortunately a wired connection isn't an option, as the router is a bit far away from the desktop) . Pressing the WiFi icon on the bottom right of the screen, it doesn't show me any WiFi networks to connect to. I've tried some things I've seen on the internet, like rfkill list, but it says that the wireless is unblocked.

Somebody knowledgeable in lubuntu help me, I'm a linux noob. :p

---

### Post by wildmanne39 on 2014-02-21
I suggest that you work on your first issue in this thread, and start a new thread in networking for your wifi issue.

We are only suppose to have one issue per thread and you will get the most help with your wifi in networking.
Thanks

---

### Post by oldfred on 2014-02-21
If force shutting down system remember the elephants. Do not power off or you may corrupt system.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

How much RAM and what video card?
My laptop with 1.5GB turns gray for a bit if I try to load too much more than one larger app like Firefox and a couple of small ones is the most I can do. Swap is many times slower than RAM. 
I think Firefox is still a large app, but newest versions are not a large as they used to be. Chromium is still considered lighter weight. 

How much swap do you have?
In terminal 
free -m

---

### Post by greglolarikos on 2014-02-21
I have a desktop, with 1GB RAM, Nvidia 6150 graphics chip,and AMD anthlon x2 CPU.

Swap:         1331         79       1251

---

### Post by oldfred on 2014-02-22
It looks like you are using almost all of swap.

---

