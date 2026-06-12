---
title: "ubuntu fails to load after updates"
date: 2007-10-16
forum: General Help
---

### Post by minesapint on 2007-10-16
Dear All,

Any help would be appreciated :)

I have just installed Ubuntu 7.04 (linux-headers-2.6.20-15-generic) and due to an problem with the realtek network card on my philips x56 laptop I had to use the alternative cd install and during the installtion, I had to delete the 8139too.ko file before it was loaded.

The laptop now runs fine, but now that I have run the updates, the linux-headers-2.6.20-16-generic has been installed and the laptop now hangs on boot up when it detects the network card.  (the original version does still boot fine)

The solution to my problem is to edit the .config file for the 2.6.20-16-generic install, but I cant find any instructions on how to do this, I dont want to compile a custom kernel, I just want to add a couple of options to the current kernel.

Could someone please point me in the right direction, thanks in advance for any help.

---

### Post by minesapint on 2007-10-19
Ok, I guess I havent explained what it is I want to do.

So ubuntu is installed and running the linux-headers-2.6.20-15-generic and all works well, when I run the updates linux-headers-2.6.20-16-generic is installed and this hangs on start up.

So what I need to do is edit the .config file for the linux-headers-2.6.20-16-generic files and change a couple of settings to do with the realtek 8139too.

If I edit the .config file do I have to recompile the kernel for the changes to be made?

Do I need to download the source files for the 2.6.20-16-generic kernel in order to recompile?

Once the kernel has been recompiled will any future kernel updates need to be reconfigured or will they keep the new settings?

Sorry for all the questions, but now I know that ubuntu can run on this laptop, I would like to get the updates working as well.

---

