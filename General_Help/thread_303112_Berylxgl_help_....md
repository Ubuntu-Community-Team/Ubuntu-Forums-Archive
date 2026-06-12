---
title: "Beryl/xgl help ..."
date: 2006-11-19
forum: General Help
---

### Post by kbsuperstar on 2006-11-19
Yeah, so I just installed Beryl, and when I load the gnome-session of XGL, there's no desktop background, and after a little while everything disappears and I have to do ctrl+alt+backspace and restart GDM. Any idea what I can do to fix this?

---

### Post by finferflu on 2006-11-19
Do not start your session as an XGL session. Start a normal session and then run **beryl-manager**. It worked well for me.

Hope it helps

---

### Post by kbsuperstar on 2006-11-19
I'll give it a try, thanks :)

---

### Post by kbsuperstar on 2006-11-20
I tried it, and it just crashed and went back to Metacity. I redid the tutorial, and now when I try to log into the XGL session, it just gives me a blank (dark red?) screen for a few seconds and then just goes back to GDM login.

Hrmm...

---

### Post by xpod on 2006-11-20
Well, i cant give you no technical help pal but i had to try one or two different howto`s out when i first started messing with it.

Trial & error really.
I`ve installed Os`s and beryl`s etc more times than i can recall now and could`nt even tell you what methods i used :-k 

Good luck regardless..

---

### Post by finferflu on 2006-11-20
What's your video card?

---

### Post by kbsuperstar on 2006-11-20
nVidia GeForce MX 4000, but in /etc/X11/xorg.conf it's just labeled "nv"

---

### Post by kbsuperstar on 2006-11-20
bump

---

### Post by CowzRule on 2006-11-20
I'm thinking you first need to install the Nvidia drivers. Have a look at [this page]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29") on how to do that.
Then I'd follow [this guide]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL") on installing XGL and Beryl.

---

### Post by kbsuperstar on 2006-11-20
Thanks, I'll try it out.

---

### Post by kbsuperstar on 2006-11-22
I did everything in the nVidia tutorial, but whenever I change "Driver" (in the "Device" section of /etc/X11/xorg.conf) from "nv" to "nvidia" and then reboot, xserver always crashes, and I have to switch it back to nv. I know I got around this somehow before, but I forgot.

---

### Post by Random20230808 on 2006-11-22
You may follow the instructions how to install Xgl/Beryl from Ubuntu community docs [https://help.ubuntu.com/community/CommonQuestions#head-23187ff8609335c10dbb55c6cdc4c1f47fddcda0]("https://help.ubuntu.com/community/CommonQuestions#head-23187ff8609335c10dbb55c6cdc4c1f47fddcda0"). They are very helpful.
Give extra caution to Hardware section [https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html"). Your graphic card is officialy supported.
When you install Xgl I suggest that you choose the first way to start it up (you'll find it in the instructions).
Make sure first of all that Xgl works fine before you proceed to Beryl.
Give extra caution to the notes that are written.

P.S. Before all this you have to reset your X config files to prior state in order to have your system working. Perhaps if you have kept an xorg.conf backup file (maybe /etc/X11/xorg.conf.old) you should backroll to it using a terminal.

---

### Post by kbsuperstar on 2006-11-22
The problem is that it won't work because my graphics card isn't working. I have to reinstall the nvidia drivers, and I can't seem to get it working

---

### Post by Random20230808 on 2006-11-22
Did you try the instructions from Ubuntu's Hardware section?
[https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html")

---

### Post by kbsuperstar on 2006-11-22
Yes, and I have tried other tutorials that are slightly different, but nothing has worked. My video card used to work correctly, but after I tried installing Beryl/XGL and editing the xorg.conf file, it stopped working ](*,)

---

### Post by Random20230808 on 2006-11-22
Which edition of Ubuntu do you run?

---

### Post by kbsuperstar on 2006-11-22
Dapper (6.06)

:-k

---

### Post by kbsuperstar on 2006-11-22
bump

---

### Post by Rajiv_Nair on 2006-11-22
i dnt think u gotta edit ur xorg.conf AFTER uve installed new drivers. I think drivers make the necessary editions themselves

---

### Post by zekonology on 2006-11-22
Hi, I also agree with that coz the nvidia drivers will automatically configure your xorg.conf once you activate it. I'm also using beryl however, i'm facing a problem which my dialog window is flickering. seems like it does not match with emerald. What i did is open up the emerald manager and the window will stop flickering so everything is going to be okay. but then, it's annoying coz i need to do the same thing in order to use beryl.

---

### Post by kbsuperstar on 2006-11-22
Well, I'm having problems with videos online with the MPlayer plugin and in my xorg.conf file the driver is labeled "nv" instead of "nvidia"

---

### Post by Random20230808 on 2006-11-23
Do you have a problem installing the 6.10 release?
From my experience it works much better with Xgl/Beryl.
In fact I couldn't have them working on 6.06.
I had problems even on Xgl...:-k

---

### Post by Random20230808 on 2006-11-23
Take a look at this one :
[https://help.ubuntu.com/community/NvidiaTroubleshooting]("https://help.ubuntu.com/community/NvidiaTroubleshooting")

---

