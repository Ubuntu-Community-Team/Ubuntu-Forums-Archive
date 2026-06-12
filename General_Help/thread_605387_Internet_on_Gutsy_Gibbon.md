---
title: "Internet on Gutsy Gibbon"
date: 2007-11-07
forum: General Help
---

### Post by Liliitha on 2007-11-07
I have successfully upgraded to Ubuntu Gutsy Gibbon and installed GIMP 2.4 & GIMP-GAP.
The problem now is the internet.  I am on Ubuntu right now, the internet works, but I have to configure it every time to make it work ever since I upgraded.  How do I make it so the internet will be permanent instead of having to go to terminal and type
> sudo modprobe ndiswrapper every time?

---

### Post by dcstar on 2007-11-07
> **Liliitha said:**
> I have successfully upgraded to Ubuntu Gutsy Gibbon and installed GIMP 2.4 & GIMP-GAP.
The problem now is the internet.  I am on Ubuntu right now, the internet works, but I have to configure it every time to make it work ever since I upgraded.  How do I make it so the internet will be permanent instead of having to go to terminal and type
 every time?

I assume you are using a Wireless connection that uses ndiswrapper?

If so, then there should be a file called /etc/modprobe.d/ndiswrapper containing the following:
```

alias wlan0 ndiswrapper
```

---

### Post by Liliitha on 2007-11-07
Well yeah but that is not the problem.  It works fine if I type sudo modprobe ndiswrapper.  The problem is I have to type this in terminal every time Ubuntu loads up.  On feisty Fawn as soon as Ubuntu turned on I would have internet access.

---

### Post by Jive Turkey on 2007-11-07
I'm sorry I can't completely answer your question but I think if you make an executable script to run that command and put it in the /etc/init.d/ folder it should run at startup.  Look at some of the other files in /init.d for examples of how to do that.  There is a readme file there too that might give you some useful info.  That's what I would try anyway.  Make sure the script is set to allowed to execute as a program.  (right click it > Properties > Permissions > allow to execute as a program.

Hope that helps.

---

