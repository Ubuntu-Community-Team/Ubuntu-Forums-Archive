---
title: "Please help organise my partitions"
date: 2013-04-02
forum: General Help
---

### Post by samsom63 on 2013-04-02
Hi folks,

I recently installed xubuntu 12.04 alongside win7 on my eee pc. Problem is, the netbook is shipped with all primary partitions used, so I had to mess around in my partitions. In fact, I just deleted the D: drive ....

I got the installation working, but now my partitions are a mess: see screenshot of GParted attached. Ideally, I would like to format the 136GB unallocated space to NTFS as I store my music in Itunes and thus want most of the space for win7. Now, i know how to format to NTFS but then? Is it possible to merge this space with the existing C: drive?

Further, there is this other 14GB unallocated space that I cannot even format into anything. All the options are grayed out for this one.

Any help would be greatly appreciated!!

---

### Post by grahammechanical on 2013-04-02
My guess is that you still have four primary partitions used up. When you freed not only space for Ubuntu but a primary partition you should have created a primary partition and changed it to an extended partition. We can put any number of logical partitions inside an extended partition and we can install Ubuntu in logical partitions.

My suggestion. As Ubuntu is a new installation (in sda3?), then delete the partition. Move sda2 closer to sda1. Mege all the unallocated space together turn it into one primary partition that is also an extended partition and inside the extended partition create 3 logical partitions - one for NTFS, one for Ubuntu and one for Swap. Make it so that Ubuntu and swap are at the end of the extended partition.

Actually I would create 4 logical partitions

NTFS
Ext4 mount point /
Ext4 mount point /home
Swap

With a spearate /home partition we can re-install Ubuntu into / partiiton without loosing our settings and data which are in /home partition.

Regards.

---

### Post by samsom63 on 2013-04-02
> **grahammechanical said:**
> My guess is that you still have four primary partitions used up. When you freed not only space for Ubuntu but a primary partition you should have created a primary partition and changed it to an extended partition. We can put any number of logical partitions inside an extended partition and we can install Ubuntu in logical partitions.

My suggestion. As Ubuntu is a new installation (in sda3?), then delete the partition. Move sda2 closer to sda1. Mege all the unallocated space together turn it into one primary partition that is also an extended partition and inside the extended partition create 3 logical partitions - one for NTFS, one for Ubuntu and one for Swap. Make it so that Ubuntu and swap are at the end of the extended partition.

Actually I would create 4 logical partitions

NTFS
Ext4 mount point /
Ext4 mount point /home
Swap

With a spearate /home partition we can re-install Ubuntu into / partiiton without loosing our settings and data which are in /home partition.

Regards.

Hi, thanks for your answer! 

However, being very ignorant of hardware issues, I am trying to fully grasp what you mean. I understand the point about the 4 partitions used up and the need to create an extended partition. However, I still struggle with the rest of your suggestion. If I delete sda3, I presume I lose everything, including /home ?? Besides, I suspect I cannot do that from my xubuntu session. Now, there is no data that I particularly want to save (all is in the cloud), so I've got no problem wiping out and reinstalling Xubuntu, but I still don't quite understand how I should proceed.

I'd be very grateful if you could take the time to provide a slightly more detailed procedure. Again, messing with partitions make me very nervous...

---

### Post by grahammechanical on 2013-04-02
It scares the life out of me as well, and I have done it a few times. It is the warning message that frightens me. But then again mistakes are made when we get too casual about things. Here is a link to the Community Documentation. It has some pics that will give some idea of what you will see.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

We do this from a live session. Load the session to the desktop and search for Gparted in the Dash. I suggest we do this one operation at a time. Gparted will work its way through a list of operations. But these take a while to run. I am much more comfortable doing one operation at a time.

So what do we want to do?

1) Move sda2 to the left. See this section

[https://help.ubuntu.com/community/HowtoPartition/MovingPartition](https://help.ubuntu.com/community/HowtoPartition/MovingPartition)

Run that operation and shutdown the live sesson and boot into Windows and check that every thing is safe.

2) What is sda4? It is a partition. Do you have any idea what it is for? It is empty. Delete it? Follow the section:

[https://help.ubuntu.com/community/HowtoPartition/DeletePartition](https://help.ubuntu.com/community/HowtoPartition/DeletePartition)

Shut down the live session and boot Ubuntu and Windows. I know that this seems a long way of doing things but it is a method that I feel comfortable with.

3) Ready to delete sda3 - Ubuntu? You now know how to do that.

You should now have 2 partitions sda1 and sda2 and a working Windows but no Ubuntu and masses of unallocated space all in one place. Yes? So far so good.

4) turn the unallocated space into an extended partition.

[https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition](https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition)

Did you notice that you get a menu that lets you choose to create a primary, logical or an extended partition. You use that same method to create 4 logical partition inside that large extended partition. See the Creating Partitions sections but we are not creating primary partitions but logical partitions and we are giving each partition a file system, NTFS, Ext4 as the case may be.

Make a note of the names or locations of these partitions - their sda number. Because when you reinstall Ubuntu you choose the Do Something Else option and at the partitioning section you ignore the new NTFS partition. You put Ubuntu into the partition you want it to go in - size about 20GB with a mount point of / and you select the partition for /home and give it a mount point of /home (size of your choosing) and then you select the partition to be swap and give it a mount point of swap (size twice RAM to allow for hibernation).

see how you go.

---

### Post by samsom63 on 2013-04-02
> **grahammechanical said:**
> It scares the life out of me as well, and I have done it a few times. It is the warning message that frightens me. But then again mistakes are made when we get too casual about things. Here is a link to the Community Documentation. It has some pics that will give some idea of what you will see.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

We do this from a live session. Load the session to the desktop and search for Gparted in the Dash. I suggest we do this one operation at a time. Gparted will work its way through a list of operations. But these take a while to run. I am much more comfortable doing one operation at a time.

So what do we want to do?

1) Move sda2 to the left. See this section

[https://help.ubuntu.com/community/HowtoPartition/MovingPartition](https://help.ubuntu.com/community/HowtoPartition/MovingPartition)

Run that operation and shutdown the live sesson and boot into Windows and check that every thing is safe.

2) What is sda4? It is a partition. Do you have any idea what it is for? It is empty. Delete it? Follow the section:

[https://help.ubuntu.com/community/HowtoPartition/DeletePartition](https://help.ubuntu.com/community/HowtoPartition/DeletePartition)

Shut down the live session and boot Ubuntu and Windows. I know that this seems a long way of doing things but it is a method that I feel comfortable with.

3) Ready to delete sda3 - Ubuntu? You now know how to do that.

You should now have 2 partitions sda1 and sda2 and a working Windows but no Ubuntu and masses of unallocated space all in one place. Yes? So far so good.

4) turn the unallocated space into an extended partition.

[https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition](https://help.ubuntu.com/community/HowtoPartition/ExtendedPartition)

Did you notice that you get a menu that lets you choose to create a primary, logical or an extended partition. You use that same method to create 4 logical partition inside that large extended partition. See the Creating Partitions sections but we are not creating primary partitions but logical partitions and we are giving each partition a file system, NTFS, Ext4 as the case may be.

Make a note of the names or locations of these partitions - their sda number. Because when you reinstall Ubuntu you choose the Do Something Else option and at the partitioning section you ignore the new NTFS partition. You put Ubuntu into the partition you want it to go in - size about 20GB with a mount point of / and you select the partition for /home and give it a mount point of /home (size of your choosing) and then you select the partition to be swap and give it a mount point of swap (size twice RAM to allow for hibernation).

see how you go.

Thank you very much for this!! I'll do this tomorrow and let you know how it went, but it all seems clear now.

I am new to the Ubuntu (or Linux for that matter) community, and while I enjoy greatly the distros, I think that it is the fantastic community support that astonishes me most. Many thanks again for taking the time to respond.

---

### Post by samsom63 on 2013-04-05
Here's the update: I deleted the small sda4 partition and increased the size of sda1 and sda3 by taking on the adjacent unallocated spaces. However, I did not erase sd3 and create an extended partition instead as I got too lazy. Instead, I created a NTFS primary partition that became my new D: drive on win7. 

Overall, I regained all the unallocated spaces I had, and both systems boot perfectly, so many thanks for your advice again :-)

---

