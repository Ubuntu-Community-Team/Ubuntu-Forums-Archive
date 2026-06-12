---
title: "power surge?!!!"
date: 2007-07-09
forum: General Help
---

### Post by luckyd on 2007-07-09
Today the cleaning lady was here and she was using the vaccum, when all the sudden my computer went off. I went outside and switched the power back on for the house, but then it happened again. I didn't try to turn on my computer again until she left, and when I did everything *seemed* fine so I went on as usual. But now that I have been using it a while it seems like some things have slowed down, significantly. I havn't run memtest yet, but for some reason I dont think that is the problem. Is it possible that a power surge could just slow down a computer without destroying it?

---

### Post by luckyd on 2007-07-09
bump

---

### Post by Turboaaa2001 on 2007-07-09
This is an odd one, I love answering these questions.

Of course when the vacume was turned on you had a power sag, not a surge. Of course when your computer turns on for the first time it will pull a lot of power and stress the parts inside it.

Your already on the right track with the memtest. The most common causes of a slow down is damaged memory. Of course the other option is that when your system shutdown the second time it could have messed with the OS files.

I had a problem with Ubuntu 5.1 when I cut power after I found out I forgot to plug-in the fan for the heatsi nk(ooops) :lolflag:

Anyway, after I rebooted I got an error about file continuity. So it could be that some files are damaged.

Thats my guess, but do run memtest and a HD test. That way you'll know its not them.

---

### Post by luckyd on 2007-07-10
when  you say "hdtest" do you mean fdisk?

---

### Post by HermanAB on 2007-07-10
Any large electric motor in a house can cause a power surge - vacuum cleaner, dishwasher, drier, washer, A/C and so on.  This spike can go down and up thousands of volts.  Although such a spike doesn't contain much energy, it can perforate silicon devices.  Therefore, it is a good idea to always plug a computer into a power bar with a built-in spike arrestor.  It is an even better idea to plug a computer into a UPS.  Even a simple and cheap $100 UPS will add years to the life of a PC.

---

### Post by smoker on 2007-07-10
you should check out all your hardware after such an event, especially the powersupply, if that isn't producing enough juice now, it will cause a slow down. but i would check everything, memory - with memtest, harddrive - with fsck, and also to check the harddrive, drive fitness test, check here:
[http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)

best of luck

---

