---
title: "Help with growing Linux Partition on dual boot machine, please!"
date: 2015-08-03
forum: General Help
---

### Post by jsheradin on 2015-08-03
I have my MacBook Pro dual booting OS X Yosemite and Ubuntu 14.04 with Gnome. I've since shrunk the OS X partition to increase the size of my Linux partition but I am having trouble growing it. This is what Gparted currently looks like for my SSD:

[IMG]https://i.imgur.com/fTplvJY.png[/IMG]
 
When I right click on /dev/sda4, I am not given the option to grow the partition into the adjacent free space:

[IMG]https://i.imgur.com/o7OvAoO.png[/IMG]


What is the reason for this? Is there any way of growing the partition short of a re-install? This laptop has a 1TB HDD in it; I could use that for moving stuff around if needed.


Thanks in advance for any and all help!

---

### Post by prshah on 2015-08-03
Hi,

It looks as though the root partition (sda4) is mounted. If you have booted into your linux install, you cannot resize it while it is active. 

You need to boot off a live-cd, ensure that /dev/sda4 is unmounted (no "key" symbol), and then you can resize/move the partition.

This is a tricky operation, make sure that you backup your stuff before attempting this!

Cheers,

---

### Post by yancek on 2015-08-03
The key icon in the GParted output to the right of /dev/sda4 and you can't modify a mounted partition as explained above with the solution.  Since this is also your root filesystem and contains the boot files which will have to be also moved to the left, you may run into problems booting after you move the partition and its data.  Never used a Mac so haven't got a clue how to deal with that.

---

### Post by jsheradin on 2015-08-03
I made a bootable USB, imaged my SSD (just in case), and resized from there; it worked perfectly. Thanks!

---

