---
title: "Partition"
date: 2008-07-02
forum: General Help
---

### Post by LoneWolfXAxis on 2008-07-02
I am completely unfamiliar with the partition software. i had a friend help me get Ubuntu on my computer before. But now since I have the new 8.04 version, I would like to install it OVER the old ubuntu. How can I do this?

When I open the Norton PartitionMagic 8.0 I keep getting an error everytime I try to delete the old Ubuntu. What is the problem here? Can anyone help? I am total newbie at this so please break it down step by step!

---

### Post by soccerboy on 2008-07-02
can you just not boot into ubuntu and run ```
update-manager -d
``` from the terminal?  This should upgrade you to the latest version.

---

### Post by LoneWolfXAxis on 2008-07-02
Well no. I have had problems with the older version of Ubuntu and it wont work at all. So I need to delete the old ubuntu on my computer or install over it. I can only work on Windows.

---

### Post by soccerboy on 2008-07-02
you can download a software called gparted from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Burn the iso that you download with a good cd burning software and boot into the livecd by editing your boot order.  This program should allow you to delete your partition.  Let me know if you get stuck somewhere.  !!!Backup all important data on the computer you are about to delete partition on!!!

---

### Post by LoneWolfXAxis on 2008-07-02
So the software is a partition editor? I already have ubuntu on another disk. I used Nero to do that...

---

### Post by soccerboy on 2008-07-02
Yes the software is a partition editor and a very good one in my opinion.  If you already have ubuntu on a another disk (cd or hard disk? i don't understand).

If it is on a cd (i assume the installation) the installer also has gparted in it and you can delete the partition during installation or install over the old one by formatting it.

---

### Post by LoneWolfXAxis on 2008-07-02
So if I click on install Ubuntu, it will give me the option of installing it in the partition?

---

### Post by soccerboy on 2008-07-02
yes.  It asks which partition you want to install to in manual partitioning mode.  If you select auto, you can tell it to use all free space or tell it to delete all partitions and use the entire hard drive.  I assume you don't dual boot.  Things get a little more complex if you dual boot.  You have to take care to keep the other os bootable.

---

### Post by LoneWolfXAxis on 2008-07-02
Thing is I am running Windows and I don't want to install over it. Will I be able to install over the whole partition without worrying about deleting Windows? I don't want to loose Windows.

---

### Post by soccerboy on 2008-07-02
if that is the case, (same with me), i don't trust that to the auto partitioning system.  I would pick manual and manually delete the OLD Ubuntu partitions.  Be careful not to delete windows partitions.  A backup of important files should be in order but I have reinstalled ubuntu on the same partition by deleting the partitions in the installer with no problem.  I dual boot Ubuntu and Windows XP.

---

### Post by LoneWolfXAxis on 2008-07-02
Thank you kind sir. I will return with news.

---

### Post by bodhi.zazen on 2008-07-02
a little late perhaps but ...

You do not need to delete anything, just install the new Ubuntu :)

You do, however, need to understand how Linux identifies partitions or you may accidentally install over Windows.

If you understand partitions you are good to go.

---

### Post by LoneWolfXAxis on 2008-07-02
Thanks! I did exactly what you recommended me to do. I still have a problem with the other partitions though. I would like to get rid of them.

---

### Post by LoneWolfXAxis on 2008-07-02
I am also wondering how to set the advanced desktop settings to the cube if anyone can help with that while we are still talking...

---

### Post by bodhi.zazen on 2008-07-02
> **LoneWolfXAxis said:**
> Thanks! I did exactly what you recommended me to do. I still have a problem with the other partitions though. I would like to get rid of them.

See this link :

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

---

