---
title: "Java GUI problem (quite weird)"
date: 2007-10-02
forum: General Help
---

### Post by keeler1 on 2007-10-02
I am having to write a program for a college class I am taking.  Everything is all coded up and on the schools servers.  I can log into those server through ssh and get to my program.  I log in with ssh -Y so I will see the graphical apps on my screen (such as java programs).  I run it off of said server in Ubuntu 7.04 and the GUI is blank.  The frame is there but nothing is on it.  

I then log into the same servers with my laptop running fedora core 6 and the GUI displays perfectly with all buttons and labels where they should be.  I am not running the program from my local systems.  It is using the java version on the server and giving my computer the graphical output.

So both are being run on the same version of java but for some reason they do not display correctly on my desktop.  Is there any reason for this?

I know its nothing with the program or java version.  (Program runs perfect on same server with same java version just not when logged in through Ubuntu)

The program also works locally on my laptop but not locally on my desktop running ubuntu 7.04.

I am at a loss for why this could happen.

---

### Post by T_W on 2007-10-02
Are you running Compiz/XGL/AIGLX?

Java Swing apps definitely have problems with  Compiz.

---

### Post by keeler1 on 2007-10-03
I am running beryl with the nvidia driver and AIGLX.

---

### Post by michaelzap on 2007-10-03
Try turning it off and see if the app then displays as expected (Alt-F2 and then run metacity --replace). I have this problem with Compiz Fusion also. The good news is probably that it's not your program...

---

### Post by keeler1 on 2007-10-03
Running metacity instead fixes it and the program displays fine.  I dont even have to exit beryl.  All I had to do was open up the beryl manger on my top panel and tell it to use the metacity window manager.  Then everything worked.

Thanks for the help.

---

