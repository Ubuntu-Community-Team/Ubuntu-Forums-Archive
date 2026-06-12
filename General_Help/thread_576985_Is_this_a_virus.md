---
title: "Is this a virus???"
date: 2007-10-15
forum: General Help
---

### Post by FlyinRedneck on 2007-10-15
Hi... i am running Kubuntu feisty... after not even a day of using it, it crashes. I restart the computer and it goes to a check disk thing... it then gives me a few errors then it says.

Apt-get not present
you can install apt-get by typing sudo apt-get install apt

i find this sort of funny but i really dont like it at the same time.

is this a virus? 

what can i do to fix it?

---

### Post by milton1 on 2007-10-15
virus, not likely. Massive glitch, definitely. I'd say try the install command it gives you (maybe with the install cd in and mounted), and see what it does. if it does nothing, you can search the install cd for a .deb package for apt and install it manually using ```
dpkg -i <package name>.deb
```

good luck

---

### Post by milton1 on 2007-10-15
on second reading of your post, I notice that this started after the system tried running a disk check. I would not be surprised if your hard disk were about to kick the bucket. It could well be that the part of the disk where apt resides has already corrupted.

---

### Post by wpshooter on 2007-10-15
Have you thought about running a disk analysis on your hard drive to see if there may be a hardware problem ?

---

### Post by FlyinRedneck on 2007-10-15
well...... i tried what you said.... i got the same error message back... when i tried dpkg it replied:

dpkg not installed to install dpkg type sudo apt-get gpkg

sorta circular... i think it is a hard drive problem...

previously i was getting write protected errors when downloading some torrents.

thanks guys for the help though.

by the way. does anyone know where i can get some cheap hard drives?

---

### Post by angryfirelord on 2007-10-15
If the torrents aren't working for you, then get a Ubuntu iso from a http or ftp server.

As for hard drives, I like [http://www.newegg.com/]("http://www.newegg.com/"). I got my PC parts from them. However, don't order a new one yet until you're absolutely sure it's not a bad burn/install.

---

### Post by FlyinRedneck on 2007-10-15
I know for a fact it is a bad hard drive... i am not completely computer stupid. It was running fine without any errors untill some suspicious stuff happened. For about a month i thought the drive was going bad i was just trying to use it untill it died. As for the torrent stuff, i have quite a bit of boot cd's already Ubuntu, Kubuntu, Knoppix, DSL,ect. so torrents arent my problem.

thanks for the link though.. i think i will get a few new hard drives.

Thank you for all of your help.

----------------------------

Flyinredneck

---

### Post by -grubby on 2007-10-15
not a virus. You should get a new hard drive

---

### Post by bodhi.zazen on 2007-10-15
> **FlyinRedneck said:**
> Hi... i am running Kubuntu feisty... after not even a day of using it, it crashes. I restart the computer and it goes to a check disk thing... it then gives me a few errors then it says.

Apt-get not present
you can install apt-get by typing sudo apt-get install apt

i find this sort of funny but i really dont like it at the same time.

is this a virus? 

what can i do to fix it?

> **FlyinRedneck said:**
> I know for a fact it is a bad hard drive... i am not completely computer stupid. It was running fine without any errors untill some suspicious stuff happened. For about a month i thought the drive was going bad i was just trying to use it untill it died. As for the torrent stuff, i have quite a bit of boot cd's already Ubuntu, Kubuntu, Knoppix, DSL,ect. so torrents arent my problem.

thanks for the link though.. i think i will get a few new hard drives.

Thank you for all of your help.

----------------------------

Flyinredneck

OK, I think you have your answer then.

I am closing this thread to keep form degenerating into a "viruses on linux" thread.

If you wish to discuss viruses on linux : [http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

