---
title: "Unable to log in after first or second reboot"
date: 2008-03-16
forum: General Help
---

### Post by ferrelas on 2008-03-16
After having installed ubuntu I'm unable to log in after a reboot or two. The login screen just starts loading again when it is finished and just keeps going, and the time between these 'refreshes' is way too short for me to log in, any idea of what I should do?

---

### Post by thinkdez on 2008-03-17
Wow unusual problem...  

A few questions:

What version of Ubuntu are you using?
When this begins to happen can you boot to failsafe mode?
Did you do anything ie updates or such right before the reboot?  

Anything that could assist with troubleshooting the issue is helpful.

---

### Post by ferrelas on 2008-03-17
> **thinkdez said:**
> Wow unusual problem...  

A few questions:

What version of Ubuntu are you using?
When this begins to happen can you boot to failsafe mode?
Did you do anything ie updates or such right before the reboot?  

Anything that could assist with troubleshooting the issue is helpful.

I'm using 7.10.

Yes, I think I can get it to boot in the console-only mode.

Yes, I've installed the availible updates before the reboot, but sometimes it works after that reboot, but not the next.

I've also tried xubuntu, but the same thing happened there.

---

### Post by thinkdez on 2008-03-17
Hmmm.... odd if I had to guess there was a incompatibility with a patch but at the same time it kinda seems random.   Can you try to boot into failsafe mode.  Once booted you should be logged in as the super user try to run the command:
```
/sbin/init 5
```

This should bring you to run level 5 which is graphical mode.  Now I don't remember if it starts up GDM at this point or if you have to invoke it but if you can run the command 'startx' and it loads the graphical interface and your problem will be something to do with GDM.  If not then the problem is more than likely to do with Gnome itself but hopefully you can get some information in the logs to see whats happening

---

