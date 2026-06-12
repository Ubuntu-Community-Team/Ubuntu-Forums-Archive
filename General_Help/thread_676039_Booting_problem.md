---
title: "Booting problem"
date: 2008-01-23
forum: General Help
---

### Post by kgwurth on 2008-01-23
I am using gpartd in order to back up my Ubuntu system. I do this on a weekly basis by booting from the live gparted cd.

I have the disk space so for me it's the easiest backup solution.
My Ubuntu is on drive 1 partition 2, my backup partition is on drive 2 partition 2.

The boot loader is pointing to disk 1 partition 2.
For some reason when I first turn on my machine what it boots is the backup partition on drive 2.
The only way I can tell is because right after it boots I get prompted with a whole bunch of updates. Then when I go in and look at my home directory I see that my latest directories and files do not exist.
I then just re-start and it boots the correct partition.

Has anyone run into this problem?  Is there any solution to keep the backup partition from booting?

Thanks for your assistance

Karl Wurth

---

### Post by jeffus_il on 2008-01-23
I am sure your problem is with grub, you may have multiple copies of grub on your machine, which disk is the bios booting from? Rerunning grub-install with the correct parameters will fix your problem.

---

### Post by kgwurth on 2008-01-23
The bios is booting from drive 1.
I will try re-installing grub.  I have Vista in drive 1 partion 1 but don't use it. Soon as I fix this problem I plan on deleting vista. 
I have vmserver running with xp pro client that handles the things I can't do under Ubuntu yet.

Thanks
Karl Wurth

---

### Post by kgwurth on 2008-01-23
Now that I think about it, I did at one time try to install Ubutu on that drive and had Grub install intself there on the MBR. I guess all I need to do is to wipe out the MBR on that disk

Would that work?

Thanks

---

### Post by jeffus_il on 2008-01-23
You can do that, you may run into a problem if the remaining grub points to a non existent partition, but this is reparable using the livecd and running grub-install from a terminal.

---

### Post by kgwurth on 2008-01-23
OK
Thank you sir

---

