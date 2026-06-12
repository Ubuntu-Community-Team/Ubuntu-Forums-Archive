---
title: "i dont want to hate ubuntu.."
date: 2007-02-28
forum: General Help
---

### Post by espanol911 on 2007-02-28
hi guys,
i really have loved ubuntu, and i have installed it on my laptop beside windows XP, and started to get well with it, but after that, there lots of problems came in.:( 

i have instaled ubuntu 6.10,and in the start up it shows me that my computer sysem has 2 of the same version of ubuntu has been repeated itself in the start up menu as it showing in the picture in the attachment ( i made it look like my laptop start up menu as i dont know how to take a snapshoot of it).

and also when i wanted to start the ubuntu it takes long, and i have count the time of it starting which it takes around 3 minutes to start up,and i dont know if thats normal.
also when i wanted to shout it down, it really takes soooo long to shout down and never saw it shut down since i have installed it, and the last time i have count the time when it shots down and it took more than 20 minutes and it still not shouting down, so i usually when i wanted to close it, i just press and hold the start button till it shout down, and its really different when i wanted to restart it as it restarts normally.

when i start ubuntu, my laptop proccessor goes high and i can hear the laptop fan from a distance, and it got so hot too. as my laptop has a good specifications.
i really dont know if that normal or not, but if its not can somebdy help me with it please?:confused: 

i dont want to format my laptop and install it again, but if i do, i cant guarantee that it will work well and dont get the same problems.

---

### Post by llamakc on 2007-02-28
> **espanol911 said:**
> hi guys,
i really have loved ubuntu, and i have installed it on my laptop beside windows XP, and started to get well with it, but after that, there lots of problems came in.:( 

i have instaled ubuntu 6.10,and in the start up it shows me that my computer sysem has 2 of the same version of ubuntu has been repeated itself in the start up menu as it showing in the picture in the attachment ( i made it look like my laptop start up menu as i dont know how to take a snapshoot of it).




Those are not two versions of Ubuntu. You have one version of Ubuntu. Your one version of Ubuntu has multiple kernels to start from (boot with). This is important and a feature. If you so choose to hide the menu, that's possible. If you so choose to edit the menu and have less options, that's possible.

No worries with this point. I don't own a laptop, so somebody else may come along to help. Cheers.

---

### Post by Tobster on 2007-02-28
i never had any problems like that.  Did you use Ubuntu default recommendations for partitioning the hard drive during install?  There a screen that tell you have much space Ubuntu should take for a dual boot.

Did you tell Ubuntu that you wonted a dual boot or did you do it manually?

There are people on here that have far greater knowledge then me but I can see how software can effect the CPU or the fan I am kind of interested to increase my knowledge.

It might be that you Ubuntu disk is faulty.  I tend to get mine from an 'Official Source' from Conical or pay £2 or £3 from an official supplier but of course with any product there always a risk of getting a faulty one in the same way that you can buy a faulty item from a job and not realized until your home

---

### Post by Tobster on 2007-02-28
i never had any problems like that.  Did you use Ubuntu default recommendations for partitioning the hard drive during install?  There a screen that tell you have much space Ubuntu should take for a dual boot.

Did you tell Ubuntu that you wonted a dual boot or did you do it manually?

There are people on here that have far greater knowledge then me but I can't see how software can't effect the CPU or the fan I am kind of interested to increase my knowledge.

It might be that you Ubuntu disk is faulty.  I tend to get mine from an 'Official Source' from Conical or pay £2 or £3 from an official supplier but of course with any product there always a risk of getting a faulty one in the same way that you can buy a faulty item from a job and not realized until your home

---

### Post by espanol911 on 2007-02-28
well, i have followed the installation instructions step by step, and i have used Ubuntu default recommendations for partitioning the hard drive as it show in the attached picture ( i have choose the first one).
but the only one thing that i have did is that i have downloaded the ubuntu 6.10 version from the Ubuntu site and burn ISO on a DVD, so then i installed it in a dual boot steps.

---

### Post by Tsen on 2007-02-28
As stated earlier, those are just multiple kernels and only one OS.  It's not using more space (well, a negligibly larger amount).
If you really don't want it to show up like that, you can edit it out.
Go to /boot/GRUB/menu.lst, and at the bottom of the file it'll have entries for all of your OS's.
To edit it, you'll have to run it using something along the lines of 
gksudo gedit /boot/GRUB/menu.lst

---

### Post by espanol911 on 2007-02-28
well, as i understood that the multiple kernels are normal, so i will go with that.
but as am a really new in ubuntu, how can i go to:
 /boot/GRUB/menu.lst 
and 
gksudo gedit /boot/GRUB/menu.lst

 you mean when the system starts up or from the terminal?

and now what shall i do with the so slow start up and the never shout down?

---

### Post by Tsen on 2007-02-28
I don't know about the slow start up, but there are some guides to optimizing boot times for Ubuntu I think.  Try googling it. 
As for how you'd edit it, just go to a terminal and try typing that.  It should bring up the file.  I think I messed it up earlier, though--it should be:
```
gksudo gedit /boot/grub/menu.lst
```
(No caps on grub, it's case sensitive)
Then just delete the -10 kernels and leave the -11's and memtest there.

---

### Post by espanol911 on 2007-02-28
really thanks for the suggestions and help.

---

### Post by PARO on 2007-02-28
You can also get rid of the old kernal image when you get a new one.  I've done that before via synaptic. I had those that you have, generic plus 386 versions, so 8 or so Ubuntu options... it felt a little excessive, but some things have a linux-image-386 dependancy I guess.

---

