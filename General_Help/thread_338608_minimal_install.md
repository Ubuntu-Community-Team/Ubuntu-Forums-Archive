---
title: "minimal install"
date: 2007-01-14
forum: General Help
---

### Post by heathen on 2007-01-14
Is there any way to install ubuntu with only the basic/needed programs...  i.e just firefox and the basic gnome desktop/utilites? (network manager, nautilus)

---

### Post by mykalreborn on 2007-01-14
if you want a minimal install why don't you use [debian]("http://www.debian.org")? it's pretty straight forward, stable and it works just like ubuntu.
well... ubuntu works just like debain hehe :p

---

### Post by heathen on 2007-01-14
tried debian... never could get it working,  I could never get it to do anything past the command line... and honestly, their forums weren't too keen on helping me.

---

### Post by mykalreborn on 2007-01-14
> tried debian... never could get it working, I could never get it to do anything past the command line... and honestly, their forums weren't too keen on helping me.
hmmm :-k
i don't think ubuntu has a minimal install version. but why do you want a minimal install anyway?

---

### Post by blackmh on 2007-01-14
There is guide somewhere on the forums for how to install ubuntu server and then add what you need.

---

### Post by heathen on 2007-01-14
I just dont need all these programs, i need firefox and the wireless utilities...  anything else i can add as i go.  Besides, I thought that building my own system up would be a nice challenge.  And it would let me learn a little more about how stuff works...

edit to add, I've been searching the forums for similar posts.. Found nothing promising..   

oh, and sorry I put this in the wrong forum... I've gone braindead reading all the stuff that's on this board

---

### Post by mykalreborn on 2007-01-14
> I just dont need all these programs, i need firefox and the wireless utilities... anything else i can add as i go. Besides, I thought that building my own system up would be a nice challenge.
well, ubuntu doesn't ahve all that much software anyway, like other distros do.
and i don't want to be a critic, but since you can't even install debian - which is not so hard - how do you think you're going to build all those programs?
*don't take it as an offense please ;)

---

### Post by heathen on 2007-01-14
debian out of the box doesnt support the craptastic laptop graphics card that I have... Since this computer is mainly for playing my music files when I'm at work and doesnt have an internet connection... hell, it doesnt even have a network card.. just a modem that will never get used...  It's kind of difficult to fix..

I find that ubuntu is fairly easy and thru the help on these forum I've managed to learn a few things... like how to compile/install programs that dont always exist in the repos...

I tried installing Xubuntu and for some reason it didnt take to my laptop... it would start load grub then do nothing...  tried 4 diffrent xubuntu cds one of which came from ship-it.  same result every time...  so i put gnome on it... but it takes about 10 minutes to load, and when I start programs i might as well go drink a pot of coffee then come back...

---

### Post by meng on 2007-01-14
One of the weaknesses of Ubuntu is that there is no good minimal install option along the lines of what you are looking for. (I think Ubuntu's great, and very few users seem to need such an option, so I'm not saying it's a critical flaw by any means.)  You could look at SLAX or PCLinuxOS, which come with multiple versions (including minimal installs), although notebook/laptop support may not be great ... what sort of graphics card is this?

As for the slow performance your computer is having, this is partly related to running a live distro. But I wouldn't recommend running GNOME with less than 192 MB RAM. If your RAM amount is borderline, you would be better off installing from the Alternate CD (text installer) rather than the Live Desktop CD (graphical environment and installer).

---

### Post by nix4me on 2007-01-14
Just install normal ubuntu and then fire up synaptic and remove the things you dont want.

Or install gentoo.  But I doubt you would have any luck, much harder to install.

nix4me

---

### Post by meng on 2007-01-14
I think it's easier to build a custom install from bottom up than top down. There are plenty of options between Gentoo and Ubuntu.

---

### Post by heathen on 2007-01-14
I've tried gentoo, but i lack the knowledge at this point..

I tried synaptic, but I aparently removed something i needed...  that's why i was asking about a minimal install...  i need to reinstall the system

---

### Post by meng on 2007-01-14
One idea:
Use PCLinuxOS 0.93 Minime edition: it will install KDE with very little else. On top of that, install Firefox if Konqueror doesn't suit your browsing needs, and a media player of your choice. (Synaptic is included for package management.)
A variation on this concept is to install PCLinuxOS Junior, which has a range of extra applications included, but not as many as Ubuntu does.

---

### Post by rabid9797 on 2007-01-14
a couple options your could try:

1. use xubuntu, its more of a minimal install(used for thin-clients and such) than regular ubuntu is. you could just uninstall what you don't want. this gives you the best choice for a full system with minimal space use.

2. vmware ubuntu(or find a custom internet focused build), they usually fit onto a cd and you can install just the bare minimum.

---

### Post by kerry_s on 2007-01-14
I also think you should try PCLinuxOS minime, it's a bare bones KDE that has excellent wireless support. It gives you just enough to start with and build on. Plus it's live cd so you can try it first. Otherwise just go for a server install build up, do a search for instructions.
-> [http://ftp.belnet.be/linux/pclinuxos/live-cd/english/preview/pclinuxos-p93a-minime.iso](http://ftp.belnet.be/linux/pclinuxos/live-cd/english/preview/pclinuxos-p93a-minime.iso)

---

### Post by heathen on 2007-01-14
got it thanks to [this]("http://www.ubuntuforums.org/showthread.php?t=293996&highlight=minimal+install") thread

---

### Post by heathen on 2007-01-14
and it's using 136mg of 256mg of ram...  hopefully when i install fluxbox it will be less..

---

### Post by kerry_s on 2007-01-15
> **heathen said:**
> and it's using 136mg of 256mg of ram...  hopefully when i install fluxbox it will be less..

Unused ram is wasted ram in linux. Your computer will work better & faster with the stuff loaded in ram.

---

### Post by heathen on 2007-01-15
> **kerry_s said:**
> Unused ram is wasted ram in linux. Your computer will work better & faster with the stuff loaded in ram.

meh, when it comes to starting the system, the less crap it loads in the first place the happier I am...  


oddly enough, I got bored and decided to do this on my main computer... conky reported that my processor was running at 800MHz, now it's at 1729MHz.   Any idea what was causing my processor to be slowed?

---

### Post by raul_ on 2007-01-15
[http://www.ubuntuforums.org/showthread.php?t=206022&highlight=arch]("http://www.ubuntuforums.org/showthread.php?t=206022&highlight=arch")

---

### Post by halw on 2007-01-15
Check out the following link. It may be what you're looking form

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by kerry_s on 2007-01-16
> **heathen said:**
> meh, when it comes to starting the system, the less crap it loads in the first place the happier I am...  


oddly enough, I got bored and decided to do this on my main computer... conky reported that my processor was running at 800MHz, now it's at 1729MHz.   Any idea what was causing my processor to be slowed?

What kind of processor is it? it sounds like it's speed stepping to me, in other words it slows down when not that much processor power is needed, then cranks up to full when needed. Maybe change your conky line so you can see the difference, here's what i use->

```
CPU:${freq}mhz / Clocked:${freq_dyn}mhz / Temp:${acpitemp}C 
```

---

### Post by heathen on 2007-01-16
ok, before I installed ubuntu this way on the main computer the output of {freq} showed 800mhz,  now it shows 1729...   I was just wondering what might have been keeping at 800

thanks for the new conky line though... I like it better than what i had

---

