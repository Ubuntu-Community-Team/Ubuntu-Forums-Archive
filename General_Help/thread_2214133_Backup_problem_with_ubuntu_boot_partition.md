---
title: "Backup problem with ubuntu boot partition"
date: 2014-03-30
forum: General Help
---

### Post by Angela_C.Murphy on 2014-03-30
I am using Ubuntu 12.04 LTS (Precise) and I have not had backup problems before now.  I usually boot from a Clonezilla Live CD and image the part of my drive devoted to Linux, then store it on an external drive.  I am currently using the Clonezilla Alternate Live 20140114 (saucy) version.  The disk imaging started out fine with a couple of Xandros partitions and an old Ubuntu partition imaged, but when it got to "sdb3", my 41 Gb current Ubuntu boot partition, there was a big problem.  It started the bitmap, but when it got to about 98%, it quit with a message something like "5,000,000 free".  It was over 5,000,000, but I don't recall the exact number.  It would not image the boot partition by itself either.

I don't know what all this means.  I have used Ubuntu for a number of years, but outside of some fairly simple things, I am pretty much a newbie.  I am not comfortable with a terminal and prefer using a GUI.  I checked the partition with GParted, and it doesn't seem to see anything glaringly wrong with it. sdb3's mount point is /, and it is flagged as boot.  21.21 Gb are used and 19.80 Gb are unused.  The first sector is 438285330 and the last is 524297339.  Total sectors = 86012010.

I thought about having Clonezilla use fsck before imaging, but this is my boot partition, so I'm a bit afraid of doing it.  I tried using System Rescue CD, but I was not knowledgeable enough to use it well.  Partimage gave me the same result as Clonezilla.

As a last resort, I used the Ubuntu Backup application to save most of the files in the partition to a 32 Gb flash drive.  That is an OK work-around, but I would really prefer to have a whole partition image or whole disk image for restoration purposes (should that ever become necessary)

I would be most grateful for any help the forum community can give me.
Angela C. Murphy

---

### Post by oldfred on 2014-03-31
Boot flag is not used by grub. It just is which version of grub you have in hard drive's MBR will determine which system you boot. And with two drives you have two MBRs so could set each MBR with different systems. Then with BIOS or a one time boot key choose to boot a different system if you have issues with default boot device.

We still suggest a boot flag on a primary partition only because some BIOS have to see a boot flag ot even let grub start to boot. Those seem to be designed more for Windows as Windows does have to have a boot flag on a primary partition.

I would suggest running fsck from live installer.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb3 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb3
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb3

---

