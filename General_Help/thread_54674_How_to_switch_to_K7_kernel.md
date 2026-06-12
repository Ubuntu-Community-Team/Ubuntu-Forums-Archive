---
title: "How to switch to K7 kernel?"
date: 2005-08-05
forum: General Help
---

### Post by Bandit on 2005-08-05
Hello everyone,
I am running a AMD AthlonXP 2GHz and have 1GB of RAM.
Ubuntu only sees 858MB of RAM. I susspect that is may be becuase I am running the default i386 kernel. 
How would I change my kernel to the K7 (AMD) one in Ubuntu 5.04?
BTW, this is the best Linux Distro ever...
Cheers,
Joey

---

### Post by orev on 2005-08-05
Use synaptic to install the K7 kernel and then reboot.  The K7 kernel will be one of your boot choices in grub (if your using that).

After I installed it, it came up as my default kernel.

---

### Post by ameerirshad on 2005-08-05
Well you're question is already answered! I'd the same, just after installing the standard i386, I ran synaptic, installed the K6 and later the K7 as well, reboot, using GRUB to select the K6 version (K7 refused to load with me), and then I removed the i386 as it ain't necessary to have 2 versions of the Kernel!

---

### Post by Bandit on 2005-08-05
Thanks, didnt know it was that simple. Been using SuSE for so long, SuSE makes things just to complicated..
I didnt see the K6 kernel, but the K7 kernel did fix my memorey problem :)
Thanks Everyone,
Joey

---

### Post by ameerirshad on 2005-08-06
Well I can imagine, as I switched from Suse to ubuntu as well! I wanted to try Debian actually, but wow, before Sarge that was impossible to install for me as Windows user! So I started out with Suse......... never been able to update 1 program there, Yast sucks! Then I stumbled on ubuntu, later someone adviced me to ubuntu and then I made the switch........ who talks about windows these days?\\:D/

---

### Post by ameerirshad on 2005-08-06
Hmmm I made 1 mistake: I said K6 instead of K7,:-\" but I see I am running K7 as well........ have no idea how that is possible as I remember from somewhere in July that I was running a "instable" kernel which refused to load, fortunately then I'd still i386 installed so rebooting and selecting the i386 solved the problem!

I don't know, maybe with some update or something :-P

---

