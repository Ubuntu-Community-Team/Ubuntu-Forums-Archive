---
title: "[SOLVED] Problems Booting - Used to boot fine"
date: 2008-02-15
forum: General Help
---

### Post by molemoore on 2008-02-15
Hello,

This is my official first post here. I just took the leap and put Ubuntu on my Tablet PC to get rid of Vista (still have dual boot "just in case"). That was a tough switch cause I had to give up the tablet part of my computer, but here I am anyways. Anywho, to my issue...

I installed Ubuntu (7.10 I believe) a few weeks back and it has been working great. Everything has been working great, I have been really pleased. That is, at least until a couple nights ago. Basically, I was using my PC, everything going fine, and I shut down for the night. The next morning I started my PC again and it will not boot. A couple things I noticed: First, I now see some commands on the screen, before it was just the Ubuntu loading logo. Second, the last line that says "OK" on it, and the last line on the screen is: 

* Running local boot scripts (/etc/rc.local)                   [OK]

The command prompt just sets there...blinking...taunting me...staring me down so to speak.

Note: I do see the Ubuntu loading screen before the command lines. The progress bar finishes and then the command lines show up. I would say that that is the point where the login screen usually is displayed.

Anyways, the only thing I did the prior night that was out of my norm was I played with the display settings a little, I tried to hook up a second monitor and use the two of them but I could never get it to work so I gave up and change everything back to its original setting (or so I believe I did) and all was well. Other than that I was browsing the web, nothing special. I played with Eclipse a little, but did no coding and listened to some music.

My experience level: Pretty much none. I am an IT pro but I am pretty much new to linux, so step by step would be nice to start with. I have begun reading n00b stuff to get up to speed but I am not there yet.

As always, any help is appreciated. Please let me know what additional information you need.

Thanks!

mole

---

### Post by molemoore on 2008-02-15
bump

---

### Post by molemoore on 2008-02-15
bump

---

### Post by molemoore on 2008-02-15
Third and final bump...a hand with this is appreciated.

---

### Post by Ivorydawn on 2008-02-15
Hi,

Can you boot into the repair console? if so can you try to reconfigure the x server with  sudo dpkg-reconfigure -phigh xserver-xorg.

That's what I use, it's got me out of lots of sticky situations.

Regards

Andrew

---

### Post by molemoore on 2008-02-15
That worked perfectly. I will add this command to my "emergency" notebook and work on learning what all it does later.

Thanks!

---

