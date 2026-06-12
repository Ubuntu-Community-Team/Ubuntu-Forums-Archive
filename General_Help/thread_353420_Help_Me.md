---
title: "Help Me"
date: 2007-02-04
forum: General Help
---

### Post by maceylou on 2007-02-04
I have ubuntu running on my computer now. This is a recent transition for me. At once I had windows xp intalled on one of my partitions /dev/sda5. I have formated this to extended 3,and now it is free space. I want to incorperate it with my ubuntu /dev/sda3. In other word I want these to be one partition. How do I do this? I also do not want to lose my current ubuntu settings.:(

---

### Post by allwin on 2007-02-04
> **maceylou said:**
> I have ubuntu running on my computer now. This is a recent transition for me. At once I had windows xp intalled on one of my partitions /dev/sda5. I have formated this to extended 3,and now it is free space. I want to incorperate it with my ubuntu /dev/sda3. In other word I want these to be one partition. How do I do this? I also do not want to lose my current ubuntu settings.:(

I'm too much of a noob to guide you through this step by step BUT...if you GOOGLE around for "GPARTED live cd" you can download another live CD of a different flavor of UNIX which contains all the tools you should need to move your partitions around and expand them and so forth.  It's kind of like a free version of the commercial package Partition Magic.  However, I'm not absolutely sure your particular partitions can be merged exactly the way you have them laid out.  I used this to copy a dual boot system from one internal HD to another, expanding the partitions and so forth.  The only problem was I could not boot until I installed GRUB from the Ubuntu Live CD.  So if you have Linux, XP, and FREE, and you want to end up with XP, (Linux + FREE) it's possible.  You may have to copy UBUNTU to the free space, delete the old UBUNTU partition, move the XP left, move the new UBUNTU left, and then expand it to include the free space.  Then deal with GRUB using the live CD.  That's a broad outline, as I said, I don't consider myself qualified to explain in further detail. 

As always, be sure you have backup in case something goes wrong.  Hope that helps.

---

### Post by STREETURCHINE on 2007-02-04
gparted should be fine for this,
just delete the partition you dont want and extend the outher partition.
 back up all your info first,and folloow the instructions on gparted,

---

