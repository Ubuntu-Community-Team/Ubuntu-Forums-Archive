---
title: "Partition hard drive so I can clone OS with clonzilla."
date: 2016-07-24
forum: General Help
---

### Post by Tom_Carr on 2016-07-24
I don't know anything about this but I want to learn.
First I need to learn about partitioning the hard drive.

Can you partition the hard drive when you already have ubuntu installed, or do you need to do that during the install?
Either way, can someone please either give me a link to instructions, or give me basic instructions here.  I have been googleing and haven't found anything that makes clear how to do this.

---

### Post by yancek on 2016-07-24
You cannot change a mounted partition so if for example, the partition on which you have Ubuntu takes up the entire disk, you cannot change it.  Generally the recommendation is to use a DVD or flash drive with Ubuntu Live CD on it as it contains the partition manager GParted.  Booting from that, you should be able to make any changes you want.  The link below is to the online GParted Manual which has a Table of Contents so you can go to the applicable section for what you want to do.

[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

So the answer to your question is yes and no.  You can not modify the partition to which you are booting, the partition with the Ubuntu (or other Linux) root filesystem.  You can modify partitions other than the partition on which the root of the filesystem exists.

---

### Post by grahammechanical on 2016-07-24
Working with partitions is less complicated if we have a UEFI boot system for that means that we have a GPT partition scheme.

If GParted is showing a key icon against a partition then the partition cannot be moved or resized because it is mounted. The Ubuntu live session will always make use of the swap partition. To do anything with the swap partition we need to use the GParted menu system to take "swap off."

If the motherboard has a BIOS boot system then we might have MBR partitioning. We can have GPT partitioning with BIOS boot systems because GPT is backwards compatible with BIOS boot systems but we will need to know about primary, extended and logical partitions.

With MBR partitioning it might be the case that the swap partition is inside the extended partition. With "swap on" the extended partition and any partitions inside the extended partition will be locked with the key icon showing. Taking "swap off" will make it possible to work with all the partitions.

Regards.

---

### Post by howefield on 2016-07-25
> **Tom_Carr said:**
> Partition hard drive so I can clone OS with clonzilla. 

Are you asking about partitioning in order to create another partition in which to store Clonezilla images ?

If so, yes, you can by using an Ubuntu Live media as mentioned already but it might be worth mentioning that you can also store your image on a separate disk, whether that be an external hard drive, USB flash stick, network drive or whatever, even a rewritable CD/DVD.

---

### Post by Tom_Carr on 2016-07-25
> [COLOR=#000000]Are you asking about partitioning in order to create another partition in which to store Clonezilla images ?[/COLOR]

Yes

> [COLOR=#000000]If so, yes, you can by using an Ubuntu Live media as mentioned already but it might be worth mentioning that you can also store your image on a separate disk, whether that be an external hard drive, USB flash stick, network drive or whatever, even a rewritable CD/DVD.[/COLOR]

That sounds better to me.  I have an external usb drive that I would like to back up the image on.  However there is a problem using that drive, which I will describe in the next post.

I have a usb external hard drive that I installed a different version of linux on several years ago.  I have two ubuntu boxes here, a Dell and an Acer.  On the Dell, I pluged in the exrernal drive and it booted up the old linux version just fine.  On the Acer box, I pluged it in and it ignored it and booted from the internal hard drive.  I unplugged the internal hard drive, booted, and got a message "error: no such partition, grub resuce".  

I can see the external drive on the Acer after I boot up from the internal drive.  I can copy and paste into it, so the Acer sees it but just can't boot from it.

2 questions:

1 - Why can't the acer boot from the external drive
2 - Is there any problem doing a clone of the ubuntu on the internal hard drive in the acer and backing it up on the external drive?

---

### Post by howefield on 2016-07-25
> **Tom_Carr said:**
> Why can't the acer boot from the external drive

Sounds like the stuff of another thread.

> Is there any problem doing a clone of the ubuntu on the internal hard drive in the acer and backing it up on the external drive?

Are you intending on keeping whatever is installed on the external drive ?

---

### Post by yancek on 2016-07-25
Did you boot the unidentified Linux distribution on the Dell from the Grub menu on Ubuntu or did you select it by changing the boot priority in the BIOS to set the external drive to first boot priority?  Same for the Acer?  Is the Acer a Desktop, laptop or notebook?  Is the external attached via usb port?  Have you tried different usb ports if that's the case?

---

### Post by Tom_Carr on 2016-07-25
The external HD has Mint 13, Cinammon, 32-bit.
If you want me to replace that with Ubuntu I will.  At this point I am just using it for cloning the ubuntu systems.  I don't care about anything on it now.
On both the Dell and the Acer the bios was already set to look for something in the usb port as first boot priority.
When I started the Dell with the external hd pluged in it brought up a grub menu with Mint at the top and then loaded mint without my selecting it.
When I started the Dell without the external hd it went directly to ubuntu with a grub menu.


On the Acer, I pluged it in and it ignored it and booted from the internal hard drive. I unplugged the internal hard drive, booted, and got a message "error: no such partition, grub resuce". 


Both computers are desktop
All external hd connections are with usb port
I tried 3 usb ports on the Acer that I know work with other things and all had the same problem with the external hd.

---

### Post by yancek on 2016-07-25
On some laptops and certainly on the smaller notebooks, there are multiple usb ports but not all of them will boot.  I have an Acer Aspire D250 noteboot which has two usb ports on the right side but will only boot when a bootable flash is placed in the first/front usb port.  If you had the Acer set to boot from the flash drive, I can't think of any other reason it would not boot if it worked on another machine.  Good luck with it.

---

### Post by Tom_Carr on 2016-07-25
Thanks yancek.  I will try all the usb ports.  It has 8.

I tried all the usb ports and it didn't work.  I did a fresh install of ubuntu 16.04 and it didn't work.  I will open another topic on my problems with booting from an external HD.  

I want to get back to my original question about cloning.   The reason I want to learn to clone is so I can back up my whole system so if I mess something up while experimenting with it, I can quickly restore it.  

Questions:
1 - Is cloning or imaging what I should use to back up my system in case I mess it up while experimenting?
2 - Can I clone several versions of my system to several different partitions on the external HD?

---

### Post by Geoffrey_Arndt on 2016-07-26
Cloning is not generally the optimal way to back up and restore a system that the user has fubar'd.

A better way is the combo of running weekly backups via a quality app such as "Back in Time" and having/using a reliable rescue live OS such as "Parted Magic".

The back up program restores your data, which is usually the most important thing on the pc, and
the live OS can fix the installed OS.

---

