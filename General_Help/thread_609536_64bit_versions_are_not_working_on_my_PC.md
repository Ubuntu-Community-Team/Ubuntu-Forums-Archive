---
title: "64bit versions are not working on my PC"
date: 2007-11-11
forum: General Help
---

### Post by heatblazer on 2007-11-11
I have Core2 DUO e4400 cpu and I wanted to try the 64bit ubuntu 7.10.I`ve burned it with k3b and the CD is ok but when I boot from it , after the loading bar it stops.When I try to open it with synaptic packaga manager it tells me that it`s not a software cd,however it shows everything inside the CD.I`ve tried again with ubuntu 6.06 64bit and kubuntu 7.10 64bit but it was the same.What`s the problem?Is it olny for AMD 64bit?:confused:

---

### Post by PmDematagoda on 2007-11-11
You can try the Alternate CD to see if it can solve your problem. 

BTW, could you post the full specs of your PC?

P.S. The AMD64 bit version of Ubuntu is also for Intel processors, there is no "EM64T" bit version of any OS, this is because AMD first introduced 64 bit which Intel followed up with an almost exact replica.

---

### Post by heatblazer on 2007-11-11
INTEL c2DUO e4400 , ASROCK - 945 GLAN , 2G RAM , ATI x800xl , 2 HDDs - 80G Seagate , 320G seagate.
 Not a single 64 bit version is working :(

---

### Post by PmDematagoda on 2007-11-11
> **heatblazer said:**
> INTEL c2DUO e4400 , ASROCK - 945 GLAN , 2G RAM , ATI x800xl , 2 HDDs - 80G Seagate , 320G seagate.
 Not a single 64 bit version is working :(

I would say that your problem is the ATi x800xl, I do know that it works on your 32 bit Ubuntu, but it could be that ATi's 64 bit driver is even less reliable than their 32 bit one. But anyway, why don't you give the Alternate CD a try, that way you can see if it's your VGA card that's causing the problem or if it's some other component of your system.

---

### Post by heatblazer on 2007-11-11
Thanks a lot.I think you are making sense.I know that older versions had problems with the ATI drivers.But why the synaptic can`t open the CD ... this doesen`t make any senses.I`ll try again with later versions 8.xx probably :)

---

### Post by PmDematagoda on 2007-11-11
About your Synaptics problem, I believe it should be because of the fact that the packages are meant for only 64 bit Ubuntu. The 64 bit version of Ubuntu can run and install 32 bit applications using the 32 bit libraries, but this does not apply to Ubuntu 32 bit. Or it could be because you have specified the incorrect name in the sources.list file, for example, the one in mine is:-

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release Candidate amd64 (20071010)]/ gutsy main restricted

```

But I do not think you can use 64 bit packages on Ubuntu 32 bit anyway, so it would be futile to try.

---

### Post by heatblazer on 2007-11-11
Thanks a lot,you`ve been of a great help.Now I know that the VGA is the real problem.Thanks :) let`s hope that they`ll fix the problem because I want to run a 64bit OS on my system and I have no intention of buying nvidia just for that :)

---

### Post by PmDematagoda on 2007-11-11
I was happy to help:). 

P.S. Your wish for using Ubuntu 64 bit is going to be satisfied, maybe faster than you think since the drivers are now open-source which means that the entire Linux community can help in making the drivers better.

---

### Post by heatblazer on 2007-11-11
That is awesome!I am looking forward to see that :) It`s indeed a great new!

---

### Post by cotcot on 2007-11-11
If ATI is the problem than it should be possible to boot with vesa in xorg.conf instead of fglrx ?

---

