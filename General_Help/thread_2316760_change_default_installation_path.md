---
title: "change default installation path"
date: 2016-03-10
forum: General Help
---

### Post by amine_othmane on 2016-03-10
Hi,

I have a Dell inspiron 17R Special edition with two hard discs: 32Gb SSD disc an a 1Tb normal disc. I have installed ubuntu on the SSD disc. However I habe several programms that need a lot of space (Matlab, Maple...). I don't have anymore enought space on this hard disc. Is there any possibility to change the default installation path of Ubuntu to be able to install programs on the second disc?

Thanks in advance for your answer.

Amine

---

### Post by Dennis N on 2016-03-10
I have a solution, but it requires backing up your data and reinstallation of the OS and software. The solution requires use of LVM (Logical Volume Management), and installing Ubuntu's root file system within a logical volume which can then be extended over your two disks. You can allocate as much of the 2nd disk as you need, and add more space even after installation of the OS.

Too big a topic to explain here. There are how-to articles on the internet.

If you are interested, here is a how-to I have used specific to Ubuntu. It will help you to get the general idea:

[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

### Post by amine_othmane on 2016-03-11
Thanks a lot for your answer! It seems to be time consuming. I will try to do it in a couple of weeks when I have more time.

---

### Post by Dennis N on 2016-03-11
Besides using LVM, there are other ideas that could be explored:

Another option would be to create a dual boot system and install a second OS (another Ubuntu would be fine) onto the 1tB disk and install and use the disk-space-hungry programs on that OS instead. Could be a good solution if these programs use  a .deb file, install from a repository with apt, or have their own install script; all of which specify where the program files have to be within the root file system.   

Some ready-to-run programs (binary blobs) don't have an installer, so for those, you could locate them (often just a single file) in a place of your choosing, like your home folder for example, or create and mount a partition on your 2nd drive to place them there.

Just the working directory of a program for data might be located on the other drive. The program may have an option to specify that. 

That's all that comes to mind now. Others on the forum may have a suggestion. I do like LVM, though. I see lots of advantages with that, especially the ease of expanding disk space.

---

### Post by btindie on 2016-03-11
You don't need to go to the trouble of dual-booting or reinstalling the OS.

I'm not familiar with the programs you mentioned but you just need to find out where they install to or save all the data to.

If you've got the *.deb files you can use the 'dpkg-deb -c <deb_filename>' command to see where it puts the files, the big ones at least.

Assuming your SSD appears as /dev/sda and your mechanical disk as /dev/sdb, you just need to create a new partition on /dev/sdb1 and mount that on the directory where all the files will be installed to.

If you've already got stuff where it want's to install to, then you just need to do the following to move it all to the new partition.
1) create a temporary mount point
2) mount the new partition on there
3) move all the files there
4) umount that
5) edit /etc/fstab and add an entry for your additional partition

Say you've got a partition mounted on /home already, there's no reason why you couldn't have another partition mounted on /home/amine/Documents. All that would need to be done is make sure it's listed in the correct order in /etc/fstab

If you're not using LVM already then you may want to consider creating a Volume Group on your mechanical disk and that way you can slice it up easier if you need multiple partitions and you can also resize them a lot easier in future if needed.

If you've got a lot of stuff on your SSD that needn't be there you can use the same method as above to move it to your mechanical disk thereby freeing up more space on the SSD.

---

### Post by amine_othmane on 2016-03-19
THanks a lot for your answer!! I will go through them in details :)

---

### Post by mcduck on 2016-03-19
> **btindie said:**
> You don't need to go to the trouble of dual-booting or reinstalling the OS.

I'm not familiar with the programs you mentioned but you just need to find out where they install to or save all the data to.

If you've got the *.deb files you can use the 'dpkg-deb -c <deb_filename>' command to see where it puts the files, the big ones at least.

Assuming your SSD appears as /dev/sda and your mechanical disk as /dev/sdb, you just need to create a new partition on /dev/sdb1 and mount that on the directory where all the files will be installed to.

If you've already got stuff where it want's to install to, then you just need to do the following to move it all to the new partition.
1) create a temporary mount point
2) mount the new partition on there
3) move all the files there
4) umount that
5) edit /etc/fstab and add an entry for your additional partition

Say you've got a partition mounted on /home already, there's no reason why you couldn't have another partition mounted on /home/amine/Documents. All that would need to be done is make sure it's listed in the correct order in /etc/fstab

If you're not using LVM already then you may want to consider creating a Volume Group on your mechanical disk and that way you can slice it up easier if you need multiple partitions and you can also resize them a lot easier in future if needed.

If you've got a lot of stuff on your SSD that needn't be there you can use the same method as above to move it to your mechanical disk thereby freeing up more space on the SSD.
This is the best way to do it, assuming you really need the program files on the additional drive (rather than moving your home directory there, for example).

However, one thing to keep in mind: If you mount the new partition over the current directory, all the files that right now exist in that directory will still remain in that drive, using space, even though they aren't visible or accessible since they are hidden by the new partition.

So, if you want to free some space on your SSD at the same time, you'll have to boot with live-USB or something (so the directory isn't in use, and the new drive isn't mounted), and empty that directory.

---

