---
title: "Broken Package Doesn't need to be removed"
date: 2007-06-04
forum: General Help
---

### Post by FuZ3 on 2007-06-04
Hey,

Need a little help. I was working on an old dell laptop that one of my friends had got off ebay. They said they didn't care what I did with it as long as I got the wireless plug in card to work. Unfortunately the laptop didn't come with an ethernet card which meant I couldn't get what I needed because they had a wireless card not supported in Ubuntu. 

So I tried ndiswrapper except I had to download everything on another machine and move them over via USB flash drive due to the no internet access thing. First I tried compiling ndiswrapper but alas I haver never got even one thing to compile from source correctly. 

So i got the .deb packages and the windows driver. Installation of ndiswrapper went smoothly but when I got to ndiswrapper-utilities it said that It needed "libc6" older than verson 2.5.5. So I tried downloading that but when installing it told me I already had version 2.5.(ubuntusomething), So I used ```
sudo dpkg -i --force-
``` to get it to work. After that I installed the windows driver and everything worked perfectly. The only problem is that now Apt thinks its a broken package because their are missing dependancies which means that any time it updates/installs new software it removes the package and breaks WiFi. 

Is their any way to either convince Ubuntu that the package is working fine and doesn't need to be removed or in some other way fix this problem?

---

### Post by zvacet on 2007-06-04
I don´t know if it is works but you can try.Go to the synaptic and select package you installed >edit>lock version

I hope it helped.

---

