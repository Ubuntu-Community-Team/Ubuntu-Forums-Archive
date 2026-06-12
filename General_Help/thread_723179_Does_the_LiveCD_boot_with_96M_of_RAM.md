---
title: "Does the LiveCD boot with 96M of RAM?"
date: 2008-03-13
forum: General Help
---

### Post by steve196 on 2008-03-13
I have an old  laptop. The 7.10 livecd does not boot there. It ends with a black screen and a cursor in the corner.
Now my laptop has 96M of RAM which is far below the requirements, but i have a swap partition on it and with that it should be more than enough. 
Can it still be, that the lack of RAM is at fault, or must it be something else?

---

### Post by taurus on 2008-03-13
It won't boot with only 96MB of RAM.

---

### Post by Cadmus on 2008-03-13
Hmm, 96MB is a bit low for regular ubuntu.

If you need a livecd (as opposed to an installer) you may have to look at Damn Small Linux and family, they're a bit thorny with laptops but the answers are out there. 

If you just need to install I know fluxbuntu can work on 96MB, Xubuntu might but Im worried about perfomance levels.

---

### Post by steve196 on 2008-03-13
fluxbuntu is installed and works. The only problem is, it is not really self explaining and has hardly any documentation. Do you know something really mainstream, that works on 96M?

---

### Post by Cadmus on 2008-03-13
To be honest with memory prices the way they are I'd be sorely tempted to suggest buying more memory, but that feels like surrender ;)

Xubuntu says it can only run on more than you currently have. Fluxbuntu is as you rightly point out still in it's infancy, but I can see things improving shortly (old hardware and knowledgable gurus go together very often).

At the risk of going off-topic what's the biggest prolem you have at the moment? Maybe if we can help get you started you can carry on from where you are now.

---

### Post by Therion on 2008-03-13
96MB? A single 128MB stick and 32MB being borrowed by onboard graphics, I'm guessing?

Even assuming you *could* boot using that config I think the bigger question is would you really *WANT* to?

---

### Post by trippinnik on 2008-03-13
With that amount of ram, you'll really want to use one of the lightweight WM, and also find light weight apps too.  There may not be much documentation for fluxbuntu specifically but a lot of Ubuntu documentation will still apply.  You could also try E17 or enlightenment (e16).

---

### Post by sandysandy on 2008-03-13
u could give the alternate CD a try. Live Cd will require minimum 256 to 400mb RAM.

better still try Xubuntu alternate CD. have a look at this link. it says 64 mb is required for install, but higher mb for running.

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

> 
Minimum system requirements

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM. 

gOS is based on ubuntu but with enlightenment which is not so heavy on resources. i am not sure however if they have the alternate CD.

otherwise damm small linux and puppy linux are there.

regards

---

### Post by steve196 on 2008-03-13
Thank you!
The alternative install cd worked (plain ubuntu). The installed system on the harddisk also works but is really slow and always on swap.
I think, the livecd just failed to find the swap partition and therefore crashed.

---

### Post by sandysandy on 2008-03-13
> **steve196 said:**
> Thank you!
The alternative install cd worked (plain ubuntu). The installed system on the harddisk also works but is really slow and always on swap.
I think, the livecd just failed to find the swap partition and therefore crashed.

happy to know u could install with the alternate CD.

u may also consider increasing ur SWAP size since the RAM is less.

increasing swap can be done with gparted CD. 

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

boot into gparted live CD and u can resize ur SWAP partition. take backup prior to resizing any partition.

regards

---

### Post by CREEPING DEATH on 2008-03-13
You could try the [Debian Live]("http://debian-live.alioth.debian.org/") XFCE CD.  I'm using Debian XFCE (installed) on a Pentium-MMX 233 Mhz machine with 64 MB RAM.

CD

---

### Post by s.jesudasan on 2008-03-14
> **steve196 said:**
> I have an old  laptop. The 7.10 livecd does not boot there. It ends with a black screen and a cursor in the corner.
Now my laptop has 96M of RAM which is far below the requirements, but i have a swap partition on it and with that it should be more than enough. 
Can it still be, that the lack of RAM is at fault, or must it be something else?

i think u need 190 mb of ram
i read it somewhere

---

