---
title: "Partitions problem"
date: 2007-05-04
forum: General Help
---

### Post by Mulajokull on 2007-05-04
Hi. 

I have installed Ubuntu Festy. I have two partitions (in fact 3 if we counted swap).

In one I have root and in another one/ home. I have chaged the size of the partitions. Root has made it perfect. But when it was with /home the light has gone… and partition doesn't work! 

Now, when I start ubuntu, it says to me that there is no /home for my user. If I take with live CD and mount the partition it appears an enormous file.

I want to recover the data (or the partition) in /home (if not,  I am dead man) 

Do you believe that I will obtain it with testdisk? In principle he is the one that I will use since. 
Or do you know some other program? 

Thanks in advance

PS: Already, the next time I do backup before touching the partitions

---

### Post by seshomaru samma on 2007-05-04
If you can access it with the LiveCD then you can recover the data with the live CD
Personally I prefer to use Knoppix as a LiveCD but an Ubuntu one will do.
Boot from it, install Gparted (maybe it's already installed)
```
sudo apt-get install gparted
```
resize ,change,create partitions as you like
copy your data to wherever
reboot

---

### Post by zvacet on 2007-05-04
Download Gparted live CD.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

