---
title: "[SOLVED] update = no boot"
date: 2007-10-20
forum: General Help
---

### Post by skymera on 2007-10-20
ok ive just restarted from the updates that jus popped up,
retsarted like it said.

and after grub no boot, just a black screen, no HD activity or anything!

anyone else?

although more liely reason is i saw a command to eun

sudo dpkg reconfigure -a

that may have vchanged settings, how i restore them?

---

### Post by DagMan on 2007-10-20
assuming issuing the command is the problem, and you have a cd with the gutsy kernel then you can boot into it, start mounting partitions with / for example, 
sudo mount /dev/sda1 /mnt
sudo mount /dev/sda2 /mnt/home
etc
then 
sudo -s
chroot /mnt /bin/bash
and then you can issue the command you skipped, and close the terminal when you finish, or type exit.  Then unmount your partitions.
You might be able to get away with it using another CD besides gutsy if you don't have one though not sure.


Also while in the live CD environment, in a differant terminal, maybe looking at how to setup grub again is worth investigating too, in case this is the problem.
There's a tutorial in the tips and tricks section

---

### Post by skymera on 2007-10-20
thanks, thats just what i was looking for but,

how do i make it do it itself, i mean

like xorg, 

sudo dpkg-reconfigure -phigh xserver-xorg

would anything like -phigh work? to select whats right?

---

### Post by skymera on 2007-10-20
ok it works!
yay

man you are a life saver!

many thank yous.

---

