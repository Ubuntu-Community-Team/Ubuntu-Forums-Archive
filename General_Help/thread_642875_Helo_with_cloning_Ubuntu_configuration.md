---
title: "Helo with cloning Ubuntu configuration"
date: 2007-12-17
forum: General Help
---

### Post by zsugiart on 2007-12-17
Guys, 

I want to make a backup of my system's configuration. Not the data, because I have all of my data on the network (got a P3 machine turned into a home file/misc server), 

At this point, I just need a way to back up the operating system along with the packages that I have installed on it into a DVD. 

Ideally I'd like to be able to boot from this DVD to restore my Linux configuration. Not sure about using this DVD to install the linux on a separate machine, that'd be the idea of a distro isn't it?

Any pointers as to where tpo look?

---

### Post by viking777 on 2007-12-17
Disk imaging is the safest way to do this although this copies everything not just configurations. 
Some people swear by a seperate /home/ folder (which contains most of your configuration options) although I have tried this and found it to cause nothing but trouble.
Some people copy configuration files from the home folder and then copy them back again (they mostly end in 'rc' as in 'krusaderrc' ) I have never found that this is any use either.
So imho your best way is imaging. The Linux tool for this is 'partimage'  although it works it is not exactly user friendly (and I am being kind by restricting myself to saying that). Do you have any other tools available like Ghost or TrueImage? Although they are windows programs they run from cd so once you have the cd you don't need windows to run them any more. They cost money of course, but if you have them lying around I would use those, otherwise have a wrestle with partimage.

---

### Post by louieb on 2007-12-17
Since your data is separate from your  Ubuntu install probably the easiest way to go is use **partimage **  - its available on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") 
Just create an image file then copy it to DVD. 
Pretty good how to here [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
1st 3 steps are about using the Ubuntu live CD. IF you get the System Rescue CD you can start in step 4.

---

### Post by staticvoid on 2007-12-17
try reconstructer

---

