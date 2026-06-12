---
title: "Server and RAID0"
date: 2006-07-24
forum: General Help
---

### Post by umattu on 2006-07-24
I have been looking high and low for some help on this one. I am trying to install ubuntu server using the software RAID0 configuration. After an hour of messing with hthe partitioning I got the install going. When it got to the point to install GRUB it took a crap on me. It tells me that it can't install grub to the MBR of /dev/hd0/ now Ive tried pointing it to install to MD0, RAID0  and so on so forth. I have not been able to find any useful info to help me out on this one, (heck I even have the complete server user guide printed out and bound up nicely) even that guide doesn't have anything on the RAID configuration installation process. I need help on this one. I did find one thread where someone said something about RAID0 not being bootable at all and I just can't beleive that. 

Someone please help!!

---

### Post by JoWilly on 2006-07-24
As you said, software raid0 is not bootable.

You need to make a /boot partition at the beginning of your first disk (about 100mb).
Example if you have 2 disks and want 2 raid0 partitions, this is what I would do:

HD1:
partition1: 500 mb /boot
partition2: 20 Gb raid
part3: 40 Gb raid

HD2:
part1: 500 mb swap
part2: 20 Gb raid
part3: 40 Gb raid

In this example you put 500 mb /boot so you have a 500 swap, this way all raid partitions can be of the same size (important for raid performance when disks fill up).

Then, add the part2 on each disk to a raid (md0) and part3 of each to md1.

So now you have:

/boot
/ (root is md0)
/media/anyname (md1)

You put grub on the HD1 mbr and set your bios to boot from it.

---

### Post by umattu on 2006-07-25
Thanks a million, I now understand why it wasn't bootable. So far its running like a champ. I have been using ubuntu for 4 months now and as my main OS for 2 months. I knew ubuntu would not let me down.

Thanks again!!!!!!!!!!

---

