---
title: "startup error 17"
date: 2007-12-05
forum: General Help
---

### Post by mrroboto1 on 2007-12-05
howdy. im completely new to linux, but i chose it as something that would serve as both a more functional and stable os rather than xp which has lead me though nothing but years of hassle....soooo my issue i recently got a sony vaio through a coworker cheep since xp was beyond gone so i opted to load ubuntu. i loaded off an old vers 6, then gave it to a more computer savvy friend of mine to load the new gusty version. well his skills turned to be a little less than i expected what im left with is a boot error 17 during grub 1.5, and thats it. its hangs up. i have no idea what happened from when i gave it to him working and when i got it back with one foot in the grave. ive tried reinstalling gusty as well as xubuntu just for kicks and it hangs up at 5% of a full hd instillation. i can run the live session fine but i cant modify my hd at all. theres no data on the old os i need to save so no worry if i haft to wipe it out completely. any help would be greatly appreciated but keep in mind you'll haft to put it in somewhat simple terms as my knowledge of linux is severely limited

thanks ubuntu community,
joseph

---

### Post by Aseld on 2007-12-05
Ah, yes, the dreaded Error 17. 

Are you sure that the installation hangs? How long did you leave it to check? If you run GPartEd from the live CD (Desktop->Administration->GPartEd) what do you see? Which partitions are listed?

---

### Post by mrroboto1 on 2007-12-05
dev/sda 55.89GiB

partition; unallocated
filesystem; unallocated
size; 55.89GiB
used;---
flags;---

if i view the device info its listed as an unrecognized disklabeltype

i let it sit for about an hour and it just sat

---

### Post by mrroboto1 on 2007-12-05
if it helps, when i run the gparted i get this;

ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 - unrecognised disk label.
Unable to open /dev/sda - unrecognised disk label.
ubuntu@ubuntu:~$

---

### Post by Aseld on 2007-12-05
I'm sure there's a good and easy way to do this properly, but I don't know it, unfortunately. What I recommend you do is if you have a Windows install CD (can already be in use) use it and run the installation just until after it's formatted the hard drive. Then do a fresh Ubuntu install. Again, sorry, I know this isn't the best way, but I don't know any others, and it's always worked for me.

---

### Post by mrroboto1 on 2007-12-05
ill try to track down an install cd. the comp didnt come with a disk and vaios use a system recovery type disk that didnt come with it. thanks allot for the help

---

