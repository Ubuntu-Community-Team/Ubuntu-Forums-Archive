---
title: "I need more HDD space for Linux"
date: 2008-03-21
forum: General Help
---

### Post by daxdog on 2008-03-21
I bought a new Dell XPS-M1330 a few weeks ago.  I have it dual booting into Ubuntu 7.10 and Windows Vista.  I originally setup only a 20GB partition for Linux and left the rest for Windows.  Yesterday was the first time in two weeks that I booted into Windows and that was to show a co-worker what her new Dell computer with Vista would look like.  I don't use Windows anymore, but I am scared to totally blow it away because I am not a Linux expert yet.

Can I repartition my drive (both EXT3 and NTFS partitions) without data loss?

---

### Post by justleen on 2008-03-21
yes, you should be able to resize without dataloss, with something like gparted

But with resizing you always risk data loss..  If you do resize make sure you run defrag on the windows disks (from windows)

And no, you cannot repartition without dataloss. to spilt up one partition in two, or join two partitions, you will have to recreate the parition table which destroyx the data. Only way around that is backing up to a third partition / disk /dvd

---

### Post by daxdog on 2008-03-21
I'm wanting to reduce the size of my ntfs partition and increase my ext partition.

Here is what I have:
/dev/sda1   fat16   Dell utilities
/dev/sda2   ntfs     Windows Vista  80gb total/47 used/33 free
/dev/sda3   extended   31.74gb total
   /dev/sda6   ext3   Linux   18gb total/9 used/9 free
   /dev/sda7   linux-swap   11gb
   /dev/sda5   fat32             2 gb total/691mb used/1.33gb free

I had to install gparted as it apparently does not come with the default Ubuntu install.   If I boot to a LiveCD is there a way for me to load it?

---

### Post by coninsan on 2008-03-21
You simple download a .iso file called gparted live cd, install that .iso on a empty disk and boot from you new gparted live cd, it will alow you to resize all your partitions without a hitch, but i would advise you to make a system backup before you do it.

i resized my partitions just yesterday and it whent well, but although it goes well most of the time, it must go wrong at some point, murpheys law if you will. :)

you can get the live cd iso here: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by Awperator on 2008-03-21
Doesn't the Gutsy live CD have GParted on it as well? I used it recently to resize my linux partition, warning though:

Backup your system
Give it time because it might take a while.

Good luck

---

### Post by justleen on 2008-03-21
you can install anythig from the repros while booted from a live cd.

so if gparted is not available on the live cd, just run sudo apt-get install gparted..

---

### Post by prshah on 2008-03-21
> **daxdog said:**
> 
Can I repartition my drive (both EXT3 and NTFS partitions) without data loss?

Yes, sure.

Boot off your live CD, and run the partition editor System-> Administration-> Partition Editor (or install it using "sudo apt-get install gparted").

You HAVE to use a live CD for this, you cannot resize/muck about with partitions when they are mounted.

gparted is pretty much self-explanatory and easy to use.

As long as you don't turn off your laptop in the middle of the resizing operation, it will go through without a flaw.

---

### Post by jespdj on 2008-03-21
> **daxdog said:**
> Here is what I have:
...
/dev/sda7   linux-swap   11gb
...
Why do you have such an enormous swap partition?! A swap partition of a little bit more than the size of your physical RAM is more than enough.

---

