---
title: "Grub\ubuntu\vista issues :\"
date: 2008-06-19
forum: General Help
---

### Post by Crayling on 2008-06-19
Hello all, I have a rather weird problem, probably caused by myself and not knowing that much about linux.

First off, I have a system running Vista, I use two harddrives running in sata raid. (dont know what mode, but the mode that gives me better speed)
I tried in vain to make a dual boot of it, with xp, and with ubuntu, to no use. they couldnt recognize my raid partitions...

So, I got my hands on a third hard drive. Thought I could use that for ubuntu, and eventually xp, while keeping vista and all my files.

xp wouldnt install on it, ubuntu did. 
I let ubuntu itself make the neccesary partitions to the new hard drive, and after it was installed I was prompted to restart.

Then I got the

 Grub loading stage 1.5
Grub loading, please wait.....
error 21

>_<

After googling for a while on another pc, I realised it had something to do with my raid. So I went into bios and disabled the raid. just to check if ubuntu would work then. Grub loaded, and here I am in ubuntu.
But I want back to vista and my files :(

What REALLY itches though, is Grub has done something to my ..uh..I dunno, raid drives?

Before I disabled raid, I just tried removing the third and newest single hard drive with ubuntu, so I just had the two hard drives in raid left that I had not installed anything on.

I still got the 

 Grub loading stage 1.5
Grub loading, please wait.....
error 21

I have read about a live cd as well, not sure what exactly that is.. I have the ubuntu cd (the latest version downloaded from the ubuntu site), which I can boot with. My vista dvd is useless at this point, as it can find nothing wrong, and wont let me boot into vista either >_<

And to make things worse, I have no familiarity with linux whatsoever >_<

Any help would be greatly appreciated, I need a way to either get rid of ubuntu and grub in a way that makes my pc boot vista again, or even better make grub recognize my raid and do its job as a bootloader ;)

Sorry if I havent made myself clear enough, just ask and I shall clarify as best as I may.

ps: wow, ubuntu was not as noob friendly as it seemed ;)

---

### Post by Titan8990 on 2008-06-19
You really should do more resarch before jumping in.

Ubuntu and XP did not recognize your RAID set because you did not install the fakeRAID drivers during the installation of either OS. 

Vista no longer boots because you broke your RAID set in your BIOS. In order to fix this you will need recreate your RAID array and reinstall Vista.

RAID0 (which sounds like what you are using) offers very little performance gain for the instability that it adds. I suggest that you don't bother with it anymore.

Personally, I would run a disk scrubber on all the drives and then start over.

Computers in general are not newb friendly outside of the everyday entertainment and internet browsing. For your own sake, read up on things before you go breaking operating systems.

Wikipedia RAID article: [http://en.wikipedia.org/wiki/RAID#Standard_levels](http://en.wikipedia.org/wiki/RAID#Standard_levels)

---

### Post by Crayling on 2008-06-19
Wow, sorta harsh there :P
> **Titan8990 said:**
> 

Vista no longer boots because you broke your RAID set in your BIOS. In order to fix this you will need recreate your RAID array and reinstall Vista.


Vista didnt boot long before i "broke" my raid in the bios.

edit: and yes, after seeing your edit inserted article I can say that I have\had raid0

---

### Post by Crayling on 2008-06-19
Apologies for the bump, but that didn\t exactly tell me how to fix this in a manner that saves my files. And my raid is intact.

---

### Post by qwalton on 2008-06-19
From the sound of it that may not be possible, if your raid array is truely broken recreating it will wipe the drives.

---

### Post by Titan8990 on 2008-06-20
I did not mean to be harsh and for this I apologize. I was just trying to get the point accross that this a mistake that you learn from and hopefully you will do you homework next time. Nearly all of us have had a big foul up such as this at one time or another. Just look at it as a learning experience and move on.

I am no expert on data recovery, which brings up lesson #2: always backup, especially before making changes to your drive.

Whenever you "turned off" RAID that is breaking the RAID set. Whenever you renable it that is an entirely different RAID set that it once was. Therefore there is not going to be an easy way of recovering your data.

---

