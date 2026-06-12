---
title: "blue screen , x wont start new install ubuntu studio"
date: 2007-07-25
forum: General Help
---

### Post by JDForensics on 2007-07-25
please help i installed ubuntu today but x wont work please help

---

### Post by Shardsofmetal on 2007-07-25
you probably need to install a video driver. When I installed Ubuntu Studio, i had that problem.

---

### Post by JDForensics on 2007-07-25
how do i do that i just installed it

---

### Post by mykrob on 2007-07-25
can you provide more information on what you computer or laptop you have installed this on, particularly what video card/chipset you are running?

---

### Post by JDForensics on 2007-07-25
i have a compaq labtop and an ati graphics card

---

### Post by mykrob on 2007-07-25
try to drop to an alternate terminal.. Press Ctrl+Alt+F3

Log in.. 

next, type

sudo nano /etc/X11/xorg.conf

press enter, supply your password, then press enter again


using the arrow keys, scroll down and look for a line that calls out your video card.. it will look somethign like this:

```

Section "Device"
  identifier "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
  boardname "Intel 945"
  busid "PCI:0:2:0"
  driver "i810"
  screen 0
  vendorname "Intel"
EndSection

```

move to the portion that says 

driver        'xxxx"

and change whatever is in the quotes so the line reads:

```

driver  "vesa"

```

now, press Ctrl+x, be sure to answer Yes to save the file.. When you are put back to the command prompt, type

startx


this should get you a working X-session..

Please report back with your results,
-myk

---

### Post by mykrob on 2007-07-26
any luck?

---

### Post by Agenator on 2007-07-27
I personally know JD and I called him 2 c if he had any luck... he said that it didn't work... and just fyi he hasn't had  a chance to install anything on it cuz he cant even get to the login screen. He gets a BSOD which says that x wont start and to restart gdm... He installed using wubi... Please continue to help him, I dont know much and am learning as well so I have no ideas..... could possibly be a mis configured xorg.conf file but i dont really know how to change that....

---

### Post by mykrob on 2007-07-27
please have him to post as much detail as possible. At this point, no one really has enough info to go on.. Even if Xdoesnt start, he should have been able to drop to the virtual terminal and edited the xorg file. Perhaps he has a screwed up install all together?

On a side note, i have heard that a lot of people had trouble with installing Ubuntu Studio. I would recommend him doing a clean Ubuntu Feisty install, then simply add the repository for Ubuntu Studio to add their software and kernels..

-myk

---

### Post by Agenator on 2007-07-27
k ill tell him that....
edit:
I told him, he said he would try it when he gets his internet back....

---

