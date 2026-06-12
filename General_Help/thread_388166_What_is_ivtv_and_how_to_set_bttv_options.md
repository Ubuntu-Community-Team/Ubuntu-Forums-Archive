---
title: "What is ivtv and how to set bttv options"
date: 2007-03-19
forum: General Help
---

### Post by camini on 2007-03-19
Hello,

I managed to make my TV-Card (bt878 based, Hauppauge WinTV) work - once - then after reboot it didn't work.

So after looking around and reading lots of threads on this miserable TV tuner subject I'm left with a couple of questions:

1) what is ivtv and why is it specified in the modules to load on boot?  Do I need it?  My card works with bttv - can these 2 clash?

2) I've managed to make my TV-tuner work using:
rmmod bttv
rmmod tuner
modprobe bttv card=10 type=38

But is seems these settings are not permanent.  Can anybody tell me how to make sure these bttv settings get set once and for all?

Thanks in advance

---

### Post by camini on 2007-03-19
Bump.

Nobody knows what ivtv is and whether its needed?

---

### Post by fragos on 2007-03-19
ivtv is a different chip set for TV and you don't have it.  If you need to modify the boot-script do so in /etc/rc.local which will be executed as root as you'll need to.  With Ubuntu I'm very surprised you have to go through this.  The card is automatically detected at boot.  The only thing you should have to do is install a good TV viewer.  I highly recommend tvtime which will take you through all the  steps to watch TV in a window.  You need to know a few things like NTSC vs PAL, NTSC in the US and signal source as TV antenna, cable or cable 100+ channels.  How did you determine tuner=38, that could be wrong?

---

### Post by camini on 2007-03-21
Fragos,

Thanks for this info.  I thought I didn't need ivtv, but wasn't sure.
Using bttv I was able to make tvtime work - once.  After reboot my card and tuner/type setting for bttv seemed to have disappeared.. hence my question on how to make these permanent.
I will check whether this can be added to rc.local.

Thanks again.
Camini

---

### Post by camini on 2007-03-27
OK, I finally solved this problem.
I was indeed trying to use tvtime to watch TV - looks like a decent piece of software.
So, first I removed the ivtv entry from /ect/modules as apparently I don't need it.
Then I created a /etc/modprobe.conf file with as only entry (so far):
options bttv card=10 tuner=38

How did I find out these were the right settings for my WinTV PCI (bt878) card?  I had a look trhough the bttv cardlist and tuner files and figured out those were the ones (trial & error).

Voila - now Ubuntu boots with the correct bttv options.

I hope this will help out others with the same hardware..

---

### Post by fragos on 2007-03-27
A point of information.  For some reason tvtime, which I love, won't work with the ivtv driver.

---

