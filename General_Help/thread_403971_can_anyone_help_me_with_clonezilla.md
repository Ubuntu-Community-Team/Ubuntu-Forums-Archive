---
title: "can anyone help me with clonezilla??"
date: 2007-04-07
forum: General Help
---

### Post by billdotson on 2007-04-07
I downloaded the latest gparted + clonezilla LiveCD and burned the ISO to a CD-RW.
I went in and did everything it told me to do to get it started:  

```

sudo su -
mount -t auto /dev/sdb5 /home/partimag
ocs-sr -x

```

Then I told it to save the partition /dev/sda1 (my Windows partition using the default options).  It saved "successfully" and then I chose 0 to poweroff.  I booted back into the LiveCD and then did

```

sudo su -
mount -t auto /dev/sdb5 /home/partimag
ocs-sr -x

```

again and then instead of saying to save I told it to restore.  I also let it restore using the default options. 
It went through a bunch of lines of text and then said at the bottom Unknown format for /home/partimag/test_image/sda1.ntfs-img.aa!!!  Program terminated!

Then it went back to the #live at the terminal.

I retried saving and restoring 2 more times and it didn't work either time.  

Does anyone know what is going on?  I have tried partimage but I don't trust it w/ NTFS partitions and I have also tried device image (zsplit and unzsplit) but it won't even make an image at all.. of anything.

Am I grasping for straws in trying to find a reliable and free disk cloner for NTFS partitions?

This is very frustrating.. :mad:   

Thanks again.

---

