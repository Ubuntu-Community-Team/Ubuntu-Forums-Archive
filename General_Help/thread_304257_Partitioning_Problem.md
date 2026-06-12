---
title: "Partitioning Problem"
date: 2006-11-21
forum: General Help
---

### Post by jasper182 on 2006-11-21
I've been runing Ubuntu for about 5 months now and I really like it, but some work I need to do requires me to use WinXP now as well.  So, I was going to dual boot my laptop.  Thing is, I need a partition to install XP on, and I don't want to remove my current setup of Ubuntu.  Is there a way to simply split my current partition into two?  I've looked around some but have been unable to find anything on this subject.  Thanks.

---

### Post by jasper182 on 2006-11-21
I've been runing Ubuntu for about 5 months now and I really like it, but some work I need to do requires me to use WinXP now as well.  So, I was going to dual boot my laptop.  Thing is, I need a partition to install XP on, and I don't want to remove my current setup of Ubuntu.  Is there a way to simply split my current partition into two?  I've looked around some but have been unable to find anything on this subject.  Thanks.

---

### Post by Nameless_one on 2006-11-21
With gparted, which is in the standard ubuntu installation (although an old version - it would be better to use the gparted live cd which you can get from [here]("http://gparted.sourceforge.net/livecd.php")), you can resize a partition into a smaller one, and create a new partition in the empty space.

---

### Post by Spin Doctor on 2006-11-21
If you have your ubuntu installed on an EXT 3 filesystem, you might run into trouble...

When I tried to resize my Ubuntu partion formated with EXT3 filesystem, I realized that many partioners will not allow you to resize an EXT3 Partion. I wanted to reduce my windows partion, and increase my ubuntu partion.

The easy solution I found was to use the partioner from the alternative install CD with the rescue mode (in my case ubuntu 6.1 alt install cd) That will let you resize your EXT3 filesystem. And also create a FAT 32 partion. I am not sure if it will let you create a NTFS partion. Just make sure you have the mountpoint of your ubuntu partition set to: / 

Another great live cd is the system rescue cd:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Make sure you backup your data properly before doing anything with your partions.

---

### Post by K.Mandla on 2006-11-21
(Moved to General Help. :) Merged with identical thread. ;) )

You could try a live CD of GPartEd, resize the Ubuntu partition and install Windows on that. You'll probably have to restore Grub after you do that, since XP will brazenly overwrite the MBR. But so long as you don't tamper with the Ubuntu partition, it'll work out just fine.

---

