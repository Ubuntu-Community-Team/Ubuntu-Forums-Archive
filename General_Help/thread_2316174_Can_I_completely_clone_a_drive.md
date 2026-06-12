---
title: "Can I completely clone a drive?"
date: 2016-03-05
forum: General Help
---

### Post by Evil Wayz on 2016-03-05
Ok here's the deal.  Couple years back my computer took a complete dump on me in the middle of an important project, and I hurriedly bought a new box off the internet for cheap.  It had a 40 gb drive in it and it got me on the internet so it was fine at the time.  I added a 2 tb drive and everything was fine.  TOday, that tb is slap full of stuff I need.  It's basically a data drive.  THe problem is now the os drive, the 40gb one is also near full, and it's clogging down the works because its an older sata drive and the 2tb is a newer one with a faster speed.  

Here's my problem.  I have done all manner of tweaks to my system.  I don't remember most of them.  Now I suppose I could write down all the ppa's i have added, and gho thru programs and write down the names of all the programs I have added.  But I've done a lot of work editing files to make things work  that I don't remember.  For instance the other day I added a ppa, installed a driver and then added a module to my kernel.  I have no idea what the name of the driver was.  And so it goes.  Now I know that rsync and clonezilla can copy and sync your home folder.  But I need the whole drive copied over. 

I have a brand new caviar ready to replace it, but I really don't want to spend a day reinstalling things.  

So is there anyway I can clone the entire 40gb drive and put the contents on the 2 tb drive and have it work out the gate?

---

### Post by QDR06VV9 on 2016-03-05
Have A look here: [http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/?PageSpeed=noscript](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/?PageSpeed=noscript)
Just be-careful of the exact names for drives.
Happy Cloning..
Oh just a heads up for future planing..
> *Note: while you can copy a smaller drive to a larger one, you can&#8217;t  copy a larger drive to a smaller one with the method described.*

---

### Post by Evil Wayz on 2016-03-05
Thank you, I'll have to read through it a few times. It doesn't seem particularly complicated.  And I'll definitely backup my home folder just in case.

---

### Post by s0urCr34m on 2016-03-05
your problem's probably been solved but I just wanted to chime in here:  > For instance the other day I added a ppa, installed a driver and then added a module to my kernel. I have no idea what the name of the driver was.  I'd really be careful and understand the source and content of downloads, especially when you're adding 3rd party repos. What you described to me IMO sounds dangerous!

---

### Post by Evil Wayz on 2016-03-09
> **s0urCr34m said:**
> your problem's probably been solved but I just wanted to chime in here:    I'd really be careful and understand the source and content of downloads, especially when you're adding 3rd party repos. What you described to me IMO sounds dangerous!

I rarely do that.  I needed the driver for my wireless to work and I was not going to compile it everytime the kernel changed.  It was use a ppa or upgrade to 15.04 which supports ralink natively.  I could find the name of the driver if I really needed to by using lsusb.

---

### Post by oldfred on 2016-03-09
If you use dd to copy to larger drive, you just erase the first 40GB of that drive and may not be able to access anything as it will also erase partition table.

I believe in new installs. And you should have backups that let you restore to your working state quickly anyway.
You can backup installed ppa list, installed apps list, all of /home, any files you edit in /etc like fstab or grub and any other data. If a server type system you may need addition folders/files for web, databases etc that are in / (root).

Use dd or full image clone really only works from exact size drive to another same size drive or one that is larger with out any data. Then you can expand old 40GB to entire drive and restore backup data.

---

### Post by mastablasta on 2016-03-10
i used clonezilla to do this with windows XP: [http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

result = perfect.

---

### Post by howefield on 2016-03-10
I'll give another vote of confidence to Clonezilla, should do what you want perfectly. Its only downside for me is that it isn't trivial to mount the resulting image and extract/view files from it but that won't be a problem for what you want to do.

I'll also urge you to document what you do to your system as you go along, a simple text file with a few notes is all it needs :)

---

### Post by QDR06VV9 on 2016-03-10
Interesting.. have you guys had problems using the method in the link I posted in my first post?
I have used it twice with perfect results..But worth a mention I had to do a reboot to mount the cloned partitions..
Would like some feedback so i don't further recommend to others this method..
Or are your other suggestions just personal preferences?
Thanks and Kind Regards

---

### Post by QDR06VV9 on 2016-03-11
Ok this was as easy as falling out of bed..
I booted to a live usb installer for Xenial then went to the Menu>System Tools> Mate Terminal...click that.
In the Terminal I issued this "sudo fdisk -l" 
Which gave me the needed info for the next step.
I am going to clone a 500gig drive with Ubuntu trusty installed and also Arch Rolling...Both Disk's I am working with are both 500gigs each.
The fdisk -l shows me this
```
Disk /dev/sda: 465.8 GiB, 500106780160 bytes, 976771055 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0008e5ea

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 554589938 554587891 264.5G 83 Linux
/dev/sda2       964194302 976769023  12574722     6G  5 Extended
/dev/sda3       554592256 964191865 409599610 195.3G 83 Linux
/dev/sda5       964194304 976769023  12574720     6G 82 Linux swap / Solaris

Partition table entries are not in disk order.




Disk /dev/sdb: 465.8 GiB, 500106780160 bytes, 976771055 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf1a41731

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1  *         2048    524287    522240   255M 83 Linux
/dev/sdb2          524288 964536319 964012032 459.7G 83 Linux
/dev/sdb3       964536320 976771054  12234735   5.9G  f W95 Ext'd (LBA)
/dev/sdb5       964538368 976771054  12232687   5.9G 82 Linux swap / Solaris
```

Where sda is the source I want to clone.
Now sdb will be the target or where i want the cloned Partitions to go.
So in the Terminal I next issued
```
sudo dd if=/dev/sda of=dev/sdb
```

Now this process took a bit longer than I last remember probably due to fact that there was multiple partitions and OS'es this time.
And now posting from the cloned drive. Yes both systems boot as advertised.
Some Screen Shots posted also
So nothing to fear..
Hope this is helpful

---

### Post by goofprog on 2016-03-11
yes you can.
[URL="http://gparted.org/livecd.php"]http://gparted.org/livecd.php
[http://clonezilla.org/](http://clonezilla.org/)

[/URL]

---

### Post by RobGoss on 2016-03-11
I have to second Clonezilla it works like a charm and keeps everything just the way it was intended..

---

