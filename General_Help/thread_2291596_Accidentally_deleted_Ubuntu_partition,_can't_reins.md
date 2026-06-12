---
title: "Accidentally deleted Ubuntu partition, can't reinstall no matter what I try"
date: 2015-08-21
forum: General Help
---

### Post by thomas60 on 2015-08-21
Hey guys, I'm having a bit of a problem here as I accidentally deleted my Linux partition, but in kind of a weird way so I can't reinstall. I'm just gonna list in chronological order exactly how I messed up so maybe you can help me.


I had installed Ubuntu a couple days ago. I had manually shrunk the windows paritition beforehand, but accidentally installed Ubuntu on a new partition anyway, so I was left with an extra partition. I tried to add this partition back to the Windows parition using AOMEI Partition Assistant in windows. After it was done I couldn't boot into Ubuntu anymore, and it turned out that my Linux partition had been deleted. I thought, nbd, I'll just reinstall, but here's where the problem starts:


Everytime I try to reinstall from a live USB, it gives me a ton of nouveau errors (like hundreds of them) and then just reboots into windows. I can't even run Ubuntu from the USB itself (also a bunch of nouveau errors). So, do you have any idea what might be going on and how to fix it? Thanks!

---

### Post by dino99 on 2015-08-21
ok starting with the basics:

- dont mess windows installation : if you want to resize/shrink its partitions, then boot on the windows cd to use its formatting app (as this always been done on unmounted partition)
- you need to know how 'windows' is installed: does it use efi/gpt ? as you will need to do the same choice to install ubuntu (to avoid trouble then) ('oldfred' have made lot of posts/threads about 'installing ubuntu alongside windows, search about him on ubuntuforums to find)
- the best way to skip errors (like wipping partition or else) is to prepare the required ubuntu partitions:
 a) boot with 'gparted live' ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) )
 b) set the unused hdd/sdd space left off windows installation, as a whole 'extended' partition
 c) inside that 'extended' partition, set 3 other partitions: / (root) as ext4 & about 15 Gb , swap about 4 Gb, and the rest as /home , ext4,to store your settings and data

now that the ubuntu partitions are prepared, then you can boot with the ubuntu iso to start the installation: when the installer will ask where you want to install ubuntu, then you select 'something else' option that mean 'manual' installation, so you can select the previously created partitions (something like /dev/sdx you have noted while creating them).
Later the installer will ask where to install the bootloader (grub), so you will do a manual choice here too: /dev/sdx, corresponding to the mbr ubuntu partition, (probably /dev/sda)

---

### Post by v3.xx on 2015-08-21
> I can't even run Ubuntu from the USB itself (also a bunch of nouveau errors).

Before doing anything else, I would suggest that you get your installation media working again.  Reinstall the media to your USB and test it by running a live session without installing.

Do you have a windows backup?  A way to reinstall windows if it breaks?  Editing partitions usually goes smooth, but if it breaks, it usually breaks in a big way.

I do not know exactly whats going on, but this is where I would start.

Edit
Ninja by dino :)

---

### Post by thomas60 on 2015-08-21
I have a back-up of my data and a windows 10 iso on a usb stick, so I can always format and reinstall should it be necessary. I can run a live session on other PCs just fine, but on my laptop it just keeps hanging on the loading screen and I have no idea why. I'd like to fix that first before I try what dino said.

Edit: I have run Boot-Repair for anyone interested: [http://paste.ubuntu.com/12142341/](http://paste.ubuntu.com/12142341/)

---

