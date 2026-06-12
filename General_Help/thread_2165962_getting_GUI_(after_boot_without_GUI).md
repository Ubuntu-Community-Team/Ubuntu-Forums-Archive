---
title: "getting GUI (after boot without GUI)"
date: 2013-08-07
forum: General Help
---

### Post by col48 on 2013-08-07
I have a 64-bit Precise system with dual boot.

Occasionally, when switching on the computer, after choosing Precise it boots to a command line prompt for my username and password instead of taking the usual GUI route.

I can login that way with no problem but I can't find the command which would then give me the GUI I would get if I have logged in via the GUI route.  Can someone enlighten me, please?

---

### Post by zealibib slaughter on 2013-08-07
I believe the command you need is service gdm restart (or maybe start). I may be wrong though as I haven't had any experience in unity beyond seeing that It won't run on my system.  It may be service lightdm (re)start. Also the magic sys_rq key K will restart the xserver "alt + sys_rq(print scrn) + k"

edit 

done some googling and the command seems to be sudo gdm start but service gdm (re)start should (re)start the display manager and x server too.  Seems to me you may be  having a crash of the xserver sometimes.  you may want to check your logs in the directory /var/log.

---

### Post by col48 on 2013-08-07
Thanks for your trouble, zealibib

Next time it happens I'll try it (them!) out.
A shutdown and reboot has always sorted it in the past, but this would be quicker.

I suspect the cause is a timing issue - something is taking slightly longer to complete than usual and a contemporaneous process which needs it done is not checking before assuming it has been done.

---

### Post by grahammechanical on 2013-08-07
Precise Pangolin does not use GDM. It uses Lightdm. You may try

```
sudo service lightdm start
```

Regards.

---

### Post by col48 on 2013-09-15
The best way to make sure an intermittent fault does not happen is to ask an expert to watch it happening.....

This fault has not happened since I last posted.  So it hasn't felt right to mark it solved.

---

### Post by col48 on 2013-09-25
> **grahammechanical said:**
> Precise Pangolin does not use GDM. It uses Lightdm. You may try

```
sudo service lightdm start
```

Regards.

Fault showed up for the first time for some weeks just now.

The service call did not do the trick.  The response was something like "lightdm already running".

What should I look for in the logs, and where?  I'm not a regular log reader!

---

### Post by col48 on 2013-09-25
> **grahammechanical said:**
> Precise Pangolin does not use GDM. It uses Lightdm. You may try

```
sudo service lightdm start
```

Regards.

The fault just recurred (that's twice today!)
As stated in my previous post (#6) this did not work.  However
```
sudo service lightdm restart
```
did.

---

