---
title: "need to access hard drive from live cd"
date: 2005-10-19
forum: General Help
---

### Post by randall550 on 2005-10-19
i broke my system. i tried to use apt-get dist-upgrade to get breezy. i don't know if i actually ever had breezy, but i had all the breezy repos, and of course it was buggy. so today, now that breezy is released, i figured i would run update on synaptic, and it proceeded to remove a bunch of programs that i need. like kde, synaptic, terminal, firefox and long story short, my hard drive installation of ubuntu "whatever the critter is" is busted flat.
okay so i think "well i really dont need breezy all that badly at this time," so now im running hoary live. i can do a clean install, but i really dont want to lose my files. but i dont know how to access my hard drive so i can tar them or whatever it is i need to do. how can i get to my home directory on the hard drive and save my stuff while i am runninhg hoary live? and is there something i can do other than a clean install?:confused:

---

### Post by aysiu on 2005-10-19
Launch the live CD. Then, type this in a terminal ```
sudo fdisk -l
``` It'll show you what your partitions are called and what type they are. Let's assume, for the sake of argument, that your /home folder lives on /dev/hda3. ```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/hda3 /ubuntu
``` Now there will be a "directory" in /ubuntu that will have your old installation and /home folder in it.

---

### Post by nthwaver on 2005-11-14
I am having a similar problem.  After running HH on my PC for only a few weeks, one day it stopped booting completely - the process would always hit a standstill and the screen would freeze.  I've been running an HH Live CD for day-to-day purposes (www and gaim) but would really like to get the hard drive back.  The easiest thing would be to reinstall with BreezyBadger, as I'm still experimenting and learning anyway, but before wiping the hard drive I want to save the files I'd kept on the desktop.

I tried your instructions and kept getting this message:

   mount: /dev/hda already mounted or /ubuntu busy

All I want is to access a few files on the desktop, zip them and e-mail them elsewhere so I can safely re-format the drive.  If the drive is already mounted, how do I access it?

Thanks!

---

