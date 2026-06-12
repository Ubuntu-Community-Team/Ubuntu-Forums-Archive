---
title: "Higher Resolution With Nvidia Legacy Driver"
date: 2007-08-13
forum: General Help
---

### Post by Mark76 on 2007-08-13
Everytime I enable the Nvidia legacy drivers so that I can use programmes that depend on OpenGL I end up with a screen resolution of 800 x 600: which would be nice if it was 1995.  How do I change it to a higher res?

I'm, erm, using Gutsy.  I know I shouldn't be but it's been okay so far.

---

### Post by Mark76 on 2007-08-13
It's openGL I need help with, it seems.  I just can't get it to work :(

My card is an Nvidia Riva TNT2

---

### Post by Bezvardis on 2007-09-29
I have the same problem. Does anybody know how to fix this? Some time ago I kind of managed to find a solution, but then some upgrades or updates of the system destroyed the changes that I made, so I gave up. I also hoped that maybe this issue would be somehow dealt with when new releases of Ubuntu come out, but this has not happened :-(

---

### Post by sdn8904 on 2007-10-04
Hello. I've got the same problem as you. Before I install the Legacy Driver, I used a screen resolution of 1024X768. but now I can choose only between 640X480 and 800X600 resolutions. I hope someone has the solution for this problem. Sorry for the English :)

---

### Post by Mark76 on 2007-10-04
Xubuntu seems to have much better support for the card than the other main *Buntus.

---

### Post by themoebius on 2007-10-04
Probably something is getting changed in your xorg.conf. If you're using the nvidia drivers, you can run nvidia-xconfig (i think thats correct) and it should let you configure your monitors. You can also edit your xorg.conf yourself and add the resolutions you want to the ModeLines. you might also need to manually enter the horizontal and vertical sync rates which are specific to your monitor so xorg knows how far it can push it. There are many tutorials out there for this kind of thing.

---

### Post by sdn8904 on 2007-10-05
See those links

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)
[http://ubuntuforums.org/showthread.php?t=467482](http://ubuntuforums.org/showthread.php?t=467482)

In my case, it was a problem with HorizSync and VertRefresh. When I put the correct values, and restarted, I was able to choose 1024X768 :)

---

### Post by Mark76 on 2007-10-05
:)

---

### Post by romeograham on 2007-10-08
I have a similar problem, but now i'm stuck in the command line interface part (where you go: sudo invoke-rc.d gdm start) and I can't start.  I have been following instructions from a post on installing nvidia drivers the "right and easy way".

 I get a message about my xconf (I think) not being configured right.  It shows be a bit of information (that of course I don't understand) then goes back to the prompt.

 It says to restart my GUI after I fix the xconf.  How do I do this?

BTW, I have just installed 7.04 for the first time, and am completely new to the Ubuntu world.  I think I love it though!

But I want 1600 x 1200 resolution!

Thanks

---

### Post by strikton on 2007-10-08
Change the following section in xorg.conf in /etc/X11 

[I]Section "Monitor"        
    Identifier    "Generieke beeldscherm"
    Option        "DPMS"     
    HorizSync    30-80
    VertRefresh    50-85
EndSection[/I]

Don't worry about the description of Identifier, yours is probably in English.
You only have to add HorizSync and VertRefresh. It's because these parameters are missing X defaults to the wrong screensizes. The numbers for both parms depend on your screen, but should be available in the documentation of it. When not do some trial and error. I think this problem appeared with the introduction of Feisty Fawn and seems still to be unsolved. By the way, in this release I constantly had problems with my legacy card. Looking forward to the next realease....

---

### Post by romeograham on 2007-10-08
Thanks Strikton, I'll give this a try.

Funny that the first thing I wanted to mess with after my first install is the resolution!  

My machine is about 5 years old so I'm not really surprised that I'm having a bit of trouble.

Thanks

---

### Post by dcstar on 2007-10-09
> **romeograham said:**
> I have a similar problem, but now i'm stuck in the command line interface part (where you go: sudo invoke-rc.d gdm start) and I can't start.  I have been following instructions from a post on installing nvidia drivers the "right and easy way".

 I get a message about my xconf (I think) not being configured right.  It shows be a bit of information (that of course I don't understand) then goes back to the prompt.

 It says to restart my GUI after I fix the xconf.  How do I do this?
.........
```
sudo /etc/init.d/gdm restart
```

[http://ubuntuforums.org/showthread.php?t=428968](http://ubuntuforums.org/showthread.php?t=428968)

---

### Post by alegucu on 2008-03-04
Go to System>Administration>Screens and Graphics>Model there choose the generic one from the list and then chose in the generics the resolution you wish add it and test it of course is not gonna work, then choose again your original model in the screen and try to open the resolutions now should give you the option of a higher resolution.

---

