---
title: "Logical Volume resizing issues after migrating to SSD"
date: 2014-09-02
forum: General Help
---

### Post by Gridwalker on 2014-09-02
I have recently been upgrading a machine that I built out of recycled/reclaimed/reused parts and have managed to lay my hands on an SSD. As it would provide a major speed boost over the ancient IDE drive that I was using for my root disk, I installed it and used Clonezilla to transfer my existing OS over to the new drive.

I know that many of you reading this will be wondering why I didn't do a completely clean install, but this is a box that I use for experimentation and it would take a very long time to reconfigure a fresh install in the way that I want.

The original drive was 80gb and the new drive is 120gb, so I started making adjustments to the partition sizes; I increased the boot partition slightly and increased the extended partition hosting the logical volume so that it took up the remaining space. When I checked in GParted, although the size of ubuntu-vg had increased to 111gb, it was saying only 74gb was being used (the size of the original partition on the 80gb IDE drive).

I don't know the terminal commands for volume group management, so I used the LVM GUI tool to increase the size of the volume (GParted is now reporting that the whole partition is used). There is a swap partition contained within ubuntu-vg, so increasing the root partition to use the remaining free space has sandwiched the swap file like this :

[IMG]http://i.imgur.com/FSaegXm.png[/IMG]

According to the information provided by GParted and the LVM GUI, I should have successfully extended my root partition to use all of the free space on the drive ... only other applications don't agree.

I have a Conky system monitor on my desktop that displays space on all of my drives, which is currently displaying the same stats as it did for my 80gb root drive. Additionally, right clicking on "Computer" in the nautilus side bar and selecting "Properties" then reports the same stats as Conky, so something clearly isn't right here.

Any advice will be appreciated, as I am a bit stumped by all of this. Also, please give advice in a step by step format, as this is the first time I've had to edit logical volumes and I'm not even sure how to gather the right information through the terminal ... so, be gentle ;)

Thanks in advance!

---

### Post by grahammechanical on 2014-09-02
I am speaking in ignorance but I ask about this:

> [COLOR=#000000]I have a Conky system monitor on my desktop that displays space on all of my drives, which is currently displaying the same stats as it did for my 80gb root drive. Additionally, right clicking on "Computer" in the nautilus side bar and selecting "Properties" then reports the same stats as Conky, so something clearly isn't right here.[/COLOR]

is it something what we get when we clone a drive?  Have fun with your experiment.

---

### Post by Gridwalker on 2014-09-02
The original drive has now been formatted and installed in another machine, so the system can't be inadvertently reporting the stats from the original disk.

I know that my Conky skin simply reports data gathered from the OS related to specific mount points (for the root partition, it simply looks at "/"), so it shouldn't be reporting information from before the cloning process. I have tested this by editing the configuration file to look at different disks, which were reported accurately every time; it just fails to see the extended space on the root partition ... I don't know about how Nautilus gathers drive information, but I would presume something similar.

I am wondering if it has something to do with the swap partition somehow preventing the system from seeing the extended section of root, which appears after the swap partition on the disk. Could that somehow be blocking the OS from reading that section of the disk?

---

### Post by Gridwalker on 2014-09-04
*bump*

I am still looking for suggestions on how I may get the OS to see the full extent of the extended root partition. Any thoughts will be appreciated!

---

### Post by Gridwalker on 2014-09-04
I just booted using a 14.04 live cd and tried using growfs, but the terminal reported that the command was not found. How might I go about making this available?

---

