---
title: "Gutsy won't start udev, Xorg"
date: 2007-10-19
forum: General Help
---

### Post by beniwtv on 2007-10-19
Hello,

I really need some help here :(

Today I installed Gutsy from the alternate CD, as the live CD for some odd reason just hangs while starting Xorg (the computer hard-freezes).

So, the installation went fine, after reboot, as expected (and the same as feisty), Gutsy hangs on starting Xorg.

When booting in single (rescue) mode, the system just hangs starting udev, in /etc/init.d/udev, with the line "Loading hardware drivers". Again, the system hard-freezes.

Now I tried again to boot a normal boot, and it hangs as well! Taking quiet and splash out of the start options, it hangs at the same message as above.

So I tried booting with these options: rw init=/bin/bash. It boots fine. After this I was able to edit Xorg.conf to get X to start, connect to the Internet. 

Also if I execute /etc/init.d/udev start it works. 

To see that the problem is there, I executed /etc/init.d/udev stop and then /etc/init.d/udev start, and it hung again.

My specs can be found here: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00793386&lc=en&cc=us&dlc=en&product=3308767&rule=29967&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00793386&lc=en&cc=us&dlc=en&product=3308767&rule=29967&lang=en)

It's running the amd64 version...

I tried everything I know of, but can't seem to find a solution. Any clue how to debug this?

Thanks in advance.

---

### Post by Fenix-TX on 2007-10-22
I have the same problem with kernel 2.6.22-14 that is on gutsy, but i can boot from feisty kernel (2.6.20-16). I had upgrade from feisty last saturday, and i can't solve this problem, the only thing that i can do, it's booting from feisty kernel.

---

