---
title: "Repartitioning SanDisk U3"
date: 2008-03-29
forum: General Help
---

### Post by drhou on 2008-03-29
Hi Guys,

I have recently bought a 4GB SanDisk USB with U3 technology and i was hoping to install a whole Ubuntu-Fiesty filesystem onto it, but it has got this annoying U3 thing that I need to get rid off. I've used GParted and it shows that it has got one main partition and 7mb unallocated. If I repartitoned the whole USB into one partition, would I still be able to reinstall U3 onto the USB? (I need it for school, they block many useful programs :-x)

Thanks

---

### Post by Jerry N on 2008-03-29
I haven't tried using qparted to get rid of the u3 junk but if you have access to a Windows machine the u3 remover is a part of the included software.  

Jerry

---

### Post by FuturePilot on 2008-03-29
I'm not sure that you can reinstall the U3 software after removing it. I would suggest wiping it, installing Ubuntu or whatever you're going to do and if you still want something like U3 look into [Portable Apps]("http://portableapps.com/"). It's very similar only it's all open source. :)

---

### Post by oscarmeyer51 on 2008-06-02
FYI --- Just got a 4GB Sandisk Cruzer USB Stick and could not get rid of the US Launcher software within Ubuntu. I had to boot to Windows (dual boot still comes in handy occasionally), download the Sandisk US Launcher removal tool, and run that under Windows XP WHILE the U3 Launcher was running. It reformatted the USB stick after removing the CDFS partition. Fortunately this was all fresh for me and I did not have to pull anything off of it. Sandisk apparently believe that anyone wanting their USB sticks must need all the 'utilities' they plop on to their sticks. Under Ubuntu, the stick never showed both the virtual CD and the remainder of the stick, so I could not remove the virtual CD (read Windows application).

Good luck in however you move forward on this!

---

