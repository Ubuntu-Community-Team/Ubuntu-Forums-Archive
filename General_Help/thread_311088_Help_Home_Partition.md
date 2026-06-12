---
title: "Help: Home Partition"
date: 2006-12-02
forum: General Help
---

### Post by JohnH on 2006-12-02
G'day,

I followed the instructions at [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")but somehow I wrecked it (I'm sure I followed it to the letter). However my home partition is still intact. I was forced to reinstall Edgy. How do it get the new install to use my home partition as the default "home"? I'm not the sharpest tool in the shed so I need relatively clear instructions. 

Regards
John

---

### Post by taurus on 2006-12-02
When you get to the partitioner part, tell it to mount that partition to /home.  You will get an option to either format it or keep all your data intact.

---

### Post by strabes on 2006-12-02
On the installer, instead of choosing to format the entire disk, you have to choose to manually partition the drive. Then you should create the first partition for your linux install, the second for swap (if you have <1024mb RAM), and the 3rd for your /home directory.

---

### Post by JohnH on 2006-12-02
thanks for the replies.

That is what I did. But maybe I misunderstood how this is supposed to work. I can actually see my home partition on the desktop. With this method I assumed that Ubuntu would replace the /Home/myname with the /dev/mypartition/home/myname. Is this how it is supposed to work? If so, how do I get it to do it?

Regards
John

---

