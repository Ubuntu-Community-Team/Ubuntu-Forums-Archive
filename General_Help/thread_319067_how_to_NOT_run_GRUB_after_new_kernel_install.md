---
title: "how to NOT run GRUB after new kernel install"
date: 2006-12-15
forum: General Help
---

### Post by fatsheldon on 2006-12-15
Hi, i have ubuntu installed and running and think it's great.  I "triple boot" it with windows and gentoo.  When ubuntu decides it wants to install a new kernel image (which works great) it re-runs grub-install naturally.  Well, it adds some entries including the new image and a "safe mode" and memtest86.

Is there to make it NOT do that?  can i somehow configure it to only add the one entry and take out the old image entry?  Perhaps i can just shut it off completely and do it myself?

the problem is really that i often start my machine remotely via WoL.  and if a new image is installed the night before and there are new entries in menu.lst that mix up the DEFAULT booting OS then I'm left to guess (not to mention that my current setup would leave the DEFAULT being the old kernel image which generally doesn't even work due to the nvidia drivers getting mixed up (don't quote me there... haven't tested that in a while))  I'd rather not have that happen.  

for now i just make sure to edit menu.lst and re-run grub-install after each kernel install, but it'd be nice to configure the installer and then it'd only need to be run once.

sheldon

---

### Post by lingnoi on 2006-12-15
Type 

```
sudo gedit /boot/grub/menu.lst
```

In that file there is an option for how many kernels you want kept after an upgrade. Its probably best just to keep 1 extra through just in case there is a problem but then thats up to you.

You will find a lot of other great options too just read the comments in the file and you should be able to figure it out.

:D

---

### Post by Herman on 2006-12-15
Hello fatsheldon, 
I agree with what lingnoi said and if you want to see that illustrated, click on the link that follows, 
howmany=.......[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#_howmanyall")

Personally, I like to leave mine set at 1, just for the sake of tidiness in the Grub menu. 
I do not believe in uninstalling any old kernels with synaptic though. I just leave them in place. They don't take up very much hard drive space, and can be booted from the Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") if that ever became necessary.

Click my third sig link for more on Grub in Ubuntu.

Regards, Herman :D

---

### Post by steve.horsley on 2006-12-15
You can try this if you like. It's what I do.

Firstly, I have a "master" linux installation on a small partition. This has grub installed on the MBR in ths usual way. I never change or update this installation, and only use it as a rescue system when the others are broken.

Then every other OS has a bootloader on the system partition instead of on the MBR. The easiest way to do this is to install normally (GRUB to the MBR) and then boot it and run 
**sudo grub-install /dev/hda3**
or whatever your root partition is. 

Now you need to use the rescue cd to reinstall GRUB for the "master" Linux. Boot the rescue CD, open a shell on the master linux and issue the command:
**grub-install /dev/hda**
which puts its GRUB on the MBR. Now you need to edit this one's menu.lst so that it chainloads the partition with the second / third Linux partition instead of directly loading the kernel. Chainloading (same way as with Windows partitions) will then load the local partitions's GRUB, which will offer all the rescue mode, memtest etc. But you can set the timeout on this local GRUB down to 0 os 1 seconds so it's not intrusive.

---

### Post by fatsheldon on 2006-12-15
Thanks for the replies!  I Appreciate it a lot!

I didn't realize that GRUB had these options.

sheldon

---

