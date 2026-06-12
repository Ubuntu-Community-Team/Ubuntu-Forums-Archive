---
title: "wine problems"
date: 2007-06-07
forum: General Help
---

### Post by xGutsAndGloryx on 2007-06-07
i installed wine using automatix... it isn't showing up under the applications menu.... i configured it and everything ... can anyone point me in the right direction

---

### Post by yabbadabbadont on 2007-06-07
It won't show up in the menu as it is only used to run other programs.  Sort of like the java command.  You will need to create custom launchers for the windows programs you wish to run with wine.

---

### Post by xGutsAndGloryx on 2007-06-08
how do i set a windows program to use wine?

---

### Post by yabbadabbadont on 2007-06-08
When you create the launcher, the command you would use would be "wine c:\path\to\windows\program\program.exe"

You probably should read the WINE documentation too.  :D

[http://www.winehq.org/site/documentation](http://www.winehq.org/site/documentation)

---

### Post by xGutsAndGloryx on 2007-06-09
i am not worried about creating a launcher.. i am worried about finding wine to add it to the c drive

---

### Post by atlfalcons866 on 2007-06-09
say you want to install a program like dvdshrink
you put the dvdshrink.exe in to your home folder
then go to the termenial and do 
wine dvdshrink.exe

---

### Post by xGutsAndGloryx on 2007-06-09
i am just installed the program but it didn't create a icons on the desktop or in the main menu.




here is what it said

wine slsk156c.exe
fixme:shell:SHAutoComplete SHAutoComplete stub
fixme:shell DllCanUnloadNow stub
fixme:shell DllCanUnloadNow stub
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell DllCanUnloadNow stub
fixme:shell DllCanUnloadNow stub

---

### Post by atlfalcons866 on 2007-06-09
try reading the faq

[http://www.winehq.org/site/docs/wine-faq/index](http://www.winehq.org/site/docs/wine-faq/index)

---

### Post by TravMan63 on 2007-06-12
Try installing your app with wine file - I've had some issues with using terminal (xubuntu 7.04).
Also make sure you're not using the root account (sudo...) when installing or running wine.

Some of the installs I've performed have placed desktop shortcuts, some have not.  All have appeared in my 'others' menu.

You can create a launcher or folder containing various launchers for the wine components and place that on your desktop. (I think they are in /usr/bin )

I'll have to try the code given by yabbadabbadont :KS

```
"wine c:\path\to\windows\program\program.exe"
```

I had used 'wine \home\username\.wine ....' - which didn't work.

more info (and problems) on this thread:
[http://ubuntuforums.org/showthread.php?t=470842](http://ubuntuforums.org/showthread.php?t=470842)

TM

---

