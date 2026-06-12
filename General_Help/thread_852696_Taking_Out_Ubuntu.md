---
title: "Taking Out Ubuntu"
date: 2008-07-07
forum: General Help
---

### Post by alex1350 on 2008-07-07
Okay i am migrating to a laptop and i want to know how to take out Ubuntu from my desktop since i will not be using it no more and going to free up space for the windows installation for my sister and other people in my family that use it.

---

### Post by Hyper Tails on 2008-07-07
If you want to remove it from your laptop completely just purchase a windows vista installation cd ( not the upgrade) and install windows.
It'll overwrite ubuntu completely.

---

### Post by alex1350 on 2008-07-07
is there any way without over writing because there is pictures and such on the windows installation.

---

### Post by Phixion on 2008-07-07
Insert the Windows CD, once its booted press R to Repair, this will take you to a recovery console. Choose the installation to repair and type fixmbr to re-write the Master Boot Record.

Then download a partition program for Windows (Partition Magic 8) and remove the Ubuntu partition.

---

### Post by alex1350 on 2008-07-07
Will it delete anything in my windows portion?
Because i want to make sure because my sister has stuff on there and well yeah. She get's very very mad if it's gone. 

Also does a Recovery Disk the same?

---

### Post by Phixion on 2008-07-07
As long as you don't delete the Windows XP partition it'll be fine.

I suggest you backup your stuff before trying this though, better to be safe than sorry.

---

### Post by alex1350 on 2008-07-07
Can someone post a step by step guide to do this. Because i don't want nothing to go wrong. I am a bit worried.

---

### Post by alex1350 on 2008-07-07
It didn't boot the DVD!

---

### Post by alex1350 on 2008-07-07
Is there another Method. It does not Boot From the DVD.
I start up the computer, it doesn't boot the DVD. It just goes to the Dual Boot Menu and also for some reason there is 2 options for Ubuntu well 4. 1 of them is with the last numbers end with 16 and the other is 14. but the other 2 are just safe mode. 
Then it shows 2 other options. One of them is Dell Utility i think and then Windows Vista. 
When i boot Windows Vista, it just goes straight 2 it without the DVD Booting.

---

### Post by L337_K3y5 on 2008-07-07
You have to go into the BIOS and change the boot order to where the dvd/cd drive boots before the hardisk.

---

### Post by alex1350 on 2008-07-07
How do i do that?

---

### Post by L337_K3y5 on 2008-07-07
> **alex1350 said:**
> How do i do that?

Ummm....when you restart your comp. there should be a screen that comes up that tells your comp. manufacturer and at the bottom left there should be some different words, it should say setup or BIOS, and it will also have a corresponding button.  You press the button it says, then you go to a tab labeled boot by using the right arrow, then go down to boot order and press enter.  You use the page up/down keys to change the order, unless otherwise specified.  Then you go to the exit tab, by using the right arrow, then you go down to save settings and exit.  It should boot from dvd then, if you set dvd before HD.  Hope that helps!:)

---

