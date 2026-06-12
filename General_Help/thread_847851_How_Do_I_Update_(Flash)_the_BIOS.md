---
title: "How Do I Update (Flash) the BIOS?"
date: 2008-07-02
forum: General Help
---

### Post by .Nate22 on 2008-07-02
Hey everyone!

I think I got a pretty good question for the Ubuntu community to try out for ya'll right here. Okay, so I have a Dell Dimension 4600. It was running Windows, and it sucked. So I upgraded to Ubuntu 8.04. I like Ubuntu, it's fun, great, world peace on a CD..whatever...point is, I am 10 BIOS revisions behind, and for numerous reasons, I must flash my BIOS.

On windows I would simply go to support.dell.com and then pick my computer model, get the BIOS.exe file and BAM! I'm done. Ubuntu, however, is not quite so easy.

I am wondering how I would go about flashing my BIOS using only Linux, specifically, Ubuntu 8.04. If it helps to know, I do have a floppy drive and a CD drive on my computer.

Your thoughts? 

Cheers,

Nate

---

### Post by Ocxic on 2008-07-02
this should help
**[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)**

---

### Post by damoek on 2008-07-03
Does the latest bios release have some functionality that you are lacking? Usually the good rule of thumb with bios upgrades is 'if isn't broke... don't fix it' 

Taking a look at the dell page in specific, all of the bios for the dimension 4600 are optional releases, many with updated support for cpu's that were sold/shipped after the unit was sold and such. If you are using the box as it was sold, i don't believe you will gain much additional functionality in either windows or ubuntu with the upgrade, but if there is something in specific that you are hoping to gain I understand.

I tried on mac os to run the bios exe in crossover (commercial version of wine) I believe it is just a self extracting zip file. You might try to run it in wine, depending on your level of expertise with such things. 

If worse comes to worse, you can have one of your windows friends run the .exe and give you the extracted contents, but i'm not sure if dell does their bios upgrades inside of windows or in a pre boot environment like most others. And you could always find a small 5-8 gig harddrive and install windows if you gotta, just for the upgrade.

Sorry for no solid answer... Just my musings.

---

