---
title: "Strange behaviour from Desktop when firefox running"
date: 2015-09-22
forum: General Help
---

### Post by pages on 2015-09-22
Hi all , 

I've a very strange issue regarding FF. 
Essentially after an unspecified amount of time , the OS seems to only recognise the FF window as being the only one to interact with. 
For example I can't click or interact with any of the side panel apps or the top right corner ( time /sound etc)

Now if i use Alt tab etc I can bring up the other windows and interact to a degree : For example if i alt tab to a terminal anything i type will appear on the terminal but any mouse interaction will "go through" it and interact with the browser behind it.
Just to be clear it's only the browser tabs and what's on the web page that I can interact with. I can't even close the window / minimise it  unless i use keyboard shortcuts

What i've been doing to "solve" the problem has been to Ctrl + alt + F1 
and running ```
sudo service lightdm restart
```

This isn't really a solution since I do a bit of coding so I'll always have firefox open when I'm googling help and it's really annoying to be distracting yourself with these "Breaks" every so often and trying to get back into the zone


Running 14.04

EDIT: 
JUst to be clear I can't say for certain that it is firefox which causes the issue just it seems to be very related.
Also adding in system specs since I couldn't because of issue when writing the post 
Memory 7.7 GiB
Proc      Intel® Core&#8482; i7-4770K CPU @ 3.50GHz × 8 
Graphic  Gallium 0.4 on NVE4
OS        64-bit

---

### Post by Vladlenin5000 on 2015-09-22
> **pages said:**
> Graphic  Gallium 0.4 on NVE4


^^^
This means you have a Nvidia graphics card _and_ you're using the default open-source (community) driver. For better performance and in order to avoid issues similar to the one you described you should install the proprietary nvidia drivers. 
System Settings > Software & Updates > Additional Drivers (the rightmost tab). Allow a few moments for system checking and you'll be presented with a list of available drivers. Try the recommended one. Reboot & Test

---

### Post by pages on 2015-09-22
Ok seems this might have been the issue ? Haven't had any more repeats of it since added the drivers cheers

---

### Post by Vladlenin5000 on 2015-09-22
Yours is a very new hardware for which the default driver at least provided video which isn't always the case. But then other issues occur as you know already.

---

