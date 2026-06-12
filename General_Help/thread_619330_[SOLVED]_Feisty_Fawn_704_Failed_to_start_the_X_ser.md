---
title: "[SOLVED] Feisty Fawn 7:04 Failed to start the X server"
date: 2007-11-21
forum: General Help
---

### Post by TaoBoogie on 2007-11-21
Hello
My 7:04 installation has been working perfectly for a few months now until today when I got the following message at start-up.

> kinit No resume Image
Failed to start the X server

X server output

(==) Log file "/var/log/Xorg 0.log", Time Wed Nov 21 15:19:01 2007
(==) Using Config file " /ect/X11/Xorg.config
FATAL could not open
' /lib/modules/2.6.20-16-generic/volatile/NVidia.ko': No such file or directory.
(EE) NVIDIA(0) Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0) Aborting xxx
(EE) Screen(s) found but none have a usable configuration
Fatal server error:
No screens found


I have looked at the "similar questions" but each solution seem to use a terminal. After all the error messages I am left with a black screen and a command prompt.
I am relatively  new to ubuntu so do not feel that confident at the command prompt without instruction.
The last time I used ubuntu I only browsed for my email and instaloled some updates as prompted.
Tghanks for your help.
Tao


I have a NVidia7600GT card on an ABIT KN9 Ultra MoBo

---

### Post by TaoBoogie on 2007-11-21
~bump~ :)

---

### Post by TaoBoogie on 2007-11-21
Can anybody help me please?
Am I posting in the right forum?
Is this a unique problem that has no answers that we know of?

---

### Post by zvacet on 2007-11-21
Boot in recovery mode and type

```
dpkg-reconfigure xserver-xorg
```

Select vesa driver and you should have graphic again.After that you will have to install drivers for you card again.I hope I´ll help you a bit.

---

### Post by TaoBoogie on 2007-11-21
That solved my problem, thank you so much zvacet.
I did have to go through a few screens of questions and select choices. Apart from actually naming my video card I just selected the default answer for all (I think) of the other questions then typed in exit after I had finished and the GUI was back.
Happy daze
I then installed the NVidia driver using Envy al all is back working again as it was before. So I have my Compiz-Fusion settings back again too.
Just out of interest what caused this do you think? Was it perhaps something to do with an update? I say this because I can not remember doing anything else prior to the fault other than browsing and installing the suggested updates.
Thanks again zvacet you rock. :)

I can see that ubuntu is now notifying me that there are more "Software Updates available" I feel a little apprehensive about installing them.
What do you think?

---

### Post by zvacet on 2007-11-22
I think you should install them,because most of updates are security or make your app to run better.Was it kernel upgrade wich give you trouble?Anyway,now you know how to solve that kind of problem,so don´t be afraid to upgrade your system.

---

