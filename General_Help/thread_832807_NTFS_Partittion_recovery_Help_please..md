---
title: "NTFS Partittion recovery Help please."
date: 2008-06-18
forum: General Help
---

### Post by ati on 2008-06-18
Hallo,

I have made a huge mistake when I reinstalled Ubuntu.
I had 4 partitions on hda.
Hdb was for linux.
I accidentely chose to do the automatic partitioning and ended up having Ubuntu using hda instead of hdb.
Now of course all my ntfs partittions are gone and have 2 linux partitions, a large and a small swap partition.

I know it is my own stupidity and there is no need to point that out. ] (*,) 
Is there a way to recover the partittions or at least some of the data? 
The importent data I would have to recover was on the partittion 2,3. I probably can forget about getting back the 1st one because that is the place where linux ended up, isn't it?

Please any help is appriciated.
Thank you.

---

### Post by pedro_orange on 2008-06-18
Well if the other partitions were not touched during your Ubuntu install, theoretically you should just be able to mount the other partitions from within Ubuntu and take what you want off them.

However, if during the installation you wiped the partitions, then you're probably not going to recover anything without one of those data recovery things. However I have no experience/faith in them.

---

### Post by greco8523 on 2008-06-18
In this case your going to need to use data recovery programs. Theres TestDisk that might help you to find information of the NTFS partition that might still be on your disk. Heres a website with data recovery advice that might help: 

[http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html](http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html)

Also if you download any windows commercial based data recovery tools you will be able to scan for the data and the NTFS partition which will be more detailed than TestDisk. The amount of corruption of your files will depend on the size of the files. For example images and videos are likely to be corrupt in some way, small text documents and  spreadsheets will have less corruption. 

Hope this helps tell us how you get on.

---

