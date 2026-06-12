---
title: "Fast Ubuntu on old pc?"
date: 2006-11-25
forum: General Help
---

### Post by cub on 2006-11-25
My regular pc died last week so I had to revert to my old trustworthy PentiumII 450 Mhz. It has 384 MB RAM so it runs quite alright. The thing is that the processor runs on 100% every time I do anything.

Do you have any tips on what to do (of there is something) to make it less processor intensive? Other window manager than Gnome perhaps? Or should I even look for another linux distribution and what would that be?

I would need to be able to run Firefox, mail, OpenOffice and Audacity.

---

### Post by Spin Doctor on 2006-11-25
Try the Xubuntu disto. A derative of Ubuntu. It will be less processor intensive. When it comes to open office. It is a very "heavy" program, so you should look into a leightweight word processor such as Abiword for a pleasant working environment. Abiword is included in the Xubuntu distro.

Look at the following links:

[http://www.xubuntu.org/](http://www.xubuntu.org/)
[https://help.ubuntu.com/community/InstallingXubuntu](https://help.ubuntu.com/community/InstallingXubuntu)
[https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)
[http://www.abisource.com/](http://www.abisource.com/)

---

### Post by yopnono on 2006-11-25
If you using Dapper add this.
Add this to the grub kernel option elevator=cfq

[https://wiki.ubuntu.com/CFQbyDefault](https://wiki.ubuntu.com/CFQbyDefault)

---

### Post by Rui Pais on 2006-11-25
in very old computers (a pentiumII is a good candidate for very old ;)) even Xubuntu can be slow and a resources eater. 

Without reinstall you can try already lighter window managers, specially those who are only that and not desktop environments. 
Some of the easier and very configurable are fluxbox (highly recommended), others *box like openbox, windowmaker very powerful and very light, enlightenment light and even had eyecandy... use synaptic/apt to check what is available and simpler to install then reinstall a full OS.

There are light browsers. Opera on my old machines runs much nicer then firefox, that sometimes even froze the all computer.

On old machines is even more important to turn off unneeded services. They slow start up times and waste memory. Ubuntu is terrible when came with default services... [check here some tips on that subject]("http://ubuntuforums.org/showthread.php?t=89491").

If you can avoid graphical file managers, check rox, xfe, pcmanFM or thunar, they are much lighter and faster then nautilus.

---

### Post by grizzly on 2006-11-25
Exactly why is ubuntu soooo slow? 
I have disabled plenty of services, run kde minus kdesktop/kicker/konq_preload/korganizer . fvwm  is the window manager, I have tried multiple installs using ext3/xfs , but still Ubuntu runs slowwwwwww
Xp on the otherhand literally flies! Puppy is another OS that flies, but then it runs from the ram.
Is it ubuntu or linux itelf which is slow? If ubuntu then what exactly is the problem?? Anything I can do to diagnose the problem.

---

### Post by syadnom on 2006-11-25
i have found that ubuntu is exceptionally slow on old hardware.  i have a p2 450 that just wont run ubuntu at a reasonable pace though win2k runs great on it.  i have instead installed gentoo and use distcc to compile programs remotely and gentoo screams on this little beast.

i also tried slax installed to the hard disk and it was quite fast in kde but package management on slax is just not for a hd install. enter gentoo.

---

### Post by Rui Pais on 2006-11-26
> **syadnom said:**
> i have found that ubuntu is exceptionally slow on old hardware.  i have a p2 450 that just wont run ubuntu at a reasonable pace though win2k runs great on it.  i have instead installed gentoo and use distcc to compile programs remotely and gentoo screams on this little beast.

i also tried slax installed to the hard disk and it was quite fast in kde but package management on slax is just not for a hd install. enter gentoo.

Gentoo on an old computer?... will leave you spending the rest of your days wait for compiling to finish :lol: or you need to use distcc. 
I once installed on a pentiumMMX 200Mhz the base system from stage1, just for fun. It take 3 days and nights. And when i tried to emerge X it hang it and never managed to finish... 

Ubuntu direct from the box work bad on old computers because is Gnome based (besides have a lot of services turned on by default), that heavy and not at least oriented for that kind of hardware. When people compare such things are using the term Linux to mean to much things. Linux kernel+base system is fast and faster then any Windows. 

But as long as you go for an Xserver things start to slow a lot. The X server on Linux it's heavier the what ever equivalent of Windows (thats one of the reasons games are bad on tux). The X server is a small masterpeace of technology build to be flexible and offers a lot of options to work either on a box as across boxs on a network, it was not build with old hardware and save on resources. Same goes to Desktop environments instead of simple windows managers.

Another thing is compare recent software (thats is being develop for user friendliness and some times for eyecandy, not for old machine specifically) with old software/OS like W2k (6~7 years old). Try to compare with an x server and a gnome or a kde of those days and things will run smoother . There is a slax distro oriented with that porpose, with an old version of XFree86 with the minimum security updates and a tweeked IceWM... don't remember the name. Or DSL, or Puppy (Beatrix if i remember well is old hardware oriented too...)

As an example, what i done with my old hardware was, install an old distro (in my case, strangely what worked better was an old RedHat9) that i use with WindowMaker, The faster i manager to work there. I use only to save data and music across my network, cause it's the machine that have a CDwriter. Apart from that i configured a 2nd X server (the default one) to run not on that machine but on my P4 using XDMCP protocol, and voilá, my old box is now a modern and faster computer, only slightly limited by the network speed, thanks to flexibility of X and Linux good multi-thread. :)

---

### Post by syadnom on 2006-11-26
i dissagree with the above post in that the X server is not nearly as heavy and the windows interface and newer versions are actually more efficient than older versions.

the arguemnet is made than you should use an older distro to get an older version of X but in fact the older xfree86 versions are slower than the newer xorg 6.9+ versions

i run xorg7 on gentoo on my p2 450 and i flies.  gnome is reasonably responsive as well though i have found KDE to be faster.   XFCE is nice but if im looking to replace the functionality of windows2k on this little machine i need to go with KDE.

to conclude, something in ubuntu's configs are making it very much slower than other modern distros on older hardware.  i have tried fedora core4 on this machine and it is very usable while ubuntu with anything(xfce,kde,gnome) is slow.

---

### Post by Rui Pais on 2006-11-26
> **syadnom said:**
> ...
the arguemnet is made than you should use an older distro to get an older version of X but in fact the older xfree86 versions are slower than the newer xorg 6.9+ versions
...

Nope, my argument was that you ***may*** use an old distro to get older (less complex and developed in the days that the old hardware was on use) versions of ***all*** the software to use on such ancient machines. 

But you may have a point about latest versions of xorg. The modularized version is  supposed to be lighter and eventually less hungry on resources. I didn't try that.

---

### Post by syadnom on 2006-11-26
fair enough. i maintain that X lighter and faster now than it was before but many applications will be heavier most definitely.  the only problem is that some apps such as browsers are heavier but must be used in many situations so it is unavoidable.

---

### Post by cub on 2006-11-28
Just a quick update from the thread starter: I have played around with a couple of different window managers which did wonders to my old Pentium. I'm settling for fluxbox....but I'm curious about installing Xubuntu as well so I might try it out some time soon.

---

### Post by kerry_s on 2006-11-28
> **cub said:**
> Just a quick update from the thread starter: I have played around with a couple of different window managers which did wonders to my old Pentium. I'm settling for fluxbox....but I'm curious about installing Xubuntu as well so I might try it out some time soon.

Just try as many setups as you can, to get your self familiar with the way they work. Eventually you'll figure out exactly what you like, then the real adventure begins, you can actually use the command-line install & build your system to your needs. So for now have fun & learn, than when your ready, check out the low ram install how to.-> [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by feest on 2006-11-28
well, i've got a pentium III 500mhz 310mb ram computer as server and it runs on ubuntu breezy badger. it's not the fastest but it runs good enough to work.

---

### Post by K.Mandla on 2006-11-28
There's plenty of speed in Ubuntu, if you try a different window manager and take a little time to tweak it for older hardware. The lower level for practicality in my book falls around 200Mhz; for what I've seen, below that there isn't much you can do to speed things up. But for anything above 200Mhz you can build an ultralight desktop that will do everything WinXX will do, and faster, and better looking. ;)

---

### Post by Linuturk on 2006-11-30
[www.fluxbuntu.org](www.fluxbuntu.org) << give that a try . . .

---

