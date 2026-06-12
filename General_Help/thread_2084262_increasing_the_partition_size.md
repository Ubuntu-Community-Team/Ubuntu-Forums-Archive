---
title: "increasing the partition size??"
date: 2012-11-14
forum: General Help
---

### Post by quentinl on 2012-11-14
i have installed ubuntu on a friends computer but the partition size is not big enough. how do i increase the size.

---

### Post by quentinl on 2012-11-14
is it actually possible to? i haven't done it before and any response would be appreciated

---

### Post by Mr_JMM on 2012-11-14
How many partitions are on the drive at the moment?

The process (making some assumptions) is as follows:

1. Shrink a partition (obviously not the root partition).
2. Enlarge the root partition.

GParted will do these. It's best to use the Ubuntu installation CD to boot into Ubuntu and open gparted from there. However, if you have Windows 7 installed some advise doing this from that. I prefer GParted.

Do you have a separate home partition? if not, now is a good time to create it.

Root requires at least 4GB but I would set a minimum of 6-8GB more if it's all one partition.

can you add the results of ```
sudo fdisk -l
``` to your reply if you have any other questions please?

---

### Post by quentinl on 2012-11-14
it has three partitions on it
main file-system 299gb
ubuntu 16gb
hp tools 4.3gb
he wants to enlarge the partition but it is not from cd i installed it from his windows

---

### Post by quentinl on 2012-11-14
i did a man on fdisk and tryed some of the options but it dosn't work.
do i need to sudo it??

---

### Post by Mr_JMM on 2012-11-14
How did you add the 16GB for Ubuntu?

If you don't have an install DVD I recommend burning one; they're useful and can fix a multitude or errors.

If you used Windows did you use Wubi? if not, use the same program to shrink the main file system then enlarge the ubuntu one.

Again, this is probably easier with GParted but if the WIndows program worked before it should be ok.

Caution: BACK UP IMPORTANT DATA. This applies to Ubuntu and Windows. When you play around with partitions you have to assume it'll bork.

Re your last post (I missed it as I was typing this one): Yes, you need to use sudo. Good on you for using terminal.

---

### Post by quentinl on 2012-11-15
i think it is 18GB but it was just the download and then using wubi

---

### Post by quentinl on 2012-11-15
> **Mr_JMM said:**
> 

If you don't have an install DVD I recommend burning one; they're useful and can fix a multitude or errors.


i did it when i installed my Ubuntu but i didn't have any on me at the time i installed it on there computer

---

### Post by Mr_JMM on 2012-11-15
I've never used Wubi so I can't comment about the options there.

You probably won't be able to use fdisk whilst you're running Ubuntu.

As far as I can see your only two options are to see if Windows partitioner will work or grab an Ubuntu install DVD.

---

### Post by quentinl on 2012-11-15
i haven't used Wubi before either and it's already installed.
ill try and see if windows partitioner will work.
p.s is there any way i can do it whilst running in Ubuntu?

---

### Post by Mr_JMM on 2012-11-15
Afraid you can't change a partition that is being used so no, you can't do this from a booted Ubuntu session, only whilst running Ubunut from a DVD or USB.

Try the Windows partitioner tool first (defrag lots if not already to create more room).

---

### Post by oldfred on 2012-11-15
I do not know wubi either, but you cannot resize it with Windows partition tools.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Resize wubi - bcbc
[https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by Mr_JMM on 2012-11-15
Sorry, to clarify, I wasn't talking about resizing Wubi. My bad if that's how it came across. I was suggesting the OP resize the partitions using Windows (system tools), which is what I did with an old Vista laptop (though the windows tools is cr*p and I reverted to Gparted).

---

### Post by cthom on 2012-11-15
i've tried partitioning d:/ which holds my wubi install. gparted complains of cross-linked files and aborts the procedure. i think wubi must need to be on the same partition as windows?

---

### Post by quentinl on 2012-11-15
so there is no way that i can do it whilst running Ubuntu?
ill have a go of windows partitioner

---

### Post by Mr_JMM on 2012-11-15
To confirm, there's no way to do this while you have booted into an isntalled ubuntu session. You CAN and probably SHOULD do this from a Live DVD version of Ubuntu.

But hopefully, windows partioner(?) tool will work. Though again, I stress I've not tried when Wubi was used.

---

### Post by 23senick on 2012-11-15
My recommendation is to get a usb or CD/DVD set up with Puppy linux.  You get gparted with that, but you can boot up your system without using the Ubuntu partition.  Puppy Linux loads into your RAM and the hard disc is fully accessible.  

This can also help you get round some of the issues with partitions (for example, HP ship laptops with 4 partitions, the maximum, and you have to work around that)  

One other thought - I understand it's good practice to defrag windows partitions before re-sizing them.

---

### Post by Mr_JMM on 2012-11-15
> **23senick said:**
> My recommendation is to get a usb or CD/DVD set up with Puppy linux.  You get gparted with that, but you can boot up your system without using the Ubuntu partition.  Puppy Linux loads into your RAM and the hard disc is fully accessible.
Do you feel that a live version of Puppy Linux would be better than a live version of Ubuntu? Will it run faster? Does Puppy Linux have a newer version of Gparted?

> **23senick said:**
> One other thought - I understand it's good practice to defrag windows partitions before re-sizing them.
> **Mr_JMM said:**
> (defrag lots if not already to create more room).

---

### Post by oldfred on 2012-11-15
Ubuntu includes a recent gparted. Not sure what is with Puppy, but Puppy boots quickly as it is so small and runs just in memory.

You can also download these as repair CDs.

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Mr_JMM on 2012-11-15
> **oldfred said:**
> Ubuntu includes a recent gparted. Not sure what is with Puppy, but Puppy boots quickly as it is so small and runs just in memory.
Good to know, thanks.

OP: In case you still have problems, is there any way you can get get a copy of Ubuntu or burn a new Puppy Linux DVD / USB?

---

### Post by quentinl on 2012-11-21
don't worry i have fixed the problem thanks for all your help

---

### Post by Mr_JMM on 2012-11-21
For the benefit of others could you say how you solved this?

---

