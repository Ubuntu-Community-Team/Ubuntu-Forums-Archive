---
title: "[SOLVED] Double HDD Setup?"
date: 2007-11-24
forum: General Help
---

### Post by Unicycle on 2007-11-24
Hi there.  Quick question...

I've got a spare 80 gig IDE/PATA hard disk laying around, and I want to use it as a sort-of backup drive along with my Win/Gutsy dual booting 500 gig IDE/PATA drive.  The 80 gig drive has got Win XP on it right now, and is pretty much filled with old data.

So, I want to know if it would work to do the following:

[LIST]
[*]Install 80 gig drive as "cable select."
[*]Boot to GParted LiveCD.
[*]Erase 80 gig drive.
[*]Format it to ______. (what filesystem should I format it as?)
[*]Boot as usual, and have the new drive recognized in Ubuntu, and be able to save to it.
[/LIST]
Would this situation cause any problems or conflicts, or would it work smooth as butter? [-o< :lol:

Finally, what would I do if I wanted to transfer some of my old pictures and stuff from the old drive to Ubuntu before wiping it?

---

### Post by brennydoogles on 2007-11-24
> **Unicycle said:**
> Hi there.  Quick question...

I've got a spare 80 gig IDE/PATA hard disk laying around, and I want to use it as a sort-of backup drive along with my Win/Gutsy dual booting 500 gig IDE/PATA drive.  The 80 gig drive has got Win XP on it right now, and is pretty much filled with old data.

So, I want to know if it would work to do the following:

[LIST]
[*]Install 80 gig drive as "cable select."
[*]Boot to GParted LiveCD.
[*]Erase 80 gig drive.
[*]Format it to ______. (what filesystem should I format it as?)
[*]Boot as usual, and have the new drive recognized in Ubuntu, and be able to save to it.
[/LIST]
Would this situation cause any problems or conflicts, or would it work smooth as butter? [-o< :lol:

Finally, what would I do if I wanted to transfer some of my old pictures and stuff from the old drive to Ubuntu before wiping it?

I would recommend installing Gparted directly to your current installation!!```
sudo aptitude install gparted
``` then you cando any partition changes you want as soon as the HD is installed physically into the computer. As for the partition type, Ubuntu uses EXT3 by default, so that's what I recommend. If you would like to retrieve data from the drive before formatting it, here is my recommendation on how to do it. Open Gparted, and on the top left corner you will see a dropdown box which will allow you to choose which device you are working with. Click it, and take note of the name of the second disk (it will be something like /dev/hdb1 or /dev/sdb1 ) . Now open a terminal and type ```
mkdir ~/oldhd
sudo mount /dev/(whatever your device was) ~/oldhd
```
now your HD should be mounted (read-only mode) in your home/oldhd folder, so you can drag and drop graphically.
 rescue your data, and then format. I believe that Gparted will give you the option to set a mountpoint as well when you format, so you should be all set!!

---

### Post by Unicycle on 2007-11-25
> **brennydoogles said:**
> I would recommend installing Gparted directly to your current installation!!

The problem there is I get a padlock symbol next to the partitions, meaning I can't do anything to them, even when I'm using the program as root.

---

### Post by Unicycle on 2007-11-25
bump... (I wanna get going on this!) :popcorn:

---

### Post by brennydoogles on 2007-11-25
> **Unicycle said:**
> The problem there is I get a padlock symbol next to the partitions, meaning I can't do anything to them, even when I'm using the program as root.

ok, the padlock means that the partition is currently mounted. If you want to change the partition, simply right click it in Gparted and click unmount. The screen will refresh, an you should be ready to go!!

---

### Post by Unicycle on 2007-11-25
> **brennydoogles said:**
> ok, the padlock means that the partition is currently mounted. If you want to change the partition, simply right click it in Gparted and click unmount. The screen will refresh, an you should be ready to go!!

OK.  I transfered my data, and then formatted the whole drive to Ext3.  But, now it isn't recognized by Ubuntu (i.e., no icon in the "Computer" section).  How do I get to it?  It is recognized by GParted.

---

### Post by Unicycle on 2007-11-25
Alright, somehow it became recognized.  Now, how do I access the newly installed disk with root privileges from Ubuntu?

---

### Post by brennydoogles on 2007-11-25
> **Unicycle said:**
> Alright, somehow it became recognized.  Now, how do I access the newly installed disk with root privileges from Ubuntu?

well there are a few ways. Open a terminal and either:

```
cd /path/to/hd/
```
or
```
gksudo nautilus /path/to/hd
```

If you do the second option, you will have a graphical user interface to work with, and you can right click the drive, and give yourself read/write permissions for the drive. Hope that helped!

---

### Post by brennydoogles on 2007-11-26
Did everything work out right?

---

### Post by Unicycle on 2007-11-26
> **brennydoogles said:**
> Did everything work out right?

Definitely!  Sorry I didn't reply earlier.

But yeah, I've backed up all my stuff onto it, and everything's perfect.  Thanks so much! :guitar:

---

### Post by atlfalcons866 on 2007-11-26
can you mix sata and pata?

---

### Post by brennydoogles on 2007-11-26
> **Unicycle said:**
> Definitely!  Sorry I didn't reply earlier.

But yeah, I've backed up all my stuff onto it, and everything's perfect.  Thanks so much! :guitar:

If you don't mind marking the thread as solved that would be great!!

---

