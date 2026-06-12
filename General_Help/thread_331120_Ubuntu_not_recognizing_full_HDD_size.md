---
title: "Ubuntu not recognizing full HDD size"
date: 2007-01-04
forum: General Help
---

### Post by sdelano on 2007-01-04
Hello,

This is my first post here and I have been using Linux on and off for about a month and a half and have finally settled on Ubuntu as my distro of choice. 

Therefore, I am now attempting to format my two 300GB hard drive on which I store my movies and music to ext3 from NTFS. I have backed up one and attempted a format and have finally settled on GParted as the tool of choice after using parted and fdisk combined with mkfs in command line.

I have modified the /etc/fstab to mount the HDD when I login and used :
```
 e2label /dev/sdb1 DATA 
```
to generate a label and used:
```
 LABEL=DATA /media/data default 0 0 
```
in /etc/fstab

The HDD mounts fine and I see it on my desktop but the problem is in the free space. There are only 260.9GB of free space on the drive and GParted shows the drive to be 279.46GB w/ 4.57GB used (for some odd reason but I assume it has to do with the format and 274.89GB free.

Where did my 14 GB of space run off to? Between the two hard drives I do not want to lose 30BG of space. The same thing happens when using parted, fdisk, and mkfs.

Thanks,
Stephen

---

### Post by taurus on 2007-01-04
If you are using ext3, then 5% of your disk space is reserved for journaling.  And by the way, an entry for that harddrive in /etc/fstab should look something like this!!!

```

LABEL=DATA   /media/data  ext3   defaults   0   1

```

---

### Post by mcduck on 2007-01-04
The 5% of the disk is not reserved for journaling, but for root user and the system itself (to make sure that normal users cannot fill the disk to the point that it's not able to boot any more.

You can change the amount of reserved space to 0 with 'sudo tune2fs -r 0 /dev/sdb1', but I recommend leaving it on for your root partition and only changing this for extra storage partitions and such.

---

### Post by sdelano on 2007-01-04
Thank you mcduck that worked perfectly (it is a storage partition after all)

@taurus:

That is what the entry looked like I was just tring to remember it off the top of my head (I did still have the second 0 there but have since changed it to a 1.

Now that I have the full space I am running into another problem. 

When I try to write to the hard drive it gives me an error that i do not have permission to write to this drive. I am not at home right now or I would give the exact error but how do I fix this? (I can give the exact error in a few hours when I return home).

Thanks,
sdelano

---

### Post by bodhi.zazen on 2007-01-04
Mount the hard drive

```
sudo chmod 777 /media/data
```

mcduck: Very cool post, thank you :p

---

### Post by sdelano on 2007-01-04
Thanks a ton guys. These forums are amazingly fast. This makes me extremely glad that i chose Ubuntu as my distro. 

About the chmod: do I have to do this everytime I restart? If so i could just add it in a script along with the command to unmap Shift+Backspace from the restart commands....what an annoyance (I restarted about 8 times when writing my original...how ironic I just did it again)

Thanks
sdelano

---

### Post by bodhi.zazen on 2007-01-04
> **sdelano said:**
> About the chmod: do I have to do this everytime I restart? 

Thanks
sdelano

NO ! In this case, once is enough :p

---

### Post by lucky_chouhan on 2007-01-05
Here is some details -

20 GB    -      18.26 GB (after formated FAT32 Or NTFS)
40 GB   -       37.41 GB  (after formated FAT32 Or NTFS)
80 GB  -        76.12 GB  (after formated FAT32 Or NTFS)
160 GB  -      149.32 GB (after formated FAT32 Or NTFS) 

personally my tested.


That size is windows as well as linux.

---

### Post by sdelano on 2007-01-09
lucky this is about standard for all hard drives that are shipped from manufacturer. They are usually a few GB short of the advertised size. The problem with my HDD was that linux was reserving those extra GB just so I didn't use them a prevent the hard drive from booting. Yes, my 300GB HDD only shows up as 274.9 now, but that is what it has alsways been ever since I bought it even in windows. Before I go tthe help from mcduck the drive only showed 260 GF of space.

sdelano

---

### Post by lucky_chouhan on 2007-01-09
my 80 GB show 76 GB on ubuntu.

---

