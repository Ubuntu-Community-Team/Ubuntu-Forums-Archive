---
title: "Clear Flash drive"
date: 2014-11-24
forum: General Help
---

### Post by Camilia on 2014-11-24
I have ubuntu 12.04. I want to clear all info off of a flash drive. Is there a program that will do that?

Tried commands from [here]("http://askubuntu.com/questions/185815/how-do-i-clear-everything-data-viruses-from-a-thumbdrive") with no results. Uncertain if I put the flashdrive name in the right place, though.

---

### Post by pfeiffep on 2014-11-24
[Gparted]("https://help.ubuntu.com/community/GParted") should provide the capability to clear the flash drive. Look for the section on gparted package

---

### Post by Camilia on 2014-11-24
> **pfeiffep said:**
> [Gparted]("https://help.ubuntu.com/community/GParted") should provide the capability to clear the flash drive. Look for the section on gparted package
I dowloaded GParted Partition Editor in Ubuntu software center. Uncertain what to do with it. It has /dev/sda1 ext 4 593.42 GiB and /dev/sda2 extended 2.75 GiB and /dev/sda5 linux-swap 2.57Gib. I don't know what these are. Flashdrive has 4 GiBs

---

### Post by pfeiffep on 2014-11-24
I suggest using this command
 ```
sudo apt-get install gparted
```

---

### Post by Camilia on 2014-11-24
> **pfeiffep said:**
> I suggest using this command
 ```
sudo apt-get install gparted
```
All that does is tell me that I have the latest gparted.

I found this command sudo fdisk /dev/sdx but uncertain what the flashdrive file is. 

where /dev/sdx should be replaced with the device file for your flash drive

What about Disk utility?
In Disk Utility have option Erase of partition the drive. Clicking on this get these options:
Mater Boot Record
GUID Partition Table
Don't partition
Apple partition map

---

### Post by westie457 on 2014-11-24
Look at the top right corner of the attached pic.

As long as you have an USB stick plugged in you should be able to get a similar view in Gparted.

---

### Post by Camilia on 2014-11-24
I got
/dev/sda1 ext 4 593.42 GiB 
/dev/sda2 extended 2.75 GiB 
/dev/sda5 linux-swap 2.57Gib
I don't know what these are.
Flashdrive only has 4Gib

---

### Post by yancek on 2014-11-24
sda1 is the partition with your Linux system, sda2 is an Extended partition which contains the swap partition, sda5.  Look at the image posted by westie457, particularly the highlighted part in the upper right.  If you have the flash drive plugged in you should see a down arrow, click that and select sdb.  Highlight the partition you want to clear by clicking on it in the main window, go up to the Partition tab and make sure it is not mounted then select Format to whatever filesystem you want or delete it.  A very detailed tutorial on using GParted is at the link below. 

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Camilia on 2014-11-24
> **yancek said:**
> 
select sdb.  Highlight the partition you want to clear by clicking on it in the main window, go up to the Partition tab and make sure it is not mounted then select Format to whatever filesystem you want or delete it.  A very detailed tutorial on using GParted is at the link below. 

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
So in Gparted first I unmount it in - delete format - click Check mark for apply.  Clicked format, apply. Now it is clear. 

Now flashdrive is useless. Read the info on link. Tried to save a document to the flashdrive and got. 
Error saving /media/2bde8978-67c9-452f-8a05-4c3caa607a2f/
Even tried dragging document on screen to the flashdrive.
Help!!

Seems I need to repartion it. Uncertain what the valves should be preceeding GiB and following GiB 
Help!!

I should of done this with my laptop that has windows os. Now my favorite flashdrive is useless.

Tried resizing it using similar valves at the link. Now flashdrive rated 1GB. Still useless.
Help!!

---

### Post by Camilia on 2014-11-24
Can someone explain to how to use the GParted Partition Editor to fix my flashdrive. I read the info on it and still don't get it.

yancek do know how to use the partitioner?

---

### Post by kurt18947 on 2014-11-24
> **Camilia said:**
> Can someone explain to how to use the GParted Partition Editor to fix my flashdrive. I read the info on it and still don't get it.

I'll try. Apologies if I'm telling you what you already know.

1)  Are you able to see your flash drive using gparted?  I presume you can because you mention a 1 GB. partition

2) Before you can delete and recreate a partition you'll need to unmount the flash drive.  Once you have highlighted your flash drive, click the menu item 'Partition'  then click 'Unmount'.

3) Once again select your unmounted flash drive. Click the menu item 'Partition' then 'Delete'. Confirm that you wish to delete any existing partitions. Your flash drive should now be blank.

4) Select your now blank flash drive. Click the menu item 'Device'. Click 'Create Partition Table'. Most likely you'll want the default 'msdos' type. You should now have a  flash drive with a FAT32 partition, the partition type on new flash drives.

Be certain that you're working on the correct drive!  It should be pretty easy to tell just by looking at the size in GB. It will also be called something like "/dev/sdb"  You do not want to do anything rash to /dev/sda.  That's usually your hard drive.

I hope this is helpful to you.

---

### Post by yancek on 2014-11-24
kurt18947 explains it very well.  You weren't clear in your earlier posts about exactly what you wanted to do when you said 'clear' which is why I gave the option to either format or delete.  If you want to overwrite whatever is currently on it you would simply format it but first you need to unmount as explained.  Then back to the partition tab at the top and select the option 'Format as' and select whichever filesystem you want.  What are you planning to use the flash for?  Is it just going to be data?  Are you going to use it only with Linux, with Linux and windows?  The link I posted is about as detailed a tutorial as you will find on GParted and reading that may be more helpful than waiting for a reply here.

---

### Post by Camilia on 2014-11-25
> **yancek said:**
> 
Then back to the partition tab at the top and select the option 'Format as' and select whichever filesystem you want.  What are you planning to use the flash for?  Is it just going to be data?  Are you going to use it only with Linux, with Linux and windows?  The link I posted is about as detailed a tutorial as you will find on GParted and reading that may be more helpful than waiting for a reply here.
I want to use the flashdrive to save data and pictures with PC with windows OS and ubuntu OS. 

Resized the flashdrive to 4GiB. Partioned to FAT32. Working fine with PC with ubuntu OS.
Working on PC with windows OS too.

Thanks a bunch Kurt for being so explixcit. Dealing with chronic sinus headaches makes it difficult to comprehend everything I read.

---

### Post by kurt18947 on 2014-12-01
You're welcome.  i hope you feel better.

---

### Post by Camilia on 2015-05-04
bump

---

### Post by bapoumba on 2015-05-04
[http://ubuntuforums.org/showthread.php?t=2273471](http://ubuntuforums.org/showthread.php?t=2273471)
Closing here.

---

