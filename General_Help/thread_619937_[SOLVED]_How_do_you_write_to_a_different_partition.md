---
title: "[SOLVED] How do you write to a different partition? (Physical and/or virtual)"
date: 2007-11-22
forum: General Help
---

### Post by mahasmb on 2007-11-22
My computer makes a backup that's several gigabytes big every week. Yet since it's a backup, I want it to be saved onto my nearly empty 40 GB HDD instead of filling up the HDD that I'm using for Ubuntu (plus it's safer that way incase I mess up my Ubuntu in any way in the future). Even if I open up Nautilus as root, I still can't write to a different physical partition, or to my different virtual partition that has Windows on it.

So the only way I've been able to do this thus far is boot into Windows. I'd like it if I didn't have to boot into Windows *_just_* to transfer some files though.

Is there any way I can achieve this?

---

### Post by mpierce on 2007-11-22
You have to mount the partition so you can access and write to it if it is not already mounted. Was the partition formated for use under linux or, is it a WIN partition. In order to help you, we need additional information. 

This will show you all the partitions on your current hd:
   cat /proc/partitions

Now which partition do you want to write to? Repost and someone will tell you how to mount it or create an entry so that it auto mounts with correct permissions. 

Hope this helps...

---

### Post by u-slayer on 2007-11-22
You have to mount your partitions before writing.

List your partitions with fdisk -l

Then mount them. For example if I want to mount /dev/sda2 I would type mount /dev/sda2 /mnt

Then I would navigate nautilus to the /mnt folder.

---

### Post by mahasmb on 2007-11-28
Thank you very much. That worked for me.

---

