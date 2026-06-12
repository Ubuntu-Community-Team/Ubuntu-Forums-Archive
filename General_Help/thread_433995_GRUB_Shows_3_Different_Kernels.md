---
title: "GRUB Shows 3 Different Kernels"
date: 2007-05-05
forum: General Help
---

### Post by Falkon on 2007-05-05
**RESOLVED  :)

When I turn my comp on and GRUB loads (I have a dual boot Feisty and XP), I get 3 different options to boot within the first category, and the only difference in the names is the kernel.  I can choose 2.6.10, 2.6.17, and 2.6.2something.  The numbers might not be completely accurate, but you get the basic idea.

Also, the first option was from my initial install of Edgy, the second came with an update, and the last one came with Feisty.  However, no matter which one I choose, it starts Feisty.  As far as I can tell, they all boot the latest kernel and version of Ubuntu.

I assume this is a problem with Grub, as I don't have multiple versions of Ubuntu actually installed, but I wasn't able to get GrubEd running.

So, how can I make the latest version overwrite the last two, or otherwise eliminate these vestigial options?

---

### Post by jfinkels on 2007-05-05
> **Falkon said:**
> When I turn my comp on and GRUB loads (I have a dual boot Feisty and XP), I get 3 different options to boot within the first category, and the only difference in the names is the kernel.  I can choose 2.6.10, 2.6.17, and 2.6.2something.  The numbers might not be completely accurate, but you get the basic idea.

Also, the first option was from my initial install of Edgy, the second came with an update, and the last one came with Feisty.  However, no matter which one I choose, it starts Feisty.  As far as I can tell, they all boot the latest kernel and version of Ubuntu.

I assume this is a problem with Grub, as I don't have multiple versions of Ubuntu actually installed, but I wasn't able to get GrubEd running.

So, how can I make the latest version overwrite the last two, or otherwise eliminate these vestigial options?

I guess you can just comment out their entries in your /boot/grub/menu.lst. Before you edit this file, though, make a backup copy! ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
Go down to the bottom where there is a list of kernels that looks like this
```

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=4021e53c-90f6-4f23-9d9d-1f1dbb5e0c70 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=4021e53c-90f6-4f23-9d9d-1f1dbb5e0c70 ro single
initrd          /boot/initrd.img-2.6.17-11-generic

```

Add a "#" at the beginning of each line for the sections that you don't want to see in your Grub list., like this:```

#title           Ubuntu, kernel 2.6.17-11-generic
#root            (hd0,0)
#kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=4021e53c-90f6-4f23-9d9d-1f1dbb5e0c70 ro quiet #splash
#initrd          /boot/initrd.img-2.6.17-11-generic
#quiet
#savedefault

#title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
#root            (hd0,0)
#kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=4021e53c-90f6-4f23-9d9d-1f1dbb5e0c70 ro single
#initrd          /boot/initrd.img-2.6.17-11-generic


```

I think this will work, HOWEVER I know very little about grub and I am not by a long shot certain about this :D

---

### Post by Thingymebob on 2007-05-05
Removed - Jfinkels got their first (yes this will Work)

---

### Post by rsambuca on 2007-05-05
There a few different methods you can use to get rid of the entries from the grub menu.  The method posted by jfinkels will work fine.  You can also just delete the entries entirely from your grub menu.lst file if you wish.  Keep in mind that the next time there is a kernel update (there actually isn't that many), grub will be updated and these entries will reappear, at which point you will have to either delete or comment them out again.

Another method is to change the line that says "howmany   all"  to "howmany 1", which will make grub only show the newest kernel in your list.

Another method is to actually remove the old kernels from your system.  If you are sure that the newest kernel is bug-free, then open up the Synaptic package Manager and search for linux-image.  You will see all of the kernels listed there.  Just remove the old ones you no longer need and then grub will automatically be updated.  If you use this method, I would recommend leaving the current kernel and the most recent one as well, just in case.

If you need any more help, let us know.  good luck.

---

### Post by iamajd on 2007-05-05
Find this section in your menu.lst:```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
```Change the "# howmany=all" to "# howmany=1" so that grub will only show the newest kernel (plus the single user and the memtest options).  The older kernels will still be installed on your system, so (after you are *POSITIVE* your new kernel is working) remove the older kernels in Synaptic.

EDIT:  Haha, rsambuca submitted his while I was writing this!  Good job team!

---

### Post by Falkon on 2007-05-05
Great success!

Unfortunately the howmany edit didn't work, but I commented out the extra options and now it works perfectly.

Thanks to everyone who posted! :D

---

