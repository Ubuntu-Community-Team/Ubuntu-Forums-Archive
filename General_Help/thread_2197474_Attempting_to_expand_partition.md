---
title: "Attempting to expand partition"
date: 2014-01-03
forum: General Help
---

### Post by cosmoflop12 on 2014-01-03
Hello, I am trying to expand my Ubuntu partition on a mid-2009 MacBook pro running Ubuntu 13.04. Unfortunately, the bios_grub partition cannot be moved. It can The linux-swap one can be moved, but seeing as it is squeezed to the right side almost entirely, as you can see in the image, moving it over and expanding my main partition only gives me about 1 more gb. How can I give myself more space? This picture was taken from within the partition, so the partitions are locked. I do have access to LiveCD if that needs to be used, however. If any more information is needed to solve this problem, just say so. Thanks in advance.

---

### Post by jamesisin on 2014-01-03
What's that unknown partition?

The trouble you face is interesting.  The problem is that moving the front edge of a partition is where you get your real troubles.  Moving the trailing edge of the partition is much easier.  Once you move that leading edge you'll have to run something like boot-repair so your partition tables are correctly pointed.  You can load that onto your LiveCD easily enough.

Moving your sheet however...

If you can determine what that unknown partition is and it's trashable, you can try sliding your main partition to the left (and then run boot-repair).

Though it might be more to your benefit to shrink your HFS partition, create a shared partition between them, and move all your files from both OS's into that middle partition.

---

### Post by monkeybrain20122 on 2014-01-04
If I understand correctly you want to expand sda5 somehow. As jamesisin said expanding the partition to the left can be tricky. So I would instead do this:
get fsarchiver [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)
You can install it and run it off a ubuntu live usb (or systemRescueCD [http://www.sysresccd.org/System-tools](http://www.sysresccd.org/System-tools)) It is in the repo.


Boot to the live usb, install fsarchiver and clone your /dev/sda5, save the fsa file somewhere (an external drive will be handy), then use gparted to delete everything after /dev/sda2 and reformat, recreate a new, big ext4 partition plus swap. Then restore your clone to the new partition. It would be a lot faster and safer than expanding or sliding your existing sda5.

p.s. You need the live usb basically for 1) using gparted to reformat the space after sda2 and 2) to restore the clone. 
For making the clone you can actually do it in /dev/sda5 with Ubuntu running(of course need to install fsarchiver first) The options -a and -A let you clone a mounted, running Linux partition (sudo fsarchiver -a -A -v -other options for compression, exclusion etc  savefs /path to directory where image is saved/filename.fsa  /dev/sda5)

---

### Post by jamesisin on 2014-01-04
monkeybrain20122 makes good points too.

---

### Post by Bucky Ball on 2014-01-04
Please attach large images using 'Go Advanced' and the paper clip icon. Thanks.

I have done this one for you.

---

### Post by cosmoflop12 on 2014-01-04
Jamesisin, I'm pretty sure the unknown partition is the bios_grub, which I don't think is something I can delete. I'm not sure however, so if someone could clarify whether or not it is safe to delete that would be great. And, because, like you said, moving the front part of the partition is dangerous, my plan was to move the partition to the left, then expand to the right. Monkeybrain, I might look into the fsa option if an easier one does not present itself.

---

### Post by vanadium on 2014-01-04
The following link provides information as to the "why". Perhaps, the links provided might help you to find the "how". It does not appear very trivial: [http://superuser.com/questions/378611/repartitioning-dual-booting-macbook](http://superuser.com/questions/378611/repartitioning-dual-booting-macbook)

The more practical workaround may indeed to maximize the use of your disk space by creating an additional data partition on the unallocated chunk after sd2. The suggestion of  jamesisin to shrink sd2 so you can maximize the new partition for shared data storage between toe operating systems is a very good one.

Your linux swap partition currently is very small. I wonder if you could expand it to cover the unallocated space at the end of the drive.

interesting note here: [http://gparted.org/faq.php#faq-21](http://gparted.org/faq.php#faq-21)

---

### Post by jamesisin on 2014-01-05
Grub does not live in a partition, as I understand it.  Someone else might like to comment on that.  Regardless it does not require its own partition (if it's in any partition it's with Ubuntu).

Moving your partition to the left is no different from moving the front edge of the partition to the left, as far as what I was saying is concerned.  If you move the starting point of a partition, you have to repair the partition table (which lives at the front of the drive?) so that when any boot loader (probably EFI then Grub in your case) goes looking for the partitions, the partition table has the correct information.

IF you should choose to move the front of your Ubu partition (either by moving the partition in either direction or by expanding the partition to the left) you will need to use boot-repair to correct the partition table.

Again, I'd probably prefer to move my data to a shared partition in the middle of Mac and Ubu.

---

### Post by Mark Phelps on 2014-01-05
> Grub does not live in a partition, as I understand it. Someone else might like to comment on that. 

Actually, YES it does.  There are two parts to GRUB.  One is installed in the MBR, the other in a Linux filesystem partition -- in two different paths.

People discover this the hard way when they have dual booted systems (Windows and Linux), remove the Linux partition(s) and then discover they can't boot anymore because the GRUB code in the MBR continues to point to a nonexistant partition.

---

### Post by vanadium on 2014-01-05
On MBR disks, the second stage would usually be installed in unused sectors after the MBR, not necesarilly on a separate partition. This here concerns a GTP disk. On such disk, the second stage can only exist on a separate bios boot partition. I guess that such partition could be deleted, but as a result, the bootloader would need to be reinstalled to make the system bootable again. See [here](https://help.ubuntu.com/community/Grub2/Installing) under BIOS/GPT Notes. It seems you should be able to create a bios_grub partition where you want, which will then be used by the grub installer.

But again, depending on the technical skills (and interest) of the OP, it may be better to be pragmatical and just create a data partition in the free space.

---

### Post by jamesisin on 2014-01-05
Thanks, Mark Phelps and vanadium, for the clarification.  All of those troubles can be repaired after the fact using *boot-repair* (which can also re-install GRUB if needed).  Nonetheless, I still prefer the idea of creating a shared data partition in the middle.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

(You would likely want to use the second option and add the repository to your LiveCD and install *boot-repair* there.  On dual-boot systems I also install boot-repair into the Ubuntu installation as it will be needed when distribution upgrades are made.)

---

### Post by cosmoflop12 on 2014-01-06
At this point, due to the complications that could arise in doing anything with the partitions, I think I am going to play it safe and just copy all my stuff to an external drive, and copy it to a new, larger install of Ubuntu. Thank you everyone for the help (and sorry for this late reply).

---

### Post by jamesisin on 2014-01-07
There is both *rsync* and *dd* as formidable copy tools which might help in your current quest.

---

