---
title: "Triple boot help"
date: 2007-08-31
forum: General Help
---

### Post by pspfreak101 on 2007-08-31
So far I have a dual with vista and dreamlinux, and I wanna triple boot with ubuntu server edition because I'm having some problems with my windows server. Anyways I wanna keep my dreamlinux grub menu but I'm not sure how to do this and I can just partion another part of my hardrive and ubuntu should notice vista and dreamlinux right?

---

### Post by louieb on 2007-08-31
Just so you realize Ubuntu server does not come with a GUI. But you can add one later. At a minimum you need one partition for / (root) of your Ubuntu install. You can and probably used the same swap partition for both Dream and Ubuntu. 

When you get to the Grub part of the Ubuntu install. Set it up so that it  installs in the boot sector of the Ubuntu / partition. This will leave the Dream Linux grub still in control when you reboot it. 

You will then add an entry to the Dream Linux Grub configuration file to use the chain loading or configfile option to boot Ubuntu. I have used both and they both work nicely. See the [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/") for the config file and chain loading how to.  Great site for anybody wanting to dual... triple ... whatever boot.

---

### Post by pspfreak101 on 2007-08-31
Thanks :) ,well I'll post back here if everything goes good

---

### Post by pspfreak101 on 2007-08-31
hmm I made a new portion but on the ubuntu installer it said it is unusable and on windows when I try to format it, it won't let me

---

### Post by louieb on 2007-08-31
Which install CD?  Did you create a partition or leave some disk space unallocated. If you left some disk space unallocated it could be unusable depending on its location. Can you install Gparted in DreamLinux it would help to see a screen shot of  GParted. Or if you have internet with the live CD GParted is under System>Administration I think.  I have some partition links here [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm") it might help you to understand what you can and can't do when setting up your disk partitions.

---

