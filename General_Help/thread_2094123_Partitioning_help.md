---
title: "Partitioning help"
date: 2012-12-12
forum: General Help
---

### Post by newellj79 on 2012-12-12
Windows was on my first 3 partitions. Partition 4 shows extended, 5 is ext4 (Ubuntu install), and 6 is swap. I'm trying to fully remove windows, and add the space to Ubuntu. I deleted the first 3 partitions, and tried to simply expand the the 5th partition. It of course would not let me do that. Using some guides, I created a new partition using the space from the deleted ones. New partition is 1. I then copied my system, partition 5 to partition 1, with the plan being boot into the system on partition 1 to make sure all is well, then delete partition 5 and use the free space to expand partition 1. This is where I'm at. I don't know how to boot into the first partition, because grub still reflects my old partitions including windows. So now I'm back in ubuntuon partition 5, with a full copy on partition 1 that I can't get into. On top of this partition 4 again, shows as extended, I have no idea what that is or if it is being used. Its 100gb so if I'm not currently using it I would like to get to the space. But its some how locked so I can't do anything in gparted with it. 

Whew.... Hope this makes sense. Thanks everyone!

---

### Post by offgridguy on 2012-12-12
A screenshot of your partition layout would help.
The  OS locks the partition that is in use, precisley so you can't alter it.
I use a live CD of  parted magic which contains gparted and boot from it to
create, delete or change partitions.

---

### Post by newellj79 on 2012-12-12
I'll get a screen shot tomorrow. I should have mentioned that all of that was done from a live CD.

[IMG]https://www.dropbox.com/s/l912vrtqmgf2mhv/partition.png[/IMG]

---

### Post by newellj79 on 2012-12-13
[IMG]https://www.dropbox.com/s/3e9hmxb6x01lngp/Screenshot%20from%202012-12-13%2016%3A23%3A22.png[/IMG]

---

### Post by mikewhatever on 2012-12-13
You should update Grub by running **sudo update-grub** from the existing Ubuntu installation. That should pick up the changes and update the boot menu.
I suspect that you'll need to fix the UUID in /etc/fstab of the new installation. It can be done from the old installation, run **sudo blkid** to get the UUIDs.

---

### Post by newellj79 on 2012-12-13
Alright here is what I got now.  I managed to to move my system to sda1, and get grub 2 setup right.  I still have no idea what the extended partition is or means.  Using gparted from a live cd does not let me extend either sda1, or sda4 to use the unallocated space.  Adding that space as usable, is my goal here.  Here is a current gparted screen shot.  Thanks!

[IMG]http://i1274.photobucket.com/albums/y430/newellj79/Screenshotfrom2012-12-13163902.png[/IMG]

---

### Post by Kirk Schnable on 2012-12-13
> **newellj79 said:**
> Alright here is what I got now.  I managed to to move my system to sda1, and get grub 2 setup right.  I still have no idea what the extended partition is or means.  Using gparted from a live cd does not let me extend either sda1, or sda4 to use the unallocated space.  Adding that space as usable, is my goal here.  Here is a current gparted screen shot.  Thanks!

(screenshot omitted from quote block)


An extended partition is like a "container" that can hold other partitions.

You see under /dev/sda4 you have the unallocated 146.99 gigabytes of space?  You can make a new partition there, it will become /dev/sda6, and you can put any filesystem you choose on it.

If you don't know how or why you have the extended partition and you don't want it, you could get rid of it, but because your swap partitoin /dev/sda5 is inside it, you have to get rid of your swap partition first.  Does that make sense?

If you get rid of the "extended partition" (container) you can expand /dev/sda1 to take up that unused space if you so choose.

---

### Post by oldfred on 2012-12-13
Please use screen shots and attach with paperclip icon in edit panel above your message.

Partition sda4 is the extended partition and is the container for any number of logical partitions. Currently you only have swap in the extended.

I normally suggest smaller / (root) partitions and either separate /home or data partitions. But if you want to expand your current root you have to shrink the extended first. Or you can put a data partition in the extended or other smaller partitions like another install for testing or just data.
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by newellj79 on 2012-12-13
> **Kirk Schnable said:**
> An extended partition is like a "container" that can hold other partitions.

You see under /dev/sda4 you have the unallocated 146.99 gigabytes of space?  You can make a new partition there, it will become /dev/sda6, and you can put any filesystem you choose on it.

If you don't know how or why you have the extended partition and you don't want it, you could get rid of it, but because your swap partitoin /dev/sda5 is inside it, you have to get rid of your swap partition first.  Does that make sense?

If you get rid of the "extended partition" (container) you can expand /dev/sda1 to take up that unused space if you so choose.

That makes since, I think. So, it looks like the only thing that extended partition is currently being used for is swap right? That is, I'm not storing data there? And if thats the case and I due delete it, for a new partition I will need to figure out how to access the data stored there from Ubuntu. I was really hoping I could just extend sda1. Deleting the extend has nothing to do with me being able to do that right? Thanks form your help!

---

### Post by Kirk Schnable on 2012-12-13
> **newellj79 said:**
> That makes since, I think. So, it looks like the only thing that extended partition is currently being used for is swap right? That is, I'm not storing data there? And if thats the case and I due delete it, for a new partition I will need to figure out how to access the data stored there from Ubuntu. I was really hoping I could just extend sda1. Deleting the extend has nothing to do with me being able to do that right? Thanks form your help!

It sounds like you understand... To reinforce my technical description, here's a good analogy for your situation.  I will convert Gigabytes to Square Feet for the sake of argument.  

You have a 300 sq.ft room (your 300GB hard drive).  You have a 153 sq.ft box, and inside it, you put a pile of books occupying 6 sq.ft.  You still have 145 sq.ft in your room that's not occupied by the box, and you have another 146 sq.ft inside the box that's empty (your extended partition).

You can either choose to use the remaining space in your box for additional storage, or you can take the box out, stuff your pile of books in the corner, and have 290 sq.ft of empty room to store your files.

Either option will work for you.  You can delete your swap partition, as it contains nothing of any particular value.  However, you must disable it or be using a Live CD (you can't delete swap that's in use).

You can use the **swapoff** command to disable it.  If you need help with this, we can certainly help you.

Afterwards, you could hypothetically expand /dev/sda1 to occupy the 146GB you're not currently using, and make a new 6GB swap partition, then turn that swap partition on.

---

### Post by newellj79 on 2012-12-13
> **Kirk Schnable said:**
> It sounds like you understand... To reinforce my technical description, here's a good analogy for your situation.  I will convert Gigabytes to Square Feet for the sake of argument.  

You have a 300 sq.ft room (your 300GB hard drive).  You have a 153 sq.ft box, and inside it, you put a pile of books occupying 6 sq.ft.  You still have 145 sq.ft in your room that's not occupied by the box, and you have another 146 sq.ft inside the box that's empty (your extended partition).

You can either choose to use the remaining space in your box for additional storage, or you can take the box out, stuff your pile of books in the corner, and have 290 sq.ft of empty room to store your files.

Either option will work for you.  You can delete your swap partition, as it contains nothing of any particular value.  However, you must disable it or be using a Live CD (you can't delete swap that's in use).

You can use the **swapoff** command to disable it.  If you need help with this, we can certainly help you.

Afterwards, you could hypothetically expand /dev/sda1 to occupy the 146GB you're not currently using, and make a new 6GB swap partition, then turn that swap partition on.

Thank you so much. I hope to have time tackle this tomorrow. Your help has been fantastic. Please check back in case I need more. :)

---

### Post by Kirk Schnable on 2012-12-13
> **newellj79 said:**
> Thank you so much. I hope to have time tackle this tomorrow. Your help has been fantastic. Please check back in case I need more. :)

Like all the threads I respond to, I am subscribed to yours and I will be notified via email of followup posts.  Glad I was able to be of assistance.

---

