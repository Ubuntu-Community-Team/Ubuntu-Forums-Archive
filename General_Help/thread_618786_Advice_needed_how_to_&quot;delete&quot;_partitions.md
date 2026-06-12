---
title: "Advice needed: how to &quot;delete&quot; partitions"
date: 2007-11-20
forum: General Help
---

### Post by Korrontean on 2007-11-20
Hi, I am totally illiterate about partitions.. in fact, a friend set this configuration for me.

Can you check it from the image attached?

I need to store all my files in ONLY ONE PARTITION... I guess a "swap partition" is needed for the operating system to work, but I want all my stuff together in one partition.

Could you explain me step by step how to cancel the partitions and get ALL MY FILES together?

I don't know if I explained myself very well... :confused:

Thanks a lot!

---

### Post by bodhi.zazen on 2007-11-20
You will have to manually move your files (with nautilus)


GParted:

	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by Korrontean on 2007-11-21
Thank you, bodhi.zazen, but I find the gparted documentation rather difficult.
Also, as I don't have enough room in any of the current partitions shall I pass the files progressively as I make one of the partitions bigger and the other smaller until I can delete it?
Where's my operating system supposed to be?
Is the re-sizing of a partition a critical operation? For both partitions, the one growing and the one getting smaller?
Too many questions, I know.........but I feel totally lost :(

---

### Post by bodhi.zazen on 2007-11-21
Oh, OK, sorry

Managing partitions is not too difficult, however, if this is the first time you can be faced with data loss or an un-bootable system if you aer not careful, meaning you understand exactly what you are doing.

Take a look at these threads for some information :

Basic partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

While not exaclty what you are doing see also this thread :

[http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

With that second thread in mind, you may need to edit BOTH /etc/fstab and /boot/grub/menu.lst after you re-configure your partitions.

See also here :

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

=============

OK, then,

Well, to be honest, the Gparted documentation is awesome, screen shots are included and it is hard to top ... I will try if you have a specific question ...

=============

Last, yes it sounds like you will need to either back up your data to and external media (CD/DVD/Flash driver) or step through resizing ...

If you step through resizing, keep in mind a partition needs to be **mounted** to move (copy) data and **un-mounted** to resize or move the partition (with gparted).

=============

So, yes, if you are a new user, what you are about to undertake is fairly complex and you will need to do some reading ...

Don't start if you do not have a good grasp of what you are doing, and please back up any critical data first (if you make a mistake recovering lost data will be almost impossible and, at best, incomplete and even more technical).

---

### Post by ronmarley1 on 2007-11-21
As  bodhi.zazen suggested, I think that backing up to external media would be easier.  Since it looks like you have about 35 gig, maybe an external hard drive?  You can get a huge one for about $125 if you have the cash.  This would also give you a nice place to back up your stuff.  Then, you can do away with the /media partition using gParted and resize your root partition to take the freed space.  
Again, bodhi.zazen mentioned how partitions need to be unmounted to resize.  This can be done with the Ubuntu LiveCD, or, as I prefer, the gParted LiveCD at [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/).
Listen to what bodhi.zazen says, as you really can bork your system when changing partitions.

---

### Post by Korrontean on 2007-11-22
Thank you very much, bodhi.zazen and ronmarley, I'll read through all the documentation and start the process when I have the time... unfortunately not this week. Thanks! :)

---

