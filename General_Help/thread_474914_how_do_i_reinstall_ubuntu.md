---
title: "how do i reinstall ubuntu??"
date: 2007-06-15
forum: General Help
---

### Post by linux noooob on 2007-06-15
ok so i installed ubuntu and i left my windows partition but how do i uninstall ubuntu so i can reinstall ubuntu?? or how do i wright over the ubuntu partition without wrighting over windows.

ps sorry for the bad spelling

---

### Post by NeoLithium on 2007-06-15
Well, since you already have an existing version of Ubuntu installed, you can use the CD once again, select install, and then when it comes up to the partitioning question, just select your Ubuntu partitions to be used and it will overwrite the previous installation :)

Hope this helps, 
Neo

---

### Post by mikewhatever on 2007-06-15
At the partition management stage, simply pick the /, swap and home if separate, format and install. Do not format the Windows partition.

---

### Post by linux noooob on 2007-06-15
ya but i also wanted to add some more free space to it and i thought by reinstalling it over the former ubuntu partiton and the free space i would not have to worry about working on adding the free space to the already installed ubuntu.

---

### Post by mikewhatever on 2007-06-15
> **linux noooob said:**
> ya but i also wanted to add some more free space to it and i thought by reinstalling it over the former ubuntu partiton and the free space i would not have to worry about working on adding the free space to the already installed ubuntu.
Then you should redo Ubuntu partitions. Delete the current ones, shrink whatever you need to shrink, then make the new partitions in the unallocated space.

---

### Post by linux noooob on 2007-06-15
it will not let me delete the partitions the two partitions have a light blue box around them and it locks it there or somthing so i can't move delete or edit the partiton!!!!](*,)

---

### Post by strabes on 2007-06-16
Is this happening on the live CD? It shouldn't. The only time that those 'blue boxes' appear are when the partitions are mounted.

---

### Post by DagMan on 2007-06-16
He has an extended partition and resizing it or logical partitions within it is the problem.  I don't remember off the top of my head apart from saying that every time I do this I have to shuffle data all over the place and delete partitions in order to get what I want in the end.
Anyhow, that I think is why he can't just simply resize so if someone who can help from that perspective....

---

### Post by linux noooob on 2007-06-16
it also says the partition is busy when i am on the live cd ????????? what does it all mean??????](*,)in the partition maneger it will not let me move ext3 partitions?? why? what do i do!!!](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by DagMan on 2007-06-16
your swap partition would be active.  right click on it and turn it off.
the partition editor on the live cd mounts things after it makes changes so everything needs to be unmounted again.  Except swap I think only the one time you have to do.

If you still want to go the route of wiping things out to reinstall, the you can delete all the partitions inside that extended partition, the light blue thing, then also delete the light blue thing as well and go from there however if resizing is doable without much trouble then it's easier.  
You'lle lose all data on deleted partitions.  Be sure to hit apply or all you've done is marked changes without applying them.

Partitions aren't really moved, the data is swapped around and a new partition is made and the old deleted.  That's how youd'e want to do it if you want to "move" a partition,  You need to copy data around and redefine the partitions.  The only moving is resizing and there is the problem when resizing logical partitions.
Good Luck.  I've done my learning with it the hard way losing data.

---

### Post by linux noooob on 2007-06-16
ok but the only option for the light blue box is information and it says that it is busy on the live cd??

---

### Post by linux noooob on 2007-06-16
nvm problem solved

---

