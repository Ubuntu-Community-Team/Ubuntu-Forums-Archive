---
title: "Just installed ubuntu edgy, so many problems"
date: 2007-03-19
forum: General Help
---

### Post by tomus on 2007-03-19
I'm a newbie at ubuntu.  I installed it yesterday. Anyway, I have just been playing around with it and sorted a couple of things out but I went on the update manager and added the available updates and now things have gone a bit weird. On GRUB I now have two more ubuntu choices, is it possible to delete them as they do not work. Also whenever I minimize a window it does not go onto the taskbar at the bottom, it seems to go into the show desktop icon in the bottom left corner and I dont know how to retrieve it again. Finally, the icons on the top right of the screen have moved around in a confusing manner and the bottom right spaces menu now only has one option.

Any help would be appreciated

thanks

---

### Post by praxis22 on 2007-03-19
As a general rule, you should only ever need the top line in the list GRUB gives you.

These are all revisions of the kernel. The heart of the OS. Basically:

Linux = Kernel
OS/Distro = Kernel + system utilities and programs.

You can remove things from the list by editing /boot/menu.lst (I think, it's inside /boot somewhere anyway :) But if you don't know what you're doing, better not play with it.

Which desktop are you using? Gnome? KDE? XFCE?

---

### Post by tomus on 2007-03-19
I'm using gnome

---

### Post by llamakc on 2007-03-19
Please don't edit /boot/grub/menu.lst and remove those entries. You may very well need them if things break. They are not hurting anything.

One can edit how many kernels are shown in their /boot/grub/menu.lst file at this point:

```

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

```


You would edit the last line from "all" to the number you want. After doing so, run `sudo update-grub`

What happens if you cycle through windows with ALT-TAB? You should get your missing windows back that way. Did you remove your "window list" from the panel? It may be added back if you did.

---

### Post by buuntuu! on 2007-03-19
you can just comment out (put # before the line of) the older kernels (the ones with the lower number. this will not remove them, they will just disappear from the boot menu. it is wise to keep an older kernel for if you happen to have the problems you encountered you can just boot back into the older kernel... you said the other entries do not work, could you specify which ones?

anyhow, to do this you ```
sudo nano /boot/grub/menu.lst
```
which opens nano (you could replace it with "gedit" if you feel more comfortable there)
where oyu can then edit your bootmenu. be careful though!
have fun

---

### Post by tomus on 2007-03-19
> **buuntuu! said:**
> you can just comment out (put # before the line of) the older kernels (the ones with the lower number. this will not remove them, they will just disappear from the boot menu. it is wise to keep an older kernel for if you happen to have the problems you encountered you can just boot back into the older kernel... you said the other entries do not work, could you specify which ones?

anyhow, to do this you ```
sudo nano /boot/grub/menu.lst
```
which opens nano (you could replace it with "gedit" if you feel more comfortable there)
where oyu can then edit your bootmenu. be careful though!
have fun

The two newest kernals do not work. Of which the second is the safe recovery mode of the first.

---

### Post by buuntuu! on 2007-03-19
what's the error message when you try to boot the new kernel?
hope i can help there, as i never had such a problem, i'm a bit green here too... have you searched the forum for similar problems?

---

### Post by DougieFresh4U on 2007-03-19
> **tomus said:**
> I'm a newbie at ubuntu.  I installed it yesterday. Anyway, I have just been playing around with it and sorted a couple of things out but I went on the update manager and added the available updates and now things have gone a bit weird. On GRUB I now have two more ubuntu choices, is it possible to delete them as they do not work. Also whenever I minimize a window it does not go onto the taskbar at the bottom, it seems to go into the show desktop icon in the bottom left corner and I dont know how to retrieve it again. Finally, the icons on the top right of the screen have moved around in a confusing manner and the bottom right spaces menu now only has one option.

Any help would be appreciated

thanks

Not sure if I can help here but a suggestion I can offer, open up Synaptic Package Manager and scroll down to -linux-headers & linux- image and see what kernels are installed. Also, I believe it's best when I do updates from the terminal **sudo apt-get update**  then **sudo apt-get dist-upgrade**  Once you have done that run the following from terminal to make sure all has been installed and configured **sudo apt-get -f install** then **sudo dpkg --configure -a** My reason for wanting to use terminal for updates is that some times updates will want to remove thing that should not be removed and using terminal you have better control over whats being installed and/or removed

---

