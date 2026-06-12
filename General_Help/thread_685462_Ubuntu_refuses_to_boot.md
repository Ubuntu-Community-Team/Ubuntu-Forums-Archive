---
title: "Ubuntu refuses to boot"
date: 2008-02-02
forum: General Help
---

### Post by warnec on 2008-02-02
Sorry for a non-descriptive title (did I spell it right?), but that's exactly what happens. You can read about my previous problem here:

[http://ubuntuforums.org/showthread.php?t=674188](http://ubuntuforums.org/showthread.php?t=674188)


Then, I managed to install Ubuntu 7.10 with Alternate CD. Reboot, then i choose Ubuntu... and then I can see loading menu... And it freezes. The orange loading bar is long for about 2 milimetres (:P), and that's it. I can do nothing but hard reboot. Any ideas?

---

### Post by SpiderGorilla on 2008-02-02
System specs? You running i386, AMD? Etc?

---

### Post by warnec on 2008-02-02
-C2D E6750
-3 GB ram
-GPU 8800 GTS 512 MB
-mobo Foxconn mars
-320 GB HDD
-i386 version

---

### Post by SpiderGorilla on 2008-02-02
Uhm... unless you really desperately against it, try the 64-bit version. Or try reinstalling using the English version of the system, since your previous post seems to indicate you're running Polish. I can't think of ANY reason the Polish version shouldn't run perfectly, but I speak English natively and so I install that one every time.

---

### Post by warnec on 2008-02-02
Well, the alternate CD is available only in English ;) So i have English Ubuntu. After installation, I wanted to download polish language packages, and then i'd have polish Ubuntu. And talking about 64-bits, I'm really against it. AFAIK, there aren't so many x64 packages and not every 32 bit program works.

And i don't think it would be the right way to do with the problem. Why do you think 64 bits would work? I always used 32 bits. I just want to know what is causing the problem, not get over it like every Windows user does :D

---

### Post by SpiderGorilla on 2008-02-02
Heheh. It's really hard to say what would cause the problem. Too deep-level for me, sorry.

---

### Post by Fechter on 2008-02-02
There wa s one user that also had a problem similar to yours. The only thing that occurs to my mind is - you hav 3GB Ram, how large is your swap partition? Swap should be 1,5 times more than Ram is, according to the "rule".

---

### Post by Mze on 2008-02-02
Most probably its the 8800 GTS graphics card.

Run a search on the forums for it and see if there is work around it.

---

### Post by warnec on 2008-02-02
My swap is 2 GB. Ok, I'll try to change it to 4,5 GB. Do I have to reinstall Ubutnu for this, or do I only need to run installer, delete swap partition, and then make new swap partition? I mean, is swap partition "connected" to the system during installation? Can i remove it and make it once again?

---

### Post by Mze on 2008-02-02
Keep your partition the way it is.

Concentrate on the graphic card first?

---

### Post by warnec on 2008-02-02
Ok, I definitely made some progress. I launched Ubuntu with "irqpoll" parameter and it booted! Now, after that, I've been brought to command prompt. I logged in, and then i typed "startx" and it spat out some errors. On the bottom was:

```

(==) Log file: "/var/log/Xorg.0.log", Time : Sat Feb 2 18:00:20 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected

Fatal server error:
no screens found
XIO: fatal IO erroe 104 (Connection reset by peer) on X server ":0.0"
        after 0 requests (0 known processed) with 0 event remaining.

```

What to do now? You want to see the log, or xorg.conf?

---

### Post by Mze on 2008-02-02
Please search the forum for "8800 GTS" and see if there is a work around.

Looks like a graphic driver problem.

---

### Post by warnec on 2008-02-02
Still more progress done. Now, when i boot Ubuntu, I get a few lines with [OK] and then it goes to "Running local boot scripts" and it hangs there. Monitor turns of and on 3 times (each time showing the same lines) , and then i get a small window saying I'm in safe graphics mode. Then, i manually chose my card in the card model list (i chose manufacturer - NVIDIA, model - 8 series) After i click ok, I can just see the cursor . I figured out i have to press space then. Then i go to GDM and can login in graphical interface! w00t!

But there are still problems. Restricted drivers manager says that my hardware doesn't need any proprietary drivers, even if it does! Now, I'm trying to install driver from NVIDIA site (I suppose nvidia-glx-new won't work)

---

