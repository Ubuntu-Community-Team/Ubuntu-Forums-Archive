---
title: "How do I extend a partition? Plus other questions"
date: 2007-02-07
forum: General Help
---

### Post by Vasant56 on 2007-02-07
Hi, I was wondering how I might extend a partition on my computer. I have 3 partitions set up, and 5 gigs of unpartitioned space. Is there any way I can partition my drives in Ubuntu?

Also,
I think I screwed up my settings trying to install beryl is there any way I can kinda of just "reset" my environment without formatting?

Thanks so much for all of the help

---

### Post by dexter on 2007-02-07
> **Vasant56 said:**
> Hi, I was wondering how I might extend a partition on my computer. I have 3 partitions set up, and 5 gigs of unpartitioned space. Is there any way I can partition my drives in Ubuntu?

You can use gparted to resize your drives
sudo apt-get install gparted
After it's installed, it can be found in System->Adminstration->Gnome Partition Editor
> **Vasant56 said:**
> 
Also,
I think I screwed up my settings trying to install beryl is there any way I can kinda of just "reset" my environment without formatting?

Do you still let beryl start up ? You can disable beryl at startup by removing the command (probably beryl-manager) in System->Preferences->Sessions->Startup Programs

---

### Post by Vasant56 on 2007-02-07
Hi, I tried

umount hda4 and i got this error:

umount: /dev/hda4 mount disagrees with the fstab

could you give me instructions on how to use gparted? I have absolutely no clue.. I want to append all extra space to hda4.

thanks a lot

---

### Post by raul_ on 2007-02-07
In order to resize a partition, it can't be mounted. So you can't resize your Linux partition when you're in Ubuntu, and you can'r resize your NTFS partition if it's mounted. The safest way to do this is to boot from the Live CD and use GParted from there. It's pretty self-explanatory. 

```

gksudo gparted

```

---

### Post by schibros on 2008-05-03
[QUOTE=Vasant56;2120502]Hi, I was wondering how I might extend a partition on my computer. I have 3 partitions set up, and 5 gigs of unpartitioned space. Is there any way I can partition my drives in Ubuntu?




I installed Gutsy 7.10, using the manual installation option. I Had vista preinstalled on my Compaq F700. To install Gutsy on it, i had to reformat the whole system, and then repartition the hard drive so i could use some space for Ubuntu. During the manual installation, i gave only about 4gb space to my root partitio, and 1024MB for my swap partition, then about 30gb for my Home partition.

I just realized that the amount of space i have left on my root partition is only about 800MB. This will be a serious problem for me, if im trying to upgrade or maybe install some more stuff.

QUESTION

(1) Can i run Gparted from inside Ubuntu, if i can, i hope it will not mess up my boot process.

(2) When i boot from the Gparted CD, and resize the partitinons, will it have any effect on my boot process? 

Thanks in advance.

---

