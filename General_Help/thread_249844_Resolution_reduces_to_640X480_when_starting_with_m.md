---
title: "Resolution reduces to 640X480 when starting with monitor turned off"
date: 2006-09-03
forum: General Help
---

### Post by PryGuy on 2006-09-03
Good day!
I've got an interesting problem here: I've got Ubuntu on my server and I turn off my Samsung 550b CRT monitor there, cause there's no need in it most of times. But once I have turned the monitor on (the system started with the monitor off) I  discovered that it has the resolution set to 640X480! And I couldn't change it to 1024X768 going to Preferences/Screen Resolution cause there was the single resolution 640X480. Everything's fine when I start the system with the monitor on. I can live with it, but it's not nice anyway, please help!

---

### Post by Ramses de Norre on 2006-09-03
You could disable gdm/kdm (and thereby Xorg) on startup, when you then turn your monitor on and start X you'll get the higher resolution. And your server will also run maybe a little bit faster because X isn't started when it's not used.

---

### Post by PryGuy on 2006-09-03
Thanks but is there a way to keep X running and why this thing happens?

---

### Post by Ramses de Norre on 2006-09-03
I think the reason is that X looks at your screens when it starts up and then looks in xorg.conf which resolutions it has to set for those screens. But when your screen is turned off xorg can't find it and it will use the lowest resolution.

And you can turn your monitor off after X is started with the monitor on, and since you can't use X without a monitor I guess you can always turn your monitor on when you start X. As long as X doesn't start automaticaly as it does now.

And in case you don't like this solution: I have seen this problem on the forums before so there might be a fix for it, use the search function.

---

### Post by PryGuy on 2006-09-03
Thank you! But I will try to do one trick first, I'll leave the 1024X768 as the only resolution in xorg.conf and tell you about the results.

---

### Post by PryGuy on 2006-09-03
It didn't work:(

---

### Post by Ramses de Norre on 2006-09-03
Then just start X from terminal when needed.. It will always have the right resolution and you can turn your monitor back off after it.

I don't see real disadvantages and I'll explain how to do it if you want to.

---

### Post by PryGuy on 2006-09-03
Thanks, but I really want to understand *why* it happens...;)

---

### Post by PryGuy on 2006-09-03
> **Ramses de Norre said:**
> I'll explain how to do it if you want to.Yes, please do!:D

---

### Post by Ramses de Norre on 2006-09-03
Ok first do
```
sudo aptitude install sysv-rc-conf
sudo sysv-rc-conf
```
Then go down to gdm or kdm or whichever display manager you use and disable it with your space bar (So no X under 2 or S).
Press Q to exit.
Now X wont start when you bootup.
To start gdm/kdm from terminal do this:
```
sudo /etc/init.d/gdm start
``` (replace gdm by kdm or something else when needed).
This works too but doesn't give you a login screen so you can't choose anything but the default: ```
startx
```

---

### Post by Mark England on 2007-07-17
I also have this problem and find it very annoying.

I don't want to have to use a Terminal to start X11 each time I startup the machine to get around it as I restart my machine often and booting straight into X Windows is ideal for me... having the monitor off is required sometimes as I leave it off when I go to work and I may just turn the machine on while I run out the door as I'm late etc

I have tried only allowing the resolution I want but that doesn't work, no luck... anyone else got any ideas?

Here's a lame emoticon for y'all to get you started :guitar:

---

### Post by Mark England on 2007-07-26
I found a thread with a fix for this :)


[http://ubuntuforums.org/showthread.php?t=246988&highlight=screen+power+force+resolution](http://ubuntuforums.org/showthread.php?t=246988&highlight=screen+power+force+resolution)

The solution for me was to add the virtical/horizontal sync rates into the Monitor section of the X server conf file

---

