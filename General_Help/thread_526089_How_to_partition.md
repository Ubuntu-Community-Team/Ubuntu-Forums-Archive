---
title: "How to partition"
date: 2007-08-15
forum: General Help
---

### Post by barisy on 2007-08-15
Hello everyone :)
I need to learn how to get the second unformatted space online, since i have 160 Gig disk on my desktop and i installed the Ubunutu 7.04 on the 20 Gig part of it and i just want to have a second disk drive .. 
Thank you.

---

### Post by jw5801 on 2007-08-15
So you have on your HDD a 20GB Ubuntu partition and 140GB of free space? Install GParted (sudo apt-get install gparted) and use that to format the unused space into a second partition. Alternatively if you want to expand the Ubuntu partition then the GParted LiveCD is a much better bet, it's a much newer version with more options and you boot from it so you don't need to worry about Ubuntu mounting the partition while you're trying to resize it. You can get it from the link in my signature.

---

### Post by barisy on 2007-08-15
i did it but some buttons on gparted are disabled e.g. Resize/Move etc. i can say all the buttons are disabled?! that's weird 8-[

---

### Post by splintercellguy on 2007-08-15
Make sure to unmount all partitions.

---

### Post by barisy on 2007-08-15
```

root@baris:/home/baris# umount -af
umount2: Device or resource busy
umount: /dev: device is busy
umount2: Device or resource busy
umount: /var/run: device is busy
umount2: Device or resource busy
umount: /sys: device is busy
umount2: Device or resource busy
umount: /: device is busy

```
i closed all the applications but no success why?

---

### Post by jw5801 on 2007-08-15
You can't unmount your root filesystem, Linux needs that to do stuff! :p
Download the GParted LiveCD and boot from that (link in my sig), and you'll be able to do whatever you would like to your partition!

---

### Post by barisy on 2007-08-15
cannot have partitions without liveCD?! oh god! :) anyway like to struggle ..
Thanks for your help

---

### Post by jw5801 on 2007-08-15
Of course you can create and destroy partitions without a LiveCD! You can even resize and edit them. Just not while they are mounted, ie. while you can read/write to them. So If you wanted to just make a separate partition using your free space then that won't be a problem.
However, since it's kind of a necessity to be able to read and write to your root partition (the one that contains /, or C: in Windows, or whatever it is that Mac users call it :p) you can't unmount it whilst the OS is running. Therefore you'll need to use a LiveCD to move/resize it. The Ubuntu LiveCD actually has GParted on it so you can use that if you wish. The only reason I recommend the GParted LiveCD is because it's a very small download (less than 50MB), you won't have trouble with gnome-volume-manager auto-mounting any partitions it finds, and it contains a much newer version of the software.
Hope that clears things up a bit.

---

### Post by barisy on 2007-08-15
Ahh ok i understand, but there's something that i have to ask, why Ubunutu uses unpartitioned extra space (i mean my the empty 140Gigs - total 160, used 20gigs for Ubuntu) and i could not give e.g. extra 20gigs maybe to the system? Since i couldn't unmount that part either, remember? :-k

---

### Post by jw5801 on 2007-08-15
I have absolutely no idea how you ended up with Ubuntu on a 20GB partition and the rest blank... lol. The default install should use the entire disk unless you tell it otherwise. What do you mean by giving another 20GB to the system? Adding to the swap partition? That shouldn't really be necessary, 2 or 3 GB of swap should be plenty, any more won't make any difference to performance, and if you have a reasonable amount of RAM you'll rarely use it anyway. Or do you meant adding it to /sys? /sys shouldn't be on a separate partition anyway: the only reason it shows up after umount -a is because it's one of the folders preventing you from unmounting the root filesystem.
What does GParted have to say about your partitions? Does it register as one partition with a Mountpoint of "/" and a big bit of unformatted space (and some swap at the end)? If you want to just create a new partition to store files and stuff on (or even to put your home directory on, we can help with that if you want to go down that road!), then you should just be able to right click on it and format it to something useful (ext3 is best for Linux) without using a LiveCD. But if you want to resize the root filesystem (probably the simplest option) then you will need to use a LiveCD.

---

### Post by barisy on 2007-08-15
in windows there was a concept of C: and D: etc. :) i have worked with AIX we able to give extra space (disk) to the available system when we need, here i run the GNOME Partition Editor and try to edit the other huge empty space /dev/sda3 ext3 and it says me "you better unmount them manually since other partitions connected to it :P  anyway .. lol

---

### Post by jw5801 on 2007-08-15
/dev/sda3 ext3, is not empty space... /dev/sda is your harddrive! /dev/sda1 will have a boot flag and will contain all the system files. /dev/sda2 will be your swap partition (called page file or something along those lines in Windows), and /dev/sda3 will be something else. I have a similar setup, /dev/sda1 is '/', /dev/sda3 is my /home/ folder. Linux is quite nifty in that it can use what Windows would call different drives as folders within it's root system. /dev will contain all your devices (hard disks etc etc), but you can't use them from there. First said drive must be "mounted" and can be mounted to any existing empty directory. I have /home/ on a different partition in case I wind up breaking something badly so I need to reinstall, becuase that way I don't lose any of my files or settings for all my apps (all of these are stored in your home directory). There is a file (/etc/fstab) which tells linux what it should do with any partitions it finds.
I think the best option in this case is just to remove /dev/sda3 and expand /dev/sda1 to fill the rest of the disk. What does GParted say it's mountpoint is? Just to make sure deleting it and expanding the root partition won't break anything.

---

