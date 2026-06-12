---
title: "problem with cloning a hard drive"
date: 2007-12-12
forum: General Help
---

### Post by sam2049 on 2007-12-12
My main boot drive is hda which is 80GB running Gutsy. My storage drive is hdb 160GB with Fiesty installed. I got a new drive sda 500GB. I wanted to clone my hda to my sda and use it for booting. i used the command :

sudo dd if=/dev/hda1 of=/dev/sda1

It seemed to work ok and after a bit of playing with grub it boots just like the original. The problem is it only has 20GB free space just like the original when it is a new 500GB hard drive. How can i reclaim the space, or do i need to do something different to make a bootable clone with gobs of free space?
I want my boot hard drive to have 440GB free space if you see what i mean, not 20.

---

### Post by kpkeerthi on 2007-12-12
If you are using dd, you need to make sure that the destination disk is identical to the source disk (including model and geometry). This is because dd performs byte-by-byte copy to the target. So, if a 10 GB X drive was dd'd to a 40 GB Y drive, then the 40 GB drive would show up as a X 10 GB and there is no easy way to reclaim the missing space. For more information see [this]("http://www.inference.phy.cam.ac.uk/saw27/notes/backup-hard-disk-partitions.html"), specifically the sub-heading **Reducing the storage space required**

You could rather use partimage (See [System Rescue Disk]("http://www.sysresccd.org/")). After imaging and restoring the image with partimage, use gparted to allocate the free space.

Here is what I did a while ago to restore my linux setup to a new HDD:
1. Backed up my partitions (root & home) as tar file. I backup periodically.
2. Partitioned my new drive (root, home and swap).
3. Using Live CD, extracted the tar to corresponding partitions in the new drive.
4. Edited fstab to point to the new partitions.
5. Installed GRUB to MBR.

---

### Post by sam2049 on 2007-12-12
Thanks for the info, that is what I was afraid of. My hdb 160GB is full up. i think if i back up my 80 onto my 500 with tar then i would not be able to restore it on the 500 and have it boot like my 80 and still have all the free space? I have several applications that save to my hdb is why i didnt want to make my sda my new data storage disk. It looks to me like that is the easiest thing to do, copy all files from hdb to sda (not with dd) then change my progs to save to sda.

---

### Post by kpkeerthi on 2007-12-12
If you are not used to keep TARs of your files, no worry. You can still copy files from the old disk to the new disk.

Is your 80 GB drive still good and bootable? If it is, I suggest you erase, partition and format your 500 GB disk and copy filesystem from the old to new disk partition by partition as explained [here]("http://www.brandonhutchinson.com/Moving_Linux_to_a_new_hard_disk.html").

---

### Post by sam2049 on 2007-12-13
thanks again for the help. to make it clear what i want to do is replace my 80 with my 500 and have it boot and act exactly the same and disuse the 80 keeping it as a backup. copying the disk partion by partion would leave me with the free space in a different place from my boot drive. i did get an idea from you though. 
I did a fresh install on my 500 of ubuntu 7.10 so as to make the partions like i wanted. then i tared the contents of my 80 to my 500 thinking that if i replaced all the files different with the ones i was using it would be the same and i would have all the free space available on the booting drive.
I figured out several things not to do with tar. dont tar the tar you writing to, dont forget to exclude /mnt and /media, dont tar active files that are being changed as they are tared, dont extract in any of the same way.
I had to boot off of my 160 drive with ubuntu 7.04 to do the taring. tar intricacies are another thread, I did what i set out to however......     when i booted from the 500 i could not log in as my name or password was wrong. I use the same name and password for all of my drives. so i still am not set up like i want.

---

