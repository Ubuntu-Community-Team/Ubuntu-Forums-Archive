---
title: "Ubuntu (16.04 LTS) Randomly Stops Working on Lenovo Yoga 2-11"
date: 2016-08-04
forum: General Help
---

### Post by sx78967 on 2016-08-04
I deleted Windows off of my Lenovo Yoga 2-11 and replaced it with the latest edition of Ubuntu.  Occasionally, when I'm writing something, browsing the web, or just simply on the desktop doing nothing, the computer freezes completely.  I've let it sit for up to 30 minutes hoping it's just something temporary, but it doesn't seem like it is.  Every time this happens, I have to reset the laptop by holding down the power button and pressing it again to turn it back on.  Has anybody else had any issues with this?

I've tried using system monitor to see if I can figure anything out, but I don't see anything that is potentially causing this.  I am fairly new to Linux still though, so there could definitely be something I'm missing.  
I don't know what the entire issue is at this point still.  The freezing/altogether stopping working is sporadic and happens no matter whether I've been on the computer for 5 minutes or 3 hours; it just happens randomly.  

I've even tried the Alt+SysRq + REISUB method.  That doesn't work with this.  I'm left wondering whether I should reinstall Ubuntu and risk losing all of my programs and information or if there may be another solution to the problem I'm not thinking of.

Any help is greatly appreciated!

---

### Post by Bucky Ball on 2016-08-04
Welcome. So the keyboard also stops working at this stage? Maybe why REISUB is not working. Does holding control+alt then tapping F1 bring you to a CLI, like a big terminal where you can login?

Also, is the machine fully up to date? You could try booting, selecting Advanced Options (from memory) then the recovery kernel. Drop to a shell and

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

Exit then resume normal boot.

---

### Post by sx78967 on 2016-08-04
Hey Bucky Ball.  Thanks for the tips.  The keyboard does seem to stop working at this point as well, unfortunately.

I followed your instructions and so far everything seems great!  I won't know for sure until I've used the machine for a while and can see if anything does continue to happen.  It did update quite a lot of packages so perhaps that was the problem after all.  

Thanks again for your help!  I will keep this thread updated if that solution doesn't end up working permanently.

---

### Post by Bucky Ball on 2016-08-04
All good and glad that got you somewhere. See how it goes for a day or two then please mark the thread as solved to help others. See Thread Tools at top right or link in my signature.

Here's hoping the situation remains stable so you can enjoy Ubuntu-ing. :)

---

### Post by sx78967 on 2016-08-06
Bucky Ball, bad news.  I thought things were looking up, but then today I was once again in the middle of watching a video and once again it froze up.  Here's something interesting that might give some help though; when I was working on other things, I didn't realize that literally everything freezes up/stops working.  In the middle of the video the sound stopped working and everything just froze.  Tried clicking around, and trying various keyboard shortcuts, with no avail.  I'm still not 100% sure what's causing it.  

The good news is that it does seem to happen much less frequently than before.  It didn't do it at all yesterday.  Somebody mentioned to me that this ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1518457](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1518457)) could be my issue, but I'm not sure how to fix that problem if that is indeed my issue.

---

