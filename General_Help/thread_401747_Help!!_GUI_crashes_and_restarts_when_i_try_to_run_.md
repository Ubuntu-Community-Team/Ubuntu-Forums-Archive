---
title: "Help!! GUI crashes and restarts when i try to run several programs HELP!"
date: 2007-04-04
forum: General Help
---

### Post by jdarias on 2007-04-04
Hello.When i try to do something related to wine, or start google earth, or play games like tremulous or enemy-territory i get expelled from the GUI and i just see a black screen, with nothing than a blinking cursor in it.

Then it restarts again, and i get presented to the login screen.

This seemed to start hapenning after i did an apt-get autoremove and apt-get clean. I only remember something called libwxgtk or something was deinstalled, along with some other things that got installed when i installed frostwire. 

Please help me sort this thing out, i'm desperated.

---

### Post by phidia on 2007-04-04
You could open the terminal and type > dmesg <enter>
after your gui crashes, and/or look in /var/log/message & syslog 

How much ram do you have?

---

### Post by jdarias on 2007-04-04
Sorry, i got it fixed soon as i reinstalled the nvidia driver. Somehow it affected all opengl apps, so i reinstalled the driver and everything went back to normal, seems apt-get was not the cause. Sorry for freaking out :(

---

### Post by DarkStarAeon on 2007-04-05
I had the exact same problem.

My problems started when I installed a new theme. Worked fine at first, then all of a sudden some programs I had installed via CrossOver Office or Wine itself started crashing the GUI, going to black screen, then back to login screen. Weird thing was, it wasn't all programs vis CrossOver or Wine, just some of them, ones that are graphics intensive (Quicktime, Flash MX etc)

Then after a restart I noticed that Google Earth, Stellarium and Celestia were having the same issue.

So, I got the idea that it might be the graphics driver or some OpenGL or GLX related issue, problem is I didn't know where to start to fix it.

Eventually I just used Envy to uninstall the driver, then I reinstalled it, that did the trick so far, I'm still reinstalling programs that weren't working before which I had removed out of hope it would solve the issue and didn't.

I don't know the root of this problem, but I'm reluctant to ever try changing the default settings for themes or windows on Ubuntu again if this is what happens.

---

### Post by DarkStarAeon on 2007-04-05
Well I just restarted and got a crash report/error message

Then this page opened up in Firefox....

[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/39068](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/39068)


I have no idea what to do about this.

---

### Post by xmux on 2007-04-06
hey i have the same problem, what should i do?? I wanted to install Counter Strike CS and it installed perfect but than when i wanted to open CS it has crashed down and start gnome!! 

Did anyoneelse has an idea??

---

### Post by xmux on 2007-04-29
I installed the nvidia driver again and it solved the problem!! Thanks anayway!!

---

