---
title: "Anything Linux Running Very Slow"
date: 2013-04-27
forum: General Help
---

### Post by ispofdoom on 2013-04-27
Hi!

I've been having some issues with Linux since installing Windows 8 as my primary OS.

Until recently I used X-Launch and Putty to remote into a file server on Xubuntu at home (the computer was running Windows 7 at the time).  This setup worked perfectly.

Since shifting to Windows 8 Putty and X-Launch started working vvvvvvvvvvverrrrry slowly.  ie:  it would take about 5 minutes to load an xfce session.
I've also tried installing Ubuntu 13.04 and Xubuntu 13.04 as a dual boot OS.  But these are also very slow.  It took 2-3 hours to install Xubuntu, and start up takes around an hour into Xubuntu.  (Windows 8 still works fine).  Once into the desktop environment there is a ~30 second delay when right clicking the desktop (for example).  Booting a live USB also takes a long time.  I'm at a bit of a loss as to why this is going on.

I'm quite new to Linux, and don't really know what config files or logs to post, but feel free to request any that may be of assistance.

System specs are:
Asus P8Z68-V mobo
Intel i5 2500K
2x 4GB DDR3 Ram
Geforce GTX 460 1GB
2x 1TB Hdd

Thanks!

---

### Post by papibe on 2013-04-27
Hi ispofdoom. Welcome to the forum ):P

That is very unusual. You have a powerful machine so both Ubuntu and Xubuntu should run fast.

Do you see anything using too much CPU or RAM when you run 'top' in a terminal?

Did you install the Nvidia proprietary driver?

Regards.

---

### Post by CatKiller on 2013-04-27
It's unclear from your post whether it's a problem with your Windows 8 setup remoting in, or whether you still have problems running locally. Can you clarify exactly what the setup is?

---

### Post by ispofdoom on 2013-04-27
Hi, thanks for the replies. 
I've booted back into xubuntu (30min startup), so am posting from an iPod touch.  
The top command within terminal shows ~1% CPU usage and slightly less memory usage.  The commands using resources seem to be xorg, and xfce primarily. 

To confirm my current install:  I use windows 8 mostly, and have xubuntu 13.04 installed as a dual boot os.  I've tried a few other setups mentioned in the original post, currently I'm going with xubuntu. 

I've also looked into issue arising from uefi, but I don't think there would be anything of this nature... However I'm really not sure.

Edit:  ok, updated nvidia drivers and established that the install is a legacy install, not uefi...
(See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI))
Will reinstall as uefi, as that could be an issue...?

edit 2:  never mind, windows 8 is running in legacy mode, so no need for uefi xubuntu install.....

---

### Post by CatKiller on 2013-04-28
As papibe says, this is very peculiar. If it's not CPU or RAM overloading then some other things that might cause slowdowns of the magnitude that you're seeing are incorrect bus speeds so that everything's significantly underclocked, massive I/O or equivalently faulty hard drive. I'm struggling to think of a scenario where these things might happen and Windows works fine, though.

Have you got an older Ubuntu image you could boot from to see if it's some kind of regression? My computer's got similar specs to yours and I haven't seen anything like it, though.

---

