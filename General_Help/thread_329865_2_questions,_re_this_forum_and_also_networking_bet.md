---
title: "2 questions, re: this forum and also networking between ubuntu machines"
date: 2007-01-02
forum: General Help
---

### Post by Choad on 2007-01-02
i have a new laptop! wohoo! it is awesome. however this forum wont let me log on with it. probably because im logged in with this one? oh well

main question:

i want to transfer all my files accross. i have a router for wireless/lan but only 1 lan cable, so it wold be ideal to simply connect the 2 laptops together with a lan cable.

how would i go about setting up the network so i can grab all the files. also it would be good to have a very fast connection. wired connections should theoretically go very fast shouldnt they? i will be transfering ~60 gigs

thanks for any help.

oh the new laptop is running a fresh ubuntu edgy install, the old laptop is running a relatively well used xubuntu edgy install... not sure if this matters :)

---

### Post by MrHorus on 2007-01-02
> **Choad said:**
> 
i want to transfer all my files accross. i have a router for wireless/lan but only 1 lan cable, so it wold be ideal to simply connect the 2 laptops together with a lan cable.


Yes, but you will need to make sure it is a crossover cable - with one of these the transmit and recieve pins are reversed on one end so you can connect two machines together directly.

Once done, samba or ftp should suffice for what you want to do.

As for performance, you will not get full speed as these are theoretical; actual performance will depend on the actual hardware in the machines.

---

### Post by meng on 2007-01-02
If transferring 60 GB as a one-off, definitely go for the wired connection. As for the problems logging on, check that you have cookies enabled.

---

### Post by Choad on 2007-01-02
ok cool ill have to find a crossover cable

or... would it be good to use 2 normal cables plugged in to the router? its more likely ill be able to find a second normal cable.

also, just looked at the system monitor, and before it showed 2 cpu's (core 2 duo) but now it only shows 1. i have downloaded several new kernels i think during my setting up of the system.... could it be that that has gotten rid of 1 of the cores?

---

### Post by koenn on 2007-01-03
> **Choad said:**
> would it be good to use 2 normal cables plugged in to the router? its more likely ill be able to find a second normal cable.
that should work too

> **Choad said:**
> 
also, just looked at the system monitor, and before it showed 2 cpu's (core 2 duo) but now it only shows 1. i have downloaded several new kernels i think during my setting up of the system.... could it be that that has gotten rid of 1 of the cores?
i suppose it's possible you've installed a kernel that does not work with dual core processors well and thus only 'sees' 1 of the cores.

---

### Post by Choad on 2007-01-03
yep i figured that out :) its the nvidia driver. it depends on a 386 kernel for some reason, all i had to do was use the "old" generic 686 kernel with SMP

i hope it doesnt adversely affect my graphics card performance

---

### Post by Choad on 2007-01-03
ok it does very much adversely affect graphics. namely x wont start

any idea on how to fix this?

---

### Post by koenn on 2007-01-03
you can always try to run ```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure x and see if it gets any better.

I'd first try to find out why it doesn't start. You could run 'startx' or 'xinit'  (probably  with sudo ?) and look at the output / error msgs

---

### Post by Choad on 2007-01-03
i skimmed the error message when x first crashed, and it was talking about kernel related things missing. i get the feeling that no of xorg fiddling will fix it, short of not actually using the nvidia driver

---

