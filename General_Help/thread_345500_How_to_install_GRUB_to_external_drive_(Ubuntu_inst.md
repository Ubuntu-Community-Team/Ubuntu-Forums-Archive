---
title: "How to install GRUB to external drive (Ubuntu installed on external)"
date: 2007-01-24
forum: General Help
---

### Post by presbp on 2007-01-24
I partitioned out my 300GB external harddrive to where I have my root ( / drive) set to 11GB and my swap partition set to 270MB. In the installer my internal harddrive in the drop-down menu says it is sda and the external drive is sdb. 
      The only thing I don't know what to do now is where to install GRUB. I didn't format the drive because I have all of my backup files on my external drive and I don't want to install GRUB on my Windows internal hard drive (I just did a clean reinstall of XP) and I don't want to install GRUB on the partition where I have my backup files. So when it asks me where to install GRUB I chose (/dev/sdb2) and it told me GRUB returned a fatal error and couldn't install there.
           Do I just have to choose /dev/sdb as the place to install GRUB if I don't want it on my internal drive?  I do NOT want GRUB on my Windows drive and I would prefer to not have it on the backup file partition.
        One more question, when I had WIndows XP installed recently I partitioned the internal drive to allow 12 GB of it to be Ubuntu's. My Windows got messed up so I had to format the drive and reinstall Windows completely.. but in the partitioner area it shows my internal harddrive as having like 180GBs of free space (I have a 250GB drive) and then it has 7 or so MBs of unallocated space. Is that from where GRUB was installed last time??

Thanks you guys. I really like the community support.. Help for Windows issues usually requires much more searching and getting half-answers from Microsoft knowledgebase.

Sorry I have already posted this in the installation forum but nobody has answered and I need to get it done.

---

### Post by bodhi.zazen on 2007-01-24
Well, if yo do not install it to the MBR how are you going to boot Ubuntu ?

Floppy?

From the CD ?

I would install gurb into your MBR on your internal windows drive.

Second choice would be the MBR of your external drive and set your bios to boot to it before your HD.

---

### Post by presbp on 2007-01-24
I definitely do not want GRUB on my Windows drive.  I guess I could install it to just sdb (what my external drive shows up as in the install window) and that would put it on the master boot of my external.  My BIOS does support USB booting

---

