---
title: "Recover grub after deleting some partition"
date: 2013-02-16
forum: General Help
---

### Post by seragx99 on 2013-02-16
Hi guys! i'm sorry if the post sounds reiterative, it's just that i've seen so many workarounds to my problem that i'm not really sure which one will work in my case.
This is the scenario:

1. I accidentally erased one partition in my hdd. 
Details: I have a dual boot system (win7, ubuntu 12.10), so i thought i had 4 partitions, 2 for each OS+1 that came with my computer for recovery, + 1 for linux swap, I noticed that i had 2 swap partitions, so i thought it was a leftover from a previous Ubuntu installation and chose to erase it, since it was considerably smaller than the one i (remember had) made for my actual installation. Big mistake.

2. When i restarted the system i saw the Grub rescue prompt, "no such partition". After searching and trying a lot i found this solution:
```
set root=(hd0,msdos6)
set prefix=(hd0,msdos6)/boot/grub
insmod normal
normal
```3. After previous step i could boot again, both win and Ubuntu. My problem right now is that... i have to type all of that every time i turn on my laptop and some times Ubuntu won't load . 
I already used ```
sudo update grub
``` but it remained the same. I understand that i have to make Grub stop looking for the actually non existent partition. Is there a way to do that? Do i have to reinstall Grub? 
Thanks in advance!

---

### Post by raja.genupula on 2013-02-16
you'd better to make a move with Boot-repair.
look at my signature for Grub -recovery,
Thats going to help you .

---

### Post by oldfred on 2013-02-16
Boot-Repair will work.

But if you are in your Ubuntu install you can just reinsall grub's boot loader to the MBR.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub
    
You can also do this.
       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by seragx99 on 2013-03-14
Thank you guys, i managed to get grub showing again (i don't get the "grub rescue" prompt anymore) so my computer is back to starting as normal, but still after i choose Ubuntu on grub it tells me that some partition is missing so i have to press "s" (for skip) to continue loading system, it's less annoying than the grub rescue, but is there a fix for this?

Oh i almost forgot! since i wasn't sure wich drive was correct i used 
sudo dpkg-reconfigure grub-pc
and that solved the grub rescue prompt at start up. Since the partition missing message still appeared i used 
sudo grub-install /dev/sda 
and it said no problem, but the message still shows...

---

### Post by oldfred on 2013-03-14
Were you mounting the partition you deleted with fstab? If so it will give that error message until you delete it from fstab.

---

### Post by Moose on 2013-03-14
Usually, if I have this sort of issue, I keep a copy of Puppy Linux lying around. So that I can install the Grub loader from the Live CD. It is good because it automatically detects the operating systems installed and you can customise the boot menu yourself! Not the quickest or simplest way, but that's how I choose to do it. ^.^

---

### Post by seragx99 on 2013-03-18
So, all of a sudden my wireless hardware went crazy and i got mad at ubuntu and decided to simply wipe it all and do a clean install, not the first time it happens but still supporting Ubuntu, i'm writing from my new install and hoping to learn, thank you guys!

---

### Post by patrickcage on 2013-03-18
> **seragx99 said:**
> So, all of a sudden my wireless hardware went crazy and i got mad at ubuntu and decided to simply wipe it all and do a clean install, not the first time it happens but still supporting Ubuntu, i'm writing from my new install and hoping to learn, thank you guys!


Hey, sometimes it's just quicker to start again! At least we don't have to worry about 25 digit keys and activation ;)

---

