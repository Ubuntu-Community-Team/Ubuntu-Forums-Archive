---
title: "GParted freezes when trying to use it... :'("
date: 2008-03-19
forum: General Help
---

### Post by Dojan5 on 2008-03-19
I am trying to install Ubuntu.
I finally got Windoze installed, after reformatting device.

Anyways, now when i am trying to use Ubuntu Live CD, i wouldnt want it to install OVER windows which i had so much hassle with to get it working.
So now i would want to make an EXT3 Partition and a Linux Swap.
But since you cant shrink a partition in the installing program i have to partition it using GParted first (Still on Ubuntu Live CD)...

When i open GParted, it loads, i hear the A: sound a bit (It normally does) and then, after a few more seconds loading, it just freezes. Just like that!
So currently i have the OS i HATE installed (But i need it) and i want Ubuntu installed again, i really miss it T-T
Anyone?

---

### Post by spo0neybard on 2008-03-19
Do you have information that is possible to back up onto a cd or something?
Because from then it'd be really easy to install both. If not I'm clueless.
Something about defragging and resizing. No idea how to do the first. Best luck.

---

### Post by Dojan5 on 2008-03-23
> **spo0neybard said:**
> Do you have information that is possible to back up onto a cd or something?
Because from then it'd be really easy to install both. If not I'm clueless.
Something about defragging and resizing. No idea how to do the first. Best luck.

Well, no.
My cd burner is broken, so thatd mean that i transfer data from my computer to my mothers....
And, as far as i know GParted "moves all data to the beggining of the block" or something like that. I think it is a cryptic way of saying, defragmenting. But i don't know.
I haven't had any data losses before when using GParted though.

---

### Post by spo0neybard on 2008-03-23
Sorry I haven't been on for a while. Anyway if you have a means of transferring important
data (I think you've told me that you do I'm not sure) then store all of your valuable data
into your mom's computer or whatever. Put your windows CD into your disc drive and run 
windows setup.  As soon as it says "starting windows" delete the ubuntu partition. Press
C to create a new partition in the empty space and put as much space as you want into another
partition. After that continue the windows setup as normal in any partition. After you finish installing windows, wait for it to load to the desktop and put in your ubuntu installation CD and
reboot. Then install ubuntu on your other unpartitioned space.  After it's done DON'T REBOOT.
Check your partition flags on the live CD. If you use windows often skip this step. You can boot Ubuntu from safe mode menu thingy later. If the flag 'boot' is checked on the windows partition
uncheck it. Then check the ubuntu 'boot' flag. If you choose to boot from ubuntu it still gives you
10 seconds to select which operating system you wish to choose. :D

---

### Post by Dojan5 on 2008-03-25
I forgot to tell you that my mothers computer have only 6 gig and he data is over 20...
Anyway, i solved it.
To be honest, it was just to do the installation, during the install it will ask for if i wish to use the whole hdd or split it, as a bonus it creates a swap.
Plus currently i am using enlightenment, so, not only is it good looking, it is fast too... :D
Thanks anyway for your help, it is much appreciated

---

