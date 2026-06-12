---
title: "GRUB got messy..."
date: 2007-03-07
forum: General Help
---

### Post by Alfa989 on 2007-03-07
Hi people!

I've installed Dapper a while ago and the upgraded to Edgy, but every time I've done "something" to the system, a new GRUB entry appeared (now I got 3 Ubuntu/recovery mode options). So how could I fix it so I only have 1 Ubuntu and 1 Windows options?? :)

Another thing that I have a question about is how to make Windows the default boot system: I tried with [gksudo gedit /boot/grub/menu.lst], but I set the number to 9, since that's the last line I got starting to count the first entry being 0, but it doesn't seem to work...:confused: 

Thanks for you help! :)

---

### Post by rsambuca on 2007-03-07
There are a few different methods you can use to get rid of some of those entries from the grub menu.

1.  Remove the old kernels from your system:  Go to the Synaptic Package Manager and search for linux-image.  After you are certain your newest kernels are stable on your rig, you can delete the old ones.

2.  You can simply delete the old entries from your menu.lst file, keeping in mind that they will re-appear the next time you do a kernel upgrade.

3.  You can just place a '#' in front of the lines that you want to hide from showing up on the grub bootloader screen.  You would place the '#' in front of each line that you don't want ie. #title ...#kernel...  #initrd... etc.

After you have made your changes, you can then change the default number to the correct entry for your Windows.

---

### Post by Alfa989 on 2007-03-07
Thank you so much rsambuca!

Now it works perfectly! :)

---

### Post by rsambuca on 2007-03-07
Good stuff!  Which method did you use, by the way?

---

### Post by Alfa989 on 2007-03-08
> **rsambuca said:**
> Good stuff!  Which method did you use, by the way?

Number 3.-, It worked as expected... :)

---

### Post by rsambuca on 2007-03-08
Yeah, that's what I usually do too.  Just keep in mind after your next kernel upgrade, your menu.lst will be updated and so they will all come back.  But it is not often enough to be a big hassle.

---

### Post by Alfa989 on 2007-03-08
> **rsambuca said:**
> Yeah, that's what I usually do too.  Just keep in mind after your next kernel upgrade, your menu.lst will be updated and so they will all come back.  But it is not often enough to be a big hassle.

I'll remember that, thanks... :)

Btw, Every time Ubuntu boots up performs a fsck... Is there any way to turn or off or something?

---

### Post by aminahmadi on 2007-03-19
I want to remove the old kernel, and not only from GRUB menu, is remove completely to harsh? 

are the config files as it mentions shared with the newer kernel and therefore I shouldn't go with REMOVE COMPLETELY?

---

### Post by rsambuca on 2007-03-19
It should be fine to remove the old kernels.  I like to just make sure that I use the new one a bit to make sure it is stable on my system.

---

### Post by Maximus5684 on 2007-03-25
This is my method, and I'd love to hear some comments on it:

1.  Write down the kernel versions you want to remove (such as 2.6.17-10).
2.  Go in to Synaptic and search for the kernel version.
3.  Completely remove all packages that have the word "linux" and the version number in the name.
4.  Go to a terminal and run "sudo grub-update" to update the GRUB boot list.

This is how I remove old kernels.  Just remember, folks, if you accidentally remove all kernels, your machine won't boot!

P.S. I usually leave the latest and the 2nd-latest kernel there JIC.

---

### Post by tomchuk on 2007-03-25
You could also modify the "howmany" option in /boot/grub/menu.lst from "all" to "1". As with the rest of the options for update-grub listed in menu.lst, don't uncomment them. Run update-grub to update the grub menu entries defined in menu.lst. Double check that the options you want are there, as I'm not sure if your windows entry is counted as 1 by update-grub.

This has the benefit of surviving a kernel upgrade, and the new kernel will be the only one on the list (might be worth keeping 2 just in case)

---

