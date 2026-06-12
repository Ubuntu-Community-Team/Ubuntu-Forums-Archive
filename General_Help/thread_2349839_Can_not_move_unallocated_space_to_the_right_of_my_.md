---
title: "Can not move unallocated space to the right of my Ubuntu partition...HELP please :)"
date: 2017-01-18
forum: General Help
---

### Post by alambrito86 on 2017-01-18
I attached a screenshot below of what is happening.

Basically, I shrunk the Windows partition (sda4) so that I can use that free space for the Ubuntu system.

As you can see below, the unallocated space is two slots above my Ubuntu partition (sda6). I have done swapoff with the linux swap drive, unmounted all drives, but am unable to move the partition to the right of it no matter what I try. Not sure why my drive has so many partitions lol. It's a Samsung 250 GB SSD drive.

Any suggestions here as to what I can do? I love my new Ubuntu! Thank you.

---

### Post by gdesilva on 2017-01-18
Have you tried moving sda5 and sda6 to the left?

---

### Post by alambrito86 on 2017-01-18
I have not tried that. To be dead honest, I'm not 100% clear on how to do that without destroying everything.

---

### Post by alambrito86 on 2017-01-18
I'm assuming, in GParted:
-I would click the resize/move tool for sda5 and move the slider bar all the way to the left and maintain it's original size...which would then push the unallocated space below it. 
-Then repeat that same process for sda6, which would then move the unallocated space again and now below it.
-Then resize sda6 to include the unallocated space that would, in theory, be below it?

Hopefully I described that correctly. Thanks so much for the help!

---

### Post by yancek on 2017-01-18
Theoretically, what you suggest in your last post should work but when you are moving partitions around there is always a probability of data loss.  The partition you want to move is a windows partition and the data on it could easily fit on a CD.  I don't know what that partition is but you seem to have to with the same labelling.  Surely there must be some way in windows that you could do this.  Maybe Disk Management as they are windows partitions.

If you then move sda6 to the left, you will be moving the location of the boot files which could be problematic also.
Your basic problem is that when you installed the Ubuntu system partition was too small.  You could simply create a Linux partiiton out of the unallocated space and use it for data or put your /home on that partition.

---

### Post by alambrito86 on 2017-01-18
I'm honestly not sure what that partition is. Under Disk Management in Windows, it lists at as a recovery partition, but sda1 is also listed as a recovery partition.

---

### Post by alambrito86 on 2017-01-18
This is what it shows from within Windows using MiniTool

---

### Post by gdesilva on 2017-01-19
Agree with yancek's comment about the potential data loss when moving partitions although fortunately I have not had that experience so far - I guess it is a matter of time! Perhaps one way around this issue is to take a disk image using Clonezilla so that you have a back up image to restore should everything turns into custard - this way you will have a back up of all your partitions.

---

### Post by alambrito86 on 2017-01-19
I ended up taking you advice and making that partition for my Linux home files. Solved the problem. Cleared up a bunch of space on the root drive and all is working properly thanks to your suggestion and this link mainly ([https://www.maketecheasier.com/move-home-folder-ubuntu/](https://www.maketecheasier.com/move-home-folder-ubuntu/))

Side note: I did end up researching the random ntfs drive that was in between everything and couldn't find anything on it nor did I really see Windows depending on it for anything. I deleted it. Then resized the one above that was unallocated to merge the two into one ext4 partition. Now I have one single ext4 drive for the home files. One for the root files. One Linux Swap. No pointless partitions left in there.

All is working great and smoothly! Hope this can help someone else too. And I absolutely had everything backed up beforehand. Makes things a lot less stressful!

THANK YOU THANK YOU! You guys rock

---

