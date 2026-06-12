---
title: "Ubuntu will only load in recovery"
date: 2007-05-29
forum: General Help
---

### Post by nrich61 on 2007-05-29
Well, ive been searching for an answer in this forum and in google for days now. Heres the deal.


When i boot up and choose the regular kernel in Grub, i see the numbers at the bottom of the screen 1000000x......  (and some other crap)  and then the screen goes black and does nothing, if i choose recovery mode then it does its thing to the command prompt and i can access the GUI from there. 

I also had the same problem when trying to install, to be honest, i have no clue how i finally got into the GUI via the CD to install Ubuntu, but i did. 


Now to fix this i have tried everything i could find

I have tried to load the newest Nvidia drivers, but cant, apparently i have to do it from the command prompt (sorry i dont know all the terminology for linux :D, the area that looks like DOS), so when i do that, the driver program says that i have to setinit 3 (from my limited understanding, sets security access level to 3), or something like that (forget the exact command). So when i use that command it boots into the GUI for some odd reason and i cant run the driver program in Ubuntu........ its a vicious fricking circle.

I have also tried running the xserver-xorg (i think that was it, the thing that sets up your graphic settings and what not). I have done this a number of times to try different settings.

I have tried a couple of different alterations to the load commands in Grub. one of which was setting mem=512m, another was a change to the kernel line in grub that changes a little of the end of the command and adds=771, and a couple others i dont remember.


I'm getting really frustrated, this is the first time i have even glanced at Linux, Windows has always worked well for me, but i wanted to try this out after seeing it on my brother in-laws computer and helping him figure out some stuff on it. 



My system specs are as follows:

Intel E6600
(ONLY ONE) EVGA 8800GTS 640mb Superclocked  (superclocked on this one is how it comes from the factory ;D)
2 gigs of Mushkin DDR2 6400, i have another two, but i cant get all four working in vistas right, so only two in the system right now.
i have a 150 gig raptor with windows on it, a 150gig for misc storage, and an 86 gig that is formatted and has ubuntu installed on it.
MSI P6N SLI mobo
Samsung 240bw (something like that, its the 19 inch LCD flatscreen either 2 or 4 ms)
X-Fi Fatality (havent even tried to install the sound drivers for this yet)



Please help me -.-

thanks

---

### Post by kuja on 2007-05-29
Given your situation, you'll probably want to do all of this in the recovery mode console.

Installing the nvidia drivers is probably a good start, to do so in the console run this command: ```
apt-get install nvidia-glx-new  && nvidia-xconfig
```

Another thing worth looking at is grub and usplash (the splash screen ubuntu shows while booting). Perhaps it doesn't like usplash  (it itself has caused plenty of people plenty of problems. 
Try this to disable usplash:

```
nano /boot/grub/menu.lst
```

It'll bring up a fairly length file, now look for this section:

[quote]
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
**# defoptions=quiet [color=red]splash[/color]**

Remove the word splash, and save the file by pressing ctrl + x.
To apply the above changes in the grub file, run this command:
```
update-grub
```

Give this stuff a go, I hope it'll do the trick, guess we'll see eh? 

On another side note, you won't be able to get the X-Fi card working at all as Creative has released neither drivers nor specifications for  the X-Fi series cards, though they do say they'll be releasing them sometime later.

---

### Post by nrich61 on 2007-05-29
thanks ill try it as soon as i get home :D.

---

### Post by nrich61 on 2007-05-29
so the second part where you edit the menu.1st   when i go into the file to edit, there is nothing there, no text, nada, its all blank!

---

### Post by kuja on 2007-05-29
o.O odd ... sitting here and looking it's looking like you mistook the l in lst for a 1 as opposed to a lower cased L. Could that be it?

---

### Post by nrich61 on 2007-05-30
wait... so is it a lower case L or is it a 1?    i tried it with a 1.

---

### Post by kuja on 2007-05-30
lowercase L

---

