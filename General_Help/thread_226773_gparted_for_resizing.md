---
title: "gparted for resizing"
date: 2006-07-31
forum: General Help
---

### Post by mathon on 2006-07-31
hi,

I want to use gparted, to resize my root partition /dev/hda1. But when I mark the root partition and go under Partition, the menu point for resizing the partition is greyed and cannot be chosen. 

Do I make anything wrong?? :confused: 

matti

---

### Post by Irony on 2006-07-31
You can't resize an ext3 partition, you particularly can't resize it when you are mounted on it.

You could use a live CD and copy the partition's contents to another partition then resize the partition then copy the contents back.

---

### Post by mathon on 2006-07-31
Oh okay, please one more advice: how could a copy the contents of the gparted to another partition?? - hda5 would be available

matti

---

### Post by ahaslam on 2006-07-31
> **Irony said:**
> You can't resize an ext3 partition, you particularly can't resize it when you are mounted on it.

You could use a live CD and copy the partition's contents to another partition then resize the partition then copy the contents back.

With Gparted Live resizing of ext3 partitions is very simple. You don't need to copy the partitions contents, just set the desired size, it does the rest ;)

Tony.

PS. I have used Gparted Live several times, never have I lost my data and I'm always impressed with its simplicity.

---

### Post by ahaslam on 2006-07-31
> **mathon said:**
> Oh okay, please one more advice: how could a copy the contents of the gparted to another partition?? - hda5 would be available

matti

No Need.

Just download the Gparted Live CD iso, burn it & boot it. It's very simple to use, if you encounter problems just post back here.

Tony.

---

### Post by mathon on 2006-07-31
Really?? but how does that work? As I said when I mark mei ext3 root partition the menu point under Partition for resizing the partition is greyed and cannot be chosen....??

---

### Post by ahaslam on 2006-07-31
> **mathon said:**
> Really?? but how does that work? As I said when I mark mei ext3 root partition the menu point under Partition for resizing the partition is greyed and cannot be chosen....??

You need the **LIVE** version of Gparted which can be found here:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Tony.

---

### Post by mathon on 2006-07-31
Oh okay, should I then start my laptop with this live CD, or is it enough to start the CD when I am in my ubuntu system?

---

### Post by ahaslam on 2006-07-31
> **mathon said:**
> Oh okay, should I then start my laptop with this live CD, or is it enough to start the CD when I am in my ubuntu system?

Start your system with Gparted Live in your CD drive. You need to boot from it.

Tony.

---

### Post by Irony on 2006-08-01
I'd have to disagree because I've tried resizing ext3 partitions with GParted (live CD and repository version) and it won't do it on an ext3 partition with an operating system on it.

Also Google searches say that resizing ext3 isn't possible. You can delete the partition, resize it and then recreate the partition.

To copy your operating system from say hda3 to hda6, do (from a live CD);

[PHP]sudo mkfs.ext3 /dev/hda6[/PHP]

This formats hda6 as ext3 (it may already be formatted but it won't harm it doing it again).

Right click on your desktop and make folders called say hda6_Ubuntu and hda3_Ubuntu.

[PHP]sudo mount /dev/hda6 /home/username/Desktop/hda6_Ubuntu
sudo mount /dev/hda3 /home/username/Desktop/hda3_Ubuntu[/PHP]

This mounts the partitions in the newly created folders.

[PHP]sudo cp -ax /home/username/Desktop/hda3_Ubuntu/. /home/username/Desktop/hda6_Ubuntu/.[/PHP]

This copies the contents of hda3 to hda6 (note the dots).

You can test it out by adding an entry to your menu.lst (don't delete hda3 until you have tested hda6).

---

### Post by ahaslam on 2006-08-01
> **Irony said:**
> I'd have to disagree because I've tried resizing ext3 partitions with GParted (live CD and repository version) and it won't do it on an ext3 partition with an operating system on it.

Sorry mate, I've done it.
The live cd can & does resize ext3 partitions with an operating system (or anything else) installed on it.

From Gparted's site:
"The purpose of GParted is to allow the individual to take a hard disk and change the partition organization therein, while preserving the partition contents."

Also see the features:
[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php) - notice grow & shrink?


Tony.

---

### Post by phersotty on 2006-08-01
> **Anthony Haslam said:**
> Sorry mate, I've done it.


Tony.

I've also done it to resize a Suse partition to make room for Ubuntu.  Also I would recommend if you haven't already to put /home on its own partition.  That way if you do hose things up all your precious data will safe over on the /home partition.

Here is a detailed way of resizing it [http://ubuntuforums.org/showthread.php?t=105255]("http://ubuntuforums.org/showthread.php?t=105255")

---

