---
title: "ATI Issues"
date: 2007-09-26
forum: General Help
---

### Post by Job_314 on 2007-09-26
Hey everyone, I'm new to this forum, and even more new to Ubuntu, but I figured what better way to find the die-hard Ubuntu gurus then to look here.

I've recently installed Ubuntu (Feisty) on my PC to replace Vista, and it's working marvelously thus far. The only issue I'm having is enabling my "ATI acceleration driver". I keep navigating to *System > Administration > Restricted Drivers Manager* and checking the box... but for some reason Ubuntu won't let me activate this driver!

So I tried downloading ATI's FGLRX drivers and creating a custom .deb package, but when I keep entering the "--buildpkg Ubuntu/feisty" command it keeps telling me it's an "unsupported architecture". I've tried to compile the package with every other option aswell, and the same error occurs. I know for a FACT, that I'm running Ubuntu Feisty Fawn 7.04, in 32-bit... but the darn thing just doesn't want to think I am or something. I'd much rather just enable the ATI drivers that came with Ubuntu than to get ATI's damn installer compiling correctly, but I'm desperate enough to take just about any solution at this point.

I've also heard people talking about enabling "restricted components", or something like that, but I have no clue as to what that is. I'm very well aware of ATI's disregard for Linux customers, but this is driving me nuts. 

/noob rant

Thanks guys, 
-Austin

---

### Post by sylentdogg on 2007-09-26
This page helped me install my ATI drivers.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by Job_314 on 2007-09-26
See, I've taken a look at that, but the only issue is... I do not have internet on my Ubuntu machine, therefor, the "sudo apt-get update" command is completely useless. I'm currently running up and down stairs between machines to try new options, hehe.

Hopefully there's an option to get this working without internet. I'm able to burn CD's though, so if there are any fixes/updates, I can download them on this PC, burn them, and pop it into my Linux PC.

---

### Post by jocko on 2007-09-26
What graphics card do you have? Which version of fglrx did you try to install?

---

### Post by Job_314 on 2007-09-26
I've got a Radeon X800 Pro, and I've tried to install the 8.40.8, AND the 8.38.6 FGLRX drivers. The card's only a couple years old now, and knowing Linux, it should run without a problem, it's just getting the damn drivers working that's the hard part.

---

### Post by Job_314 on 2007-09-26
**Sorry, double post. My router decided to rebel.**

---

### Post by fumduck on 2007-09-26
well if it gives you hope my card worked fine just by using  restricted drivers.. So maybe it means you need an update.. You might  want to get the internet to it..

Peace and goodluck,
M

---

