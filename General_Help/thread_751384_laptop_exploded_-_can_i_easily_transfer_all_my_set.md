---
title: "laptop exploded - can i easily transfer all my settings to my desktop?"
date: 2008-04-10
forum: General Help
---

### Post by bluepowder7 on 2008-04-10
so i've been using my laptop nearly exclusively for the past few months, to the point that my desktop's ubuntu install didn't go beyond the install.  now that something on my laptop's mobo went POOF and it no longer boots, can i just copy a bunch of my config files from the lappy's hard drive onto the desktop drive?  the lappy drive is a SATA, so i ought to be able to plug it into the SATA ports on the desktop's mobo, then mount the various partitions, and copy various files over.  will that actually work?

things i want to copy over would be firefox bookmarks, firefox passwords (where are those stored?), compiz-fusion settings, etc.

it's going to be a PITA to remember which programs i had installed and then to reinstall them on the desktop, but once i get past that, can i then copy over the relevant configuration files?

and...  um...  silly question, but where exactly ARE those config files?  as in, what path?

---

### Post by PriceChild on 2008-04-10
All applications store their configuration in your home folder, but in folders starting with a period, which makes them hidden normally.

You could simply copy the entire contents of the /home/your_username folder onto the new machine.

if you want to also install all the same applications, you could first chroot into the install... ```
sudo chroot /media/wherever_you_mounted_it
dpkg --get-selections > my-packages
```Then type exit to leave the chroot. You can then copy /media/wherever_you_mounted_it/my-packages to your home folder on the new machine, and do```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

---

### Post by bluepowder7 on 2008-04-10
does the fact that i have the / (root) and /home on separate partitions of the lappy drive complicate things?  i assume that the chroot should be with /media/the_root_partition_that_i_mounted, correct?

hmm, i have a 40G IDE drive in the desktop that's empty (my OSes are on a SATA, and the pc boots into the SATA, so the 40G IDE is there as extra storage space).  would it make it easier if i were to first copy the lappy hard drive's / (root) and /home partitions into one single combined partition on that 40G drive, and THEN do the commands you listed?  not sure if i can do that "recombine onto 40G drive" thing via nautilus or if i need to sudo it all from the terminal...  your thoughts?

what i might do at this point (since my desktop install is so utterly bare anyways) is install the 64-bit version of 7.10 on the desktop and then do the whole thing above.  i should be able to install it over top of the current 32-bit 7.10 install and HOPEFULLY have GRUB keep my existing Win2k and WinXP installs working, right?  grub seems to be smart enough from what i've seen thus far...

---

### Post by PriceChild on 2008-04-11
You only need to bother with this chrooting if you want to bother with cloning the package selection on your new system. If you do do this, you don't need to worry about the home partition, it isn't needed to complete the above process.

If you don't want that, then you can just copy files from your home partition as though it was an external drive.

---

