---
title: "Help with Ubuntu LiveCD"
date: 2007-04-04
forum: General Help
---

### Post by ben339 on 2007-04-04
Hi,
I have Ubuntu 5.04 liveCD which I tried to use, however it doesn't detect my CD drive...  I tried all the drivers on the CD and none of them work.  I have a TSSTcorp CD/DVDW TS-H653L drive which came with my HP desktop computer.
This isn't new - I have had problems with other boot CDs as well, but I still don't know what to do!

I would appreciate any help with this.

Thanks!

---

### Post by amohanty on 2007-04-04
What's the problem, does it boot off of the cd or not?

If not, you may have to set up the cd as the first boot device in your BIOS.

AM

---

### Post by ben339 on 2007-04-04
It boots the CD - it starts to load, but then says that it can't access the CD driver.  It then asks if I want to insert a floppy with the driver, but I don't have it, so I choose no.  Then it asks if I want to choose from a list of drivers that come with the CD, and those don't work either.
FInally, it says it can't run the liveCD because it can't find the CD drive.

Weird, but I don't know what to do :(

---

### Post by amohanty on 2007-04-04
Can you post the exact message???
AM

---

### Post by ben339 on 2007-04-04
Yes, I just tried it again and this is exactly what happened:
Everything goes fine until it reaches the detecting hardware step - then it says "NO COMMON CD-ROM DRIVERS DETECTED".

It then asks "LOAD CD-ROM DRIVERS FROM A DRIVER FLOPPY?", and I marked no.  Then it asks "MANUALLY SELECT CD-ROM MODULE AND DEVICE?", and I chose yes.  It displays a list of drivers (too many to list).  After trying each one, it said "INSTALLATION STEP FAILED.  THE FAILING STEP IS:  DETECT AND MOUNT CD-ROM".

After that it just gives me a list of options but none of them work since this step failed.

---

### Post by ben339 on 2007-04-05
Does nobody know how to help me with this?

---

### Post by amohanty on 2007-04-05
Do you have access to another cd drive?

You could boot off of a floppy and then launch the installer from the cd but its very complex and you may run into the same problem again.

Best bet - get another cd.

AM

---

### Post by ben339 on 2007-04-05
How will getting another CD help?

---

### Post by amohanty on 2007-04-05
Sorry I meant drive. The problem seems to be that either the drive has problems with rewritable media or burned cds (hence probably the problem with other boot cds) or that the drive is too new for the loader. 

Are you just trying to run the live cd or install it. If you are trying to install it, you could try the alternate install cd and try and click on continue multiple times to see if you can get to the install menu.

AM

---

### Post by ubuntu27 on 2007-04-05
That compatibility problem may be resolved by trying a NEW version of Ubuntu. :)

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

