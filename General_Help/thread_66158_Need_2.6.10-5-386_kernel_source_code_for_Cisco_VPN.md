---
title: "Need 2.6.10-5-386 kernel source code for Cisco VPN client v4.0.1 install"
date: 2005-09-16
forum: General Help
---

### Post by confused_user on 2005-09-16
Hi, this is my first post here so please dont shout at me ;-)

I have done a few searches here and it doesnt seem to have been asked before so here we go...

I have ubuntu 5.04 running on the 2.6.10-5-386 kerenel.

I am trying to installed the linux version of Cisco's vpn client, when i run the install script the first question it asks me is "whats the path to your kernel source?" or words to that effect.

I dont seem to have the kernel source anywhere on my machine?

Presumably i should be able to download it somwhere?

I would greatly appreciate it if somone could link me to the source and perhaps sugest a good path to store it on my machine.

Many thanks
confused_user

---

### Post by Treggats on 2005-09-16
[kernel source](http://www.kernel.org/pub/linux/kernel/v2.6/)

Here you go :) there is a list of sources.. you will need the 2.6.10-5-386 one.. its a .tar.gz file 
I'm sure you can find it :grin: it's not that hard ;-)

---

### Post by confused_user on 2005-09-16
Thanks dude, i found the source for 2.6.10 on there, but i though i needed the specific 2.6.10-5-386 which i couldnt find?

i'll try this one and see if it works.

cheers!

---

### Post by confused_user on 2005-09-16
well...i tried the 2.6.10 but it still doesnt work, if i could just find the exact kernel that i'm using.....

this is the one time i wished that i didnt go for "linux for humans", with suse and red hat the kernel source is allways on the cd!

---

### Post by varunus on 2005-09-16
Just install linux-headers-2.6.10-5-386 from synaptic (System->administration->synapitc package manager). This will install the kernel source.

Make sure to get "build-essential" too if you're adding kernel modules.

---

### Post by confused_user on 2005-09-16
you beauty, thats done it, thanks very much guys and good work.

now if i could just get the VPN working..... :razz:

---

