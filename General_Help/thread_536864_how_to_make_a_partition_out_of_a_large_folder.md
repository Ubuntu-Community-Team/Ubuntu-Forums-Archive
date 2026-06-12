---
title: "how to make a partition out of a large folder"
date: 2007-08-28
forum: General Help
---

### Post by nephish on 2007-08-28
i have a folder that stores all my media on my home computer, also it is an nfs share so the other computers in the house can access them too. However the folder is rather large, lots of home videos, etc.. about 90GB.

now i only have two partitions,  /   and  /swap
i am thinking that if i needed to re-install my OS, or something else, i am kinda screwed, as i do not have an easy way to back up all that stuff. 

So, is it possible to make another partition, ext3 ( which all of my drive is save swap ) and put all this stuff there ? 

I know that i can make a partition out of free space, but can i make one using most of the space on this drive ? This partition would take up most of the room on my drive. I only need, i suppose, about 10 GB for the OS and such.

thanks for any tips

---

### Post by notwen on 2007-08-28
This is very do-able.  First off get a hold of gParted.  You can download the gParted LiveCD [here]("http://gparted.sourceforge.net/download.php").

It should be a fairly straight-forward process, gParted will show you all of your HDD(s) partition by partition.  Are there any other OSes installed on this PC or strictly Linux?

---

### Post by nephish on 2007-08-28
No, only Ubuntu 7.04 is installed. I wanted to tinker with the new Gutsy, but still maintain
my stuff folder, and preserve anything in case i needed to switch back to Fiesty.

thanks for your help on this.

---

### Post by Wolki on 2007-08-28
> **nephish said:**
> 
I know that i can make a partition out of free space, but can i make one using most of the space on this drive ? This partition would take up most of the room on my drive. I only need, i suppose, about 10 GB for the OS and such.


You can resize a partition, but I doubt its possible to turn used space on one partition into another. Even if it was possible, it'd be dangerous because errors with resizing can happen which might lead to data loss. My recommendation would be to backup your data to an external hdd or dvds, then remove them from the hdd. Then you can resize that partition and create a new one using, for example, the gparted livecd that notwen mentioned, a standard ubuntu desktop cd should work too. Afterwards, configure your system to recognize the new partition (usually via an entry in /etc/fstab) and put your stuff there.

---

### Post by notwen on 2007-08-28
> **nephish said:**
> No, only Ubuntu 7.04 is installed. I wanted to tinker with the new Gutsy, but still maintain
my stuff folder, and preserve anything in case i needed to switch back to Fiesty.

thanks for your help on this.

Download the gParted LiveCD, I'm not sure if the Feisty LiveCD has gParted, seems like they used an alternative partition manager last time I installed from a Feisty cd..  In the end you'll be resizing your current Ubuntu(Feisty) installs partition and using the free space to create a new partition for your new Ubuntu(Gutsy) install.

---

### Post by nephish on 2007-08-29
as a little follow up, i downloaded gparted, booted off it, did everything i needed to (carefully) and rebooted, mounted my new partition, and away we go ! Now i can play with Gutsy without worring about gakking up my stuff. 

thanks for the advice, gents !

---

