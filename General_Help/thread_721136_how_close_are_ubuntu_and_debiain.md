---
title: "how close are ubuntu and debiain?"
date: 2008-03-11
forum: General Help
---

### Post by mindheavy on 2008-03-11
In effort to learn more about linux, and how it operates, i was wondering the other day how closely ubuntu and debian are related, and would studying debian provide much insight to the way ubuntu handles business?

---

### Post by kesman on 2008-03-11
If you have experience with Debian, then Ubuntu is much easier to get familiar with I'd say.
Most configuration files are the same, package handling is the same, applications are the same. Much more is automated in Ubuntu.

---

### Post by kerry_s on 2008-03-11
there are minor differences such as the boot mechanism, ubuntu uses a new event driven boot(/etc/event.d), debian still uses the very simple init type boot(/etc/inittab). there's also diferences in the kernel used in both.

other than the programs used in the base, everything like the folders and files are pretty much in the same place on most any debian based system. i used ubuntu for a long time, but have gone back to debian for it's simpleness, simple for me anyway.

learning debian is great, but the differences are so minor that it does not have to be debian, using any debian based distro you would learn the same thing. using what you like is your best bet.

my machines old 450mhz 256mb ram and i've learned through trial and error that debian is fantastic on the old stuff, newer debian based builds tend to make things work for the new stuff by dropping the old stuff. that's why some distro's like ubuntu have better hardware support for newer systems, than say a stock debian system.

i prefer using a custom install, i install the debian base and add on from there to fit my needs. every time i install i try something different and learn each time.

this build, i used jfs and deadline, i simplified my auto boot, i also decided to go with fixed fonts where ever i can. other than that my programs are always the same.

rambling :)
anyways if you really want to get a feel, start with the base and work your way up, you'll be amazed at how very simple it is to have things your way, then you can really see the difference in what it actually takes to make up a complete distro.

grab the debian net installer->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

to get a base install, when it comes to the package selection uncheck both/all of them

that will give you only the base, that means no gui, you'll be at command.

log in as root, to start getting your X stuff
apt-get install xorg (a wm) (what ever else)

yeap, its that simple. here's a example for fluxbox
apt-get install xorg synaptic fluxbox rox-filer leafpad iceweasel
type> exit
than log in as your user and
type> startx

that's it you have the beginning of a system, you can now use synaptic to get what ever else you want.
fluxbox = window manager
rox-filer = file manager
leafpad = text editor
iceweasel = firefox web browser, redone to be free
synaptic = add and remove programs

here's a couple of pic's of mine, i use jwm for my window manager.

---

### Post by mindheavy on 2008-03-11
excellent information guys, thanks.
i've got a desktop that would be perfect to get a base system on. always liked the idea of kinda building a linux system from the ground up.

---

### Post by bodhi.zazen on 2008-03-11
If you like there is also a minimal Ubuntu install cD:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I agree, there are minor differences between Ubuntu and Debian and the developers of the two projects collaborate (ie share code / improvements) for the betterment of both distros.

---

