---
title: "Clonezilla restore"
date: 2014-03-06
forum: General Help
---

### Post by i57chevy on 2014-03-06
I've been going through the different posts without much luck. I did a clonzilla image of my lubuntu partition and saved it on my usb external hdd. I reformatted and resized partition and the restore errors out. I tested the image before i wiped and resized the drive with no problems. I made the target partition larger. The error referenced something about the image being corrupt. I doubt it. I tried different options - such as checking grub, resize to fit. I know it is probably something simple. Help please. Just wanna put the image back.

Billy

---

### Post by Toz on 2014-03-06
Hello and welcome to the forums.

The exact wording of the error would be helpful. Also, from which partition were you cloning from?

I just recently cloned a secondary partition to a new computer using clonezilla. I came across 2 issues:

1. If cloning to a different partition, you need to follow some extra steps. See [http://drbl.org/faq/fine-print.php?path=./2_System/102_restore_image_to_different_partition.faq#102_restore_image_to_different_partition.faq]("http://drbl.org/faq/fine-print.php?path=./2_System/102_restore_image_to_different_partition.faq#102_restore_image_to_different_partition.faq")

2. I had to create my partitions manually before hand and select the option to not create the partitions during the restore to get it to work.

And I also had to manually reinstall grub - but I'm not sure if I selected the option to do so from within the restore or not.

---

### Post by i57chevy on 2014-03-06
Thank you for replying.  So, impatiently I reinstalled lubuntu, but I am still trying to send the clone image back to it.  I think that this would negate the grub part.  I will try to run clonezilla process again shortly and provide the exact error message and the partitions.

---

### Post by i57chevy on 2014-03-06
Partition info: image is on external usb hdd sdb1 283.2GB ntfs partition - target for lubuntu is internal hdd sda1 276.5GB ext4 partition.  The image itself is very small 2-4GB I believe

I wouldn't think the image name would make a difference.  ubuntu_12-img 2014-0306-1720_sda5.  When I cloned it the partition was sda5 - now sda1.

message "Failed to restore partition image file /home/partimag/ubuntu_12img/sda1* to /dev/sda1!  Maybe this image is corrupt or there is no /home/partimag/ubuntu_12-img/sda1*!  If you are restoring the image of partition to different partition, check the FAQ on Clonezilla website for how to make it.  Press 'Enter' to continue......."

Maybe I need to move image to sda1 or rename it.  When I tested the image before deleting target partition, It was in the same as now sdb5.

What do you think?

---

### Post by Mark Phelps on 2014-03-06
I don't believe there's an option to resize the partition as part of the restore.  I've had the best results when I used GParted to remove the partition I was going to replace before I ran Clonezilla.  Clonezilla then rewrites the saved image using the size of the partition at the time the image was made.  You can always use GParted after that to adjust partition sizes.

---

### Post by Toz on 2014-03-06
> **i57chevy said:**
> I wouldn't think the image name would make a difference.  ubuntu_12-img 2014-0306-1720_sda5.  When I cloned it the partition was sda5 - now sda1.

I had the same error message moving from partition to partition, and solved it by following the instructions in the link above. Have you tried those instructions?

---

### Post by i57chevy on 2014-03-06
The option that I was referring to was -r when you go through expert mode instead of beginner.  resize image to fit partition or something like that.

---

### Post by i57chevy on 2014-03-06
Got it guys.  After I changed the info from the link - How can I restore an image of a partition to different partition...

Thank you.  Any info on how to add solaris to lubuntu grub or should I post new thread?

---

### Post by Toz on 2014-03-06
> **i57chevy said:**
> 
Thank you.  Any info on how to add solaris to lubuntu grub or should I post new thread?
It would be best if you marked this thread as solved using the Thread Tools link above and then create a new thread for your new question.

---

