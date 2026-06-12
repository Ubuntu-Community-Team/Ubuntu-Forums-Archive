---
title: "computer freezing"
date: 2007-05-29
forum: General Help
---

### Post by nodyl on 2007-05-29
This is also posted in the absolute beginner section, but I am reposting here because the problem is becoming worse and I am hoping to have a working computer soon.  Here is the basic info:

If I have opera and mozilla running, the computer freezes.

If I have more than one tab in a browser open the computer freezes.

If I have a browser plus open office open the computer freezes.

If I have gaim and a browser open the computer does not freeze; however, if I close the browser, gaim may close too.

If I use update manager with a browser open, it freezes.

If I use update manager by itself it says to run dpkg --configure -a by itself which I cannot figure out what it is.

Please help, the computer is getting worse every moment.

---

### Post by kevinlyfellow on 2007-05-29
Hey neighbor... I'm a grad student at Calstate Fullerton

I don't know what the problem is but it seems to be with web apps?

To fix your "dpkg --configure -a" problem, go to Applications -> Accessories -> Terminal and type in
```
sudo dpkg --configure -a
```

Now when you say freezes, what freezes?  When it does freeze, does restart X help (ctrl-alt-backspace)

Edit: Oh, btw have you shown up to OCLug?  [http://www.oclug.org/](http://www.oclug.org/)

---

### Post by nodyl on 2007-05-29
My bad; I typoed the dpkg command.  Yeah, the update manager freezes too, even with no browser open.

Ctrl-alt-backspace almost never works on my computer and this is one of those times.

By freezes, I mean the computer completely hangs, mouse unresponsive, fan going nuts.

I have never been to oclug; I didn't even know that existed!

I don't know if this is a memory issue or what's going on.

---

### Post by kevinlyfellow on 2007-05-29
Check you system logs (System -> Administration -> System Logs).  See if there is the dreaded Kernel Panic.  It may be a bad driver???

Another thing you can try is the Memory Test.  When Grub starts up, there should be something the says "Memtest +86" or something along those lines.  Let it run for a while.

Is there another OS on the machine?  Have you tried another live distro?

---

### Post by nodyl on 2007-05-30
kevinlyfellow, I pressed "delete private data" in opera and mozilla seems to be working fine now.  Opera is only messing up when I try to log into a certain site; I can only stay logged in to one page at time so if I deviate from my account page the thing thinks I'm logged out.

Everything else is running okay again, but still a little slow.

I'm not really sure what happened here or how what's going on in opera has any effect on mozilla, but I think this has just become an opera problem.  I'll jump over to the threads over there, but if you know why that helped, feel free to reply or message me. 

Thanks for your help.

---

### Post by kevinlyfellow on 2007-05-30
> **nodyl said:**
> kevinlyfellow, I pressed "delete private data" in opera and mozilla seems to be working fine now.  Opera is only messing up when I try to log into a certain site; I can only stay logged in to one page at time so if I deviate from my account page the thing thinks I'm logged out.

Everything else is running okay again, but still a little slow.

I'm not really sure what happened here or how what's going on in opera has any effect on mozilla, but I think this has just become an opera problem.  I'll jump over to the threads over there, but if you know why that helped, feel free to reply or message me. 

Thanks for your help.

I have no ideal... but good thing it was something simple to fix.  Best of luck

---

