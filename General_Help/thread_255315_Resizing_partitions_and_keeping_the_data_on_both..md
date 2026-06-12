---
title: "Resizing partitions and keeping the data on both."
date: 2006-09-11
forum: General Help
---

### Post by Timothy Butwinick on 2006-09-11
Hello there!
I have one 4 GB partition for my Ubuntu system, and one on 26 for Windows. Is there a way to resize them without losing their data? In Windows, there is a programme called "Acronis partition expert", but I would like to do it from Linux.

---

### Post by 505 on 2006-09-11
Never done it myself, but according to the website it is possible. You need GParted for this, it's available through Synaptic. To resize NTFS partitions (which I assume your Windows partition is) you also need ntfsprogs. See [this table](http://gparted.sourceforge.net/features.php) for more information.

---

### Post by bernied on 2006-09-11
The applications that I know of are
parted
qtparted
gparted
The last one has it's own live cd. Since you'll need to do this from a live-cd anyway, it's as good a choice as any. The first one is command-line and clunky, the second and third are flashy graphical things.

Some advice though:
- Use a live-cd, don't try to resize partitions that you are using
- Don't resize a partition with valuable data (or applications) in it if it is not backed up.
- defrag any windows partition first
- maybe, if you want to double the size of the linux partition, you could shrink the windows one (assuming it's the first) by 4GB, then create a new one in between the two OSs, move the data from the linux partition (use 'cp -R --preserve' but look these commands up first) to the new one, see if it boots and runs ok, then delete the last partition, then grow the linux partition into the empty space. It gives you safety for your linux partition, but not your windows. Just remember that your ubuntu install on the third partition won't work because the boot parameters will be looking for it on the second.

Confused?

Good luck.

---

### Post by bernied on 2006-09-11
You may also need to reinstall grub, though I'm not sure about this. The grub master boot record (first 512 bytes of the disk) will look for the second stage of grub on your linux partition. If it is looking for 'the second partition' then everything is fine, but if it is looking for a particular point on the disk, then this will have changed. I suggest you deal with this if it happens though. You can reinstall grub with your ubuntu live cd (this incidentally should also have parted on it).

Just be prepared for your machine to be in a broken state half way through your messing about. Make sure you have internet access, say using a live cd, before you start, so you can look for more information.

---

### Post by bernied on 2006-09-11
Just to clarify, grub is the bootloader used in ubuntu, it runs first when you start up. It is the second stage of grub that gives you the option of which operating system to start.

---

### Post by Timothy Butwinick on 2006-09-11
Thank you.
Now I've got two ext3 partitions (8GB and 4GB respectively, my system is on the smaller one). Is there a way to merge them to make a big partition? There is no wayto do this in gparted.

I *could* just reformat the small one, since I don't have anything valuable on it yet, but I'd prefer not doing that.

I tried copying the system drive to the big one to be able to expand it later, but it wouldn't let me copy /proc/kcore (and some other files in the /proc directory), even though I used sudo. After this, it did not finish, but it stopped working.

---

### Post by bernied on 2006-09-11
You need to do the copy operation from a live-cd. 
The filesystem in the /proc directory is not on the disk, it is a system that gives you information about all processes that are currently running, including the kernel processes. These are not files that you want to be messing with. If you look at the proc directory of your ubuntu install when you are not running it, you will find it is empty.

---

