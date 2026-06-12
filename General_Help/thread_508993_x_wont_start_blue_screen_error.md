---
title: "x wont start blue screen error"
date: 2007-07-24
forum: General Help
---

### Post by Agenator on 2007-07-24
I have read two or three posts on this error and all seem to have diferent solutions. I have tried a couple of them and none seem to work. I am using Ubuntu Studio Fiesty with the gnome desktop. I get this error:
Failed to start the X server (your graphical
interface). It is likely that it is not set 
up correctly. Would you like to view the X
server output to diagnose the problem?

after a screen says that it is loading something then it hits timidity and says configure timidity then try again. This screen flashes 2 times after the splash screen and then the bsod comes up :(  I was using beryl which was working just fine for a couple of days and then this happened. I have an Nvidia 8600 gts and have tried to reconfigure xorg.conf a couple of times but during the configuration the b&w terminal will popup and say something about making a backup in the folder and wont let me finish the config....
please help me fix this
AGEN

---

### Post by badrobot on 2007-07-25
1) did you update the kernel between the time that it worked and now?

2)are you using the nvidia commercial drivers, via alberto milone (envy) or other such method?

if the answer is yes to both, i had a similar problem, if i remember right, the old nvidia drivers don't talk to the new kernel correctly.  the way i fixed it was by running envy again from the console and uninstalling and reinstalling the drivers.  you might also try removing beryl if the above doesn't work.

---

### Post by Agenator on 2007-07-25
no I did not update the kernel but yes I am using envy... how would I run it thourgh the terminal?

---

### Post by badrobot on 2007-07-25
just type 
[FONT="Courier New"]envy[/FONT]
at the console and since it's already installed it should run and give you a bunch of options, one of them being uninstall.  then uninstall.  when it's done, reinstall in the same way.  you may actually have to:
[FONT="Courier New"]sudo envy[/FONT] 

i'm not sure that this is your problem though since you didn't update your kernel.  you can always try it of course.  if it doesn't work, you can also try removing beryl.  

you should also check the error log that you are presented when X doesn't start.  you may get an idea of what is going on through that.

---

### Post by Agenator on 2007-07-25
it worked. TYTYTYTYTYTY now that I think about it i seem to remember downloading a kernel updat :P o well works gr8 now ty

---

### Post by badrobot on 2007-07-26
schweet, glad it worked for you.

to make life easier, next time you upgrade the kernel, uninstall the nvidia drivers with envy first, do the upgrade, then reinstall the nvidia drivers.  that way you won't get stuck in the console.

---

