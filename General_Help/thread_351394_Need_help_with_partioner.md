---
title: "Need help with partioner"
date: 2007-02-01
forum: General Help
---

### Post by ajohn2550 on 2007-02-01
I am trying to install ubuntu on my hp 
only problem is i cannot resize my sata hard drive.
i am using the alt install cd in oem mode.  
when i go to resize partition 2  which has windows media center on it it does not save the changes i make.  

currently it is devided like this

#1 
    HP recovery drive   8GB
#2 
   Windows xp media center   241 GB 

however when i go into windows it only shows up as  224GB

any help would be appreciated.

---

### Post by rocketman768 on 2007-02-01
Are you trying to shrink the second partition in order to make a 3rd on which to put linux? This is probably not possible with Ubuntu's partitioner. First, Windows tends to use the NTFS file system with which you cannot modify files from linux. Secondly, resizing a partition WITHOUT destroying the data is a _very_ risky process (however, I did this back in 1998 with a program called FIPS I believe). Think about it, data on a partition is pretty scattered. If you shrink the partition from the end towards the front, you might be cutting off essential bits of files. If I were you, I'd go buy a cheap and small hard drive (20-40GB) on which to put linux.

---

### Post by bodhi.zazen on 2007-02-02
It is possible to resize (shrink) the partition with gparted, either from the Ubuntu CD or fro the gparted live Cd.

You should boot to windows and defragment the windows partition first.

Second you can not resize the partition if it is mounted. To unmount the partition:
```
sudo umount /dev/hda2
```

rocketman768: Check out gparted:

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by rocketman768 on 2007-02-02
Cool. I didn't realize that GParted would do non-destructive re-sizing.

However, ajohn is using the alt-install cd. The only other advice I can give is to re-size the windows partition, put your linux partitions in the free space, apply the changes and watch the formatting take place (I think the alt-install asks you several times "are you sure??" before the formatting takes place). If you did it right, linux should install and windows will want to check your drive when you reboot to it.

---

### Post by bodhi.zazen on 2007-02-02
> **rocketman768 said:**
> Cool. I didn't realize that GParted would do non-destructive re-sizing.

8)

> However, ajohn is using the alt-install cd.

Oh, I missed that one ...  Yes, you are of course correct the alternated CD will not resize a ntfs partition ...

> The only other advice I can give is to re-size the windows partition, put your linux partitions in the free space, apply the changes and watch the formatting take place (I think the alt-install asks you several times "are you sure??" before the formatting takes place). If you did it right, linux should install and windows will want to check your drive when you reboot to it.

My 2c are to download the gparted live CD and partition with that. It is not such a large download and it has some additional tools ;)

---

### Post by ajohn2550 on 2007-02-02
ok this is messed up.

i installed a partition manager in windows full version with full fetures.  friend let me use one he had.

however when it trys to resize the ntfs partition before xp boots after rebooting system it says it was done sucessfully.  however when windows xp boots up again it did not  change a thing.

i have a feeling the first "recovery" partition is not leting it edit the 2nd partition.  
sounds like something bestbuy/hp would do.  so i have no clue what to do.

any ideas.

---

### Post by bodhi.zazen on 2007-02-02
1. Install over the top of windows and delete that restore partition.

If you are not quite ready for that:

1. Defragment X2

2. Download the gparted live CD. Not all windows partition managers work well with Linux.

3. resize the ntfs partition.

4. Install Ubuntu into the free space, use defaults.

If that fails, well there are advantages to a second HD ;)

---

### Post by ajohn2550 on 2007-02-03
i would install over windows but 
1 its my dads comp
2 i still need to be able to use windows for games my dad plays and some apps i use.

i will have to try gparted but if not i guess i will just have to wait till later this summer and buy a new sata hard drive

---

