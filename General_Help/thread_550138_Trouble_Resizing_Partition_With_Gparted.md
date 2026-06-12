---
title: "Trouble Resizing Partition With Gparted"
date: 2007-09-13
forum: General Help
---

### Post by bananaman on 2007-09-13
Now, this is the issue at hand and I'll be as clear as possible.

Before now:
I had a 230gb hard drive... partitioned in 3: (hda1/reiserfs/213Gb), (hda2/swap/2Gb) and (hda3/ntfs/15Gb).

I wanted to move my home folder to a new reiserfs partition, but my home folder is about 100Gb... so I cut up the first partition in 2. After that I had:

hda1/reiserfs/107Gb
hda4/reiserfs/105Gb
hda2/swap/2Gb
hda3/ntfs/15Gb

What I did then was move my 100Gb home folder (as per the instructions) to the new partition. I rebooted and everything worked... so far so good.

Now... I deleted the backup of my home folder from my first partition (hda1) because I already have the working copy on the new partition (hda4).

So now what i want is give 90Gb from the first partition (hda1) to the new one (hda4) because I dont need that much space for the ubuntu installation, but I do want it for file storage in my home folder (now on hda4).

I successfully resized hda1 from 100Gb to 10Gb using the live CD and Gparted... but now the 90Gb left of unallocated space, I cannot add to my new partition (hda4).

Gparted tells me I can move/resize, but that isnt so... I can only resize partitions from the right and this unallocated space is on the left of my new partition (because it used to belong to the first partition on the disk)... and neither can I move the new partition to be next to the first one so that i can then resize it to the right...

[[IMG]http://img385.imageshack.us/img385/2029/gparted1xw9.th.jpg[/IMG]](http://img385.imageshack.us/my.php?image=gparted1xw9.jpg)

[[IMG]http://img208.imageshack.us/img208/5862/gparted2lq7.th.jpg[/IMG]](http://img208.imageshack.us/my.php?image=gparted2lq7.jpg)

So here I am... stuck and not knowing what to do... does anyone have any suggestions? Also, Gparted tells me I can only have 4 partitions on a disk, no more, so I cannot assign a new format to that unallocated space...

In case its not clear, what I want is for my 2nd partition on the disk (hda4) to absorb that unallocated space...

Help?

Thanks in advance...

---

### Post by prince_niceguy on 2007-09-13
You can have only limited number of primary allowed on disk. You can have extended partitions but if you create extended partition then it would be a problem that you cannot merge it with primary partition unless you remove extended partition.

I am not sure and I have not used logic volume manager but seems it might help you in this case.

---

### Post by bananaman on 2007-09-13
Yes, I can only have 4 primary partitions on a drive... and thats what I want... my problem is adding the unallocated space to the second primary partition... 

Im not sure I understood your suggestion, create an extended partition? What will that do? Thanks for the reply

---

### Post by prince_niceguy on 2007-09-13
sorry misunderstood the config... i can only think of one thing... 

boot from live cd. remove the swap...

format the unformatted to some filesystem then copy the data from hda4 to the new partition.

then remove hda4 and then you would be able to resize to right...

then recreate swap....

---

### Post by bananaman on 2007-09-13
Hadnt seen your reply, yes thats what I did... the hard way...

Formated it to reiserfs, copied from the other one, then formatted the other one and added that space to the first one... I had some permission issues after that because I copied the files as root but my brother reset the permissions to my user and all was fine...

Thanks for the help...

---

### Post by bodhi.zazen on 2007-09-14
:lolflag:

FYI this problem is solved with newer versions of gparted.

In the future you can try the gparted live CD.

Or the gutsy version (gparted is updated in gutsy, but not before)

---

