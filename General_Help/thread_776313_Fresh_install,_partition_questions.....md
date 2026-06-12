---
title: "Fresh install, partition questions...."
date: 2008-04-30
forum: General Help
---

### Post by Kanaric on 2008-04-30
I bought a couple of new hard drives and I heard good things about JFS and want to try it out and do a fresh install. What kind of a partition scheme should I use? I didn't do much research on partitions on my first install and just used the default installer setup.

What file system should I use for /boot? Is there anything better than EXT2 or should I just stick with that?

Anyone have an experience with JFS so I know what to expect?

How much space should I allocate to /boot and /swap?

What kind of "options" on the partitions should I use?

I have 2GB of ram, soon to upgrade to 4GB and this is for a desktop computer. Using hardy...

---

### Post by bodhi.zazen on 2008-04-30
You do not need all those things on a separate partition, all you need it / and swap.

I advise swap = RAM x 2 , max 1 Gb, swap == RAM on laptops where you use suspend.

If you want to make a /boot, ext2 is fine. You will not be using a journal so a journaled file system just takes up space. 1 Gb for /boot is overkill, you could do 0.5 Gb.

I advise a separate data partition, mounted in /media/data or where you will.

In the end it is not a big deal as you can resize partitions later if needed.

If you want to make your life complicated :

[http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System](http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System)

[http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html](http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html)

---

### Post by Kanaric on 2008-05-01
Thanks for the reply.
> I advise swap = RAM x 2 , max 1 Gb, swap == RAM on laptops where you use suspend.
definitely thank you for this because I forgot about suspend so I probably would of just used 512 like I used on my PC, lol.

---

### Post by elvinatom on 2008-05-01
I would stay away form jfs, xfs and reiserfs. Because of technical issues these filesystems can be utterly destroyed when a power loss occurs (during a heavy write). These filesystems are super-fast because they spare some important security features.  Ext3 might be slow, but imo the risk of complete data loss are not worth the extra write speed. Don't go with Ext2 either because it can't do journaling.
Of course if stability is no concern (because the data is easily restored if lost or is simply not important) then I suggest xfs/jfs for partitions containing big files and reiserfs for the rest.

---

### Post by articpenguin on 2008-05-02
I find JFS as stable as ext3. Reiserfs and xfs are the ones that crash easy.

---

